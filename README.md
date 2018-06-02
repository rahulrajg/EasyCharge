# EasyCharge


Salient Features: 

 Starts Charging when Laptop battery percentage falls below a min threshold. 
 
 Stops charging when Laptop battery percentage is above a max threshold. 
 
 This device is Laptop Independent, i.e., User can connect this device with any Laptop with some initial settings.



Requirements: 

 Arduino Mega 2560 

 Arduino IDE 

 OS: Ubuntu with any editor 

 Bluetooth 4.0 

 Relay Module 

 Laptop with charger 

 Breadboard 

 Jumper Wires 


Description: 

A shell script (battery_status.sh) extracts the battery percentage of laptop and info about whether the laptop is plugged in or not. 

If laptop is plugged in and battery percentage exceeds a max threshold, the script writes a unique message to a file. 

A python script (batt_python.py) reads the unique message from file and then sends the message to Arduino Serial Monitor.

Arduino instructs relay module to break the circuit and turns off charging. 
 
Similarly, if laptop is not charging and battery falls below a min threshold, the script sends another unique message to Arduino Serial Monitor using python script. 

Arduino then allows relay module to turn on charging. 

All this while we can leave the power cord connected to the laptop without worrying about the battery at all.


How to Use:

 On Ubuntu Terminal, 

$ cd /*path where shell script is*/ 

$ chmod +x shell.sh 

$ ./shell.sh 

$ chmod +x pythonscript.py 

$ ./pythonscript.py 

$ env EDITOR=nano crontab –e /*add these two scripts path at the end and save it*/ 
 
 Plug the charger of laptop to the point provided on device. 
 
 Connect the device to laptop for power supply. 
 
 Device will automatically allow charging or discharging as per messaged received by shell scripts.


Implementation:

Step 1: Interface Relay Module with an Arduino

            Relay                        Arduino 
			
            RL1          -->>            pin 8 
			
            +            -->>            5V 
			
            -            -->>            GND 
 
Step 2: Interface Relay Module with Laptop Charger 

        NO pin of Relay Module     -->>   5v of Arduino 
		
        COM Pin of Relay Module    -->>   +ve pin of Charger 
		
        -ve pin of charger         -->>   Neutral of Main Power 
       
Step 3: Upload Arduino code to Arduino Mega 2560 using Arduino IDE 
