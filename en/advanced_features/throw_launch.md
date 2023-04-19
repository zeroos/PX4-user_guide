# Throw Launch

In addition to standard takeoff, PX4-based multicopters can be started by
throwing them into the air. Once the aircraft detects the throw, it turns on
the motors and behaves according to the mode it is in. The majority of testing
is done with position mode, but other modes should also work.

:::note
This feature was intended to be used with multicopters. For similar
functionality on fixed-winged aircrafts, check
[Hand Launch in Takeoff Mode](../flight_modes/takeoff.md#catapult-hand-launch).
:::

## Safety

:::warning
Caution! This procedure requires the operator to hold an armed multicopter and
be in proximity when it is flying. It is dangerous. Take special care and do not
neglect any safety measures.
:::

1. Wear safety equipment. Eye protection and safety work gloves are recommended.
1. Have an easily accessible [killswitch](../config/flight_mode.md) and remind
   the operator to be attentive and use it if needed. We found the latter part
   to be particularly important as pilots tend to try to save the aircraft even
   in hard situations. 
1. Test as much as possible without propellers. Make sure the tools to dismount
   the propellers are easily accessible not to neglect this step.
1. Test this feature with at least two people --- one handling the aircraft, the
   other one the remote control.
1. Keep in mind that after the throw, the exact behavior of the aircraft might
   be hard to predict as it depends heavily on the way it is thrown. Sometimes
   it will stay perfectly in place, but sometimes (e.g., due to extensive roll),
   it might drift to one side while stabilizing. Keep safe distance.

For safety, we recommend the following procedure to first execute the throw
launch without the propellers to confirm the arming does not happen prematurely
and for the operator to understand what to expect during the flight.

### Throw launch test without propellers

1. Dismount the propellers.
1. Set [COM_THROW_EN](../advanced_config/parameter_reference.md#COM_THROW_EN) to Enabled.
1. Arm the aircraft. The engines should not spin, but the vehicle should be
   armed and keep playing the arming tune.
1. Throw the aircraft into the air around 2 m up. It is possible to start lower
   and gradually increase the altitude until the engines turn on.
1. The engines should start just after crossing the apex.
1. Engage the kill switch (ideally a second person operating the RC should do it).
1. Catch the drone. Use safety gloves.

## Operation

Before testing the throw launch, make sure the aircraft works well using the
usual takeoff. 

### Throw launch

1. Set [COM_THROW_EN](../advanced_config/parameter_reference.md#COM_THROW_EN) to Enabled.
1. Arm the aircraft. The propellers should not spin, but the vehicle should be
   armed and keep playing the arming tune.
1. Throw the aircraft away from you, forward and up. The vehicle should reach
   the speed of
   [COM_THROW_SPEED](../advanced_config/parameter_reference.md#COM_THROW_SPEED),
   which by default is set to 5 m/s. To achieve that, throwing it to around 2 m
   altitude and 2 m away should suffice.
1. After the downward velocity is detected (the vehicle starts falling down),
   the motors should turn on and the vehicle will start flying according to the
   mode it is in.
1. Fly!

The throw launch was primarily tested in the POSITION mode, but should also work
in other modes.

## Parameters

The following parameters determine the behavior of the system. 

- [COM_THROW_EN](../advanced_config/parameter_reference.md#COM_THROW_EN) enables the feature.
- [COM_THROW_SPEED](../advanced_config/parameter_reference.md#COM_THROW_SPEED) determines 
  the minimum speed the aircraft should reach to detect the throw. If it is not
  reached, the engines will not turn on.
