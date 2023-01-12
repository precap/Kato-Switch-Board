The board is designed to throw single solenoid switches (e.g. Kato N-scale switches), and serve as multipurpose Expansion to a DCC-EX setup.


# Software
to be written. Help welcome.

# Hardware
Created in KiCad 6.10. Supposedly all the symbol libraries are included in KiCad 6 Projects. I have never tested that though, so let me know if there are any problems with loading.

## Arduino Nano Every
The Board is designed to run with an Arduino Nano Every exclusively (Note: Arduino Nano Every is distinct from Arduino Nano).
This is a conscious Design Decision, as the Nano Every has all the power supply components on board to generate sufficient 3.3V and 5V amperage to power the entire board from the higher Voltage input over the Barrel Jack.
Warning: Do not attempt to run Arduino Nano or other pin compatible boards that cannot handle high voltage on the VIN pin.

## Power Supply
should be provided to the 2.1mm Barrel Jack, or to the pins beside it marked 12V. Voltage fed here will go directly to the switches, LEDs, and to the VIN pin in the Arduino Nano Footprint.
The Arduino Nano Every can provide 1A of 5V, and up to 0.5A of that can further be converted to 3.3V. Most of this capability will be unused and is made available on the marked 2x2 pin headers for external use.

## Board Features
### Switches
Support for 12 Switches. Switching is performed by PT5126A-H chips. Supposedly they can manage up to 2.8A (Kato Switch will draw 0.5A@12V, Double crossover 2A).
Connectors are standard 1x2 pins with 2.54mm spacing for now.

### LED
Up to 128 Output pins. Using SM16206S, which seem to be a knockoff of the (magnitudes more expensive) TLC59282DBQR.
The outermst pins on the connectors are power supply, the others connected to the outputs.

### I2C
A PCA9617ADPJ i2c repeater is fitted on the board, allowing the i2c bus to reach a greater area. The chip can also translate between different voltage levels on the i2c bus, jumpers to set the voltage are provided.

### DCC
DCC Input over an optocopler is possible.

### RFID
Up to four RC522 RFID Reader breakout boards can be connected. The pin arrangement matches commonly found breakout boards, allowing connection with a 8 pin cable.
Whether this feature is can be added to the software in a way that supports all 4 readers remains to be seen, as the RC522 must be polled continuously to detect passing RFID Tags.


## Evaluation Testing

All Evaluation Testing was only performed in a feature incomplete Prototype Version.

| Component     | Status |
|---------------|--------|
| Switch Drivers| OK     |
| LED Drivers   | tbd    |
| I2C Repeater  | OK     |
| DCC Circuitry | no hw  |
| RFID Reader   | OK     |


# Production
All SMD Components are available @ jlcpcb at time of release.
Production files can be found in `jlcbcb-production/`. Only the SMD-only assembly files are complete at time of release.
10 boards, assembled with SMD Coponents only, are around 125$ before shipping and taxes. Placing all the Pins will push this to 200$.
