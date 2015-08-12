# grbl-servo
grbl 0.9i with Servo motor support

GRBL 0.9i with servo motor support.
Use the PIN D11 to driver the servo. 
Use the commands M03 Sxxx (xxx between 0 and 255) to rotate the servo between 0-180.
The command M05 turn the servo to zero degrees.

you can change the pulse duration in the file spindle_control.c:
#define RC_SERVO_SHORT     15       // Timer ticks for 0.6ms pulse duration  (9 for 0.6ms)
#define RC_SERVO_LONG      32       // Timer ticks for 2.5 ms pulse duration  (39 for 2.5ms)     
//#define RC_SERVO_INVERT     1     // Uncomment to invert servo direction

If you want to have the servo working from 0 --> 180 degrees change RC_SERVO_SHORT and put 9, RC_SERVO_LONG and put 39
If ypu want invert the servo mouvement uncomment the line above.

-------------------------------------------------------------------

Grbl is a no-compromise, high performance, low cost alternative to parallel-port-based motion control for CNC milling. It will run on a vanilla Arduino (Duemillanove/Uno) as long as it sports an Atmega 328.

The controller is written in highly optimized C utilizing every clever feature of the AVR-chips to achieve precise timing and asynchronous operation. It is able to maintain up to 30kHz of stable, jitter free control pulses.

It accepts standards-compliant g-code and has been tested with the output of several CAM tools with no problems. Arcs, circles and helical motion are fully supported, as well as, all other primary g-code commands. Macro functions, variables, and most canned cycles are not supported, but we think GUIs can do a much better job at translating them into straight g-code anyhow.

Grbl includes full acceleration management with look ahead. That means the controller will look up to 18 motions into the future and plan its velocities ahead to deliver smooth acceleration and jerk-free cornering.

Licensing: Grbl is free software, released under the GPLv3 license.

For more information and help, check out our Wiki pages! If you find that the information is out-dated, please to help us keep it updated by editing it or notifying our community! Thanks!

Lead Developer [2011 - Current]: Sungeun(Sonny) K. Jeon, Ph.D. (USA) aka @chamnit

Lead Developer [2009 - 2011]: Simen Svale Skogsrud (Norway). aka The Originator/Creator/Pioneer/Father of Grbl.

Official Supporters of the Grbl CNC Project

Carbide3D  Inventables

Master Branch:

Grbl v0.9j Atmega328p 16mhz 115200baud with generic defaults (2015-07-17)
Grbl v0.9j Atmega328p 16mhz 115200baud with ShapeOko2 defaults (2015-07-17)
IMPORTANT INFO WHEN UPGRADING TO GRBL v0.9 :
Baudrate is now 115200 (Up from 9600).
Homing cycle updated. Located based on switch trigger, rather than release point.
Variable spindle is now enabled by default. Z-limit(D12) and spindle enable(D11) have switched to access the hardware PWM on D11. Homing will not work if you do not re-wire your Z-limit switch to D12.
Archives:

Grbl v0.9i Atmega328p 16mhz 115200baud with generic defaults
Grbl v0.9i Atmega328p 16mhz 115200baud with ShapeOko2 defaults
Grbl v0.9g Atmega328p 16mhz 115200baud with generic defaults
Grbl v0.9g Atmega328p 16mhz 115200baud with ShapeOko2 defaults
Grbl v0.8c Atmega328p 16mhz 9600baud
Grbl v0.7d Atmega328p 16mhz 9600baud
Grbl v0.6b Atmega328p 16mhz 9600baud
Grbl v0.51 Atmega328p 16mhz 9600baud
Grbl v0.6b Atmega168 16mhz 9600baud
Grbl v0.51 Atmega168 16mhz 9600baud
Update Summary for v0.9j

Restore EEPROM feature: A new set of restore EEPROM features to help OEMs and users reset their Grbl installation to the build defaults. See Configuring Grbl Wiki for details.
Update Summary for v0.9i

IMPORTANT:
Homing cycle updated. Locates based on trigger point, rather than release point.
System tweaks: $14 cycle auto-start has been removed. No more QUEUE state.
New G-Codes
CoreXY Support
Safety Door Support
Full Limit and Control Pin Configurability
Additional Compile-Time Feature Options
Update Summary for v0.9h from v0.8

IMPORTANT:
Default serial baudrate is now 115200! (Up from 9600)
Z-limit(D12) and spindle enable(D11) pins have switched to support variable spindle!
Super Smooth Stepper Algorithm
Stability and Robustness Updates
(x4)+ Faster Planner
Compile-able via Arduino IDE!
G-Code Parser Overhaul
Independent Acceleration and Velocity Settings
Soft Limits
Probing
Dynamic Tool Length Offsets
Improved Arc Performance
CPU Pin Mapping
New Grbl SIMULATOR! (by @jgeisler and @ashelly)
Configurable Real-time Status Reporting
Updated Homing Routine
Optional Limit Pin Sharing
Optional Variable Spindle Speed Output
Additional Compile-Time Feature Options
List of Supported G-Codes in Grbl v0.9 Master:
  - Non-Modal Commands: G4, G10L2, G10L20, G28, G30, G28.1, G30.1, G53, G92, G92.1
  - Motion Modes: G0, G1, G2, G3, G38.2, G38.3, G38.4, G38.5, G80
  - Feed Rate Modes: G93, G94
  - Unit Modes: G20, G21
  - Distance Modes: G90, G91
  - Arc IJK Distance Modes: G91.1
  - Plane Select Modes: G17, G18, G19
  - Tool Length Offset Modes: G43.1, G49
  - Cutter Compensation Modes: G40
  - Coordinate System Modes: G54, G55, G56, G57, G58, G59
  - Control Modes: G61
  - Program Flow: M0, M1, M2, M30*
  - Coolant Control: M7*, M8, M9
  - Spindle Control: M3, M4, M5
  - Valid Non-Command Words: F, I, J, K, L, N, P, R, S, T, X, Y, Z
