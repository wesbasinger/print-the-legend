http://www.zyltech.com/arduino-cnc-shield-instructions/

Pre-flight Checklist
1. Do a visual check of all soldered points on the new board
	TODO
2. Plug the shield into an Arduino board and load the GRBL Firmware following the steps bellow:
	TODO
Download the GRBL source code. Download here
	DONE
Unzip the download and you’ll have a folder called "grbl-master"
	DONE
Launch the Arduino IDE. (Please make sure you are using the most recent version of the Arduino IDE.)	
	DONE
Load GRBL into the Arduino IDE as a Library. (Click the "Sketch" drop-down menu, then navigate to "Include Library", and select "Add .ZIP Library")
IMPORTANT: Select the "Grbl" folder inside the "grbl-master" folder, which only contains the source files and an example directory. (If you accidently select the .zip file or the wrong folder, you will need to navigate to your Arduino library, delete the mistake, and re-do this step.)
	DONE
Open the "GrblUpload" Arduino example. (Click the "file" down-down menu, navigate to "Examples->Grbl", and select "GrblUpload")
	DONE
Compile and upload GRBL to your Arduino. (1. Connect your Arduino Uno to your computer. 2. Make sure your board is set to the Arduino Uno in the "Tool->Board" menu and the serial port is selected correctly in "Tool->Serial Port".​ 3. Click the "Upload" and GRBL should compile and flash to your Arduino! Note: flashing with a programmer also works by using the "Upload Using Programmer" menu command.)
	DONE
3. Open up a serial connection to the Arduino board and check if GRBL is running. (We use Universal G-code sender to connect to GRBL)
	DONE
4. A4988 stepper drivers need adjustment for reference voltage. We will cover that in detail later.
	TODO

5. Testing each stepper controller socket individually is critical.

*Make sure the external high voltage power is not powered-up or connected
Connect a stepper motor to the stepper controller socket you want to test. This is very important because the Pololu Stepper drivers are designed to ramp up the current until it reaches the needed current to run. Without a stepper motor connected there will be nothing to consume the current and you can end up damaging the stepper driver if it over-heats in the process.*
Next, install the stepper motor driver ensuring that the enable pin on the driver aligns with the enable pin on the shield.
Connect the external power to the shield, making sure you connect the power up the right way. If not connected correctly you can cause damage to the shield, stepper motor drivers and Arduino board.
Send a g-Code to the Axis you are testing. The stepper motor should move if everything is working. (GCode Example : “G1 X5? or “G1 X0? or “G1 Y5?)
Repeat the above process with each axis using the same stepper driver.(Testing with one driver reduces the risk of damaging multiple stepper drivers at the same time.)
6. After all the above have been checked connect all the drivers and power up the system.

Current Limit (Reference Voltage) Adjustment for Stepper Driver
A4988 sold by Zyltech, Rs=0.1 ohm. Thus the max current is Vref/0.4

Vref (Reference Voltage) is measured using a multimeter at the points shown

[example](https://cdn11.bigcommerce.com/s-eblil3q2nd/product_images/uploaded_images/three.jpg)

Drv 8825 sold by Zyltech. Max current = Vref x 2

Reference voltage is adjusted with a small screwdriver at the point indicated with the white arrow in the picture to the right. We suggest adjusting the reference voltage in small increments - no more than a quarter turn at a time. For a starting point, you may set the max current to 1A. If the motor over heats, reduce the Vref. If the motor does not move or miss steps, increase the Vref.

Jumper Settings
Jumpers are used to configure the 4th Axis, Micro stepping and endstop configuration.


