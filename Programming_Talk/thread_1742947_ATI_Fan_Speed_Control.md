---
title: "ATI Fan Speed Control"
date: 2011-04-29
forum: Programming Talk
---

### Post by petsoukos on 2011-04-29
Hello,

I've posted this on another thread but this section of the forum is more appropriate:

I don't know if this is helpful or if an application already exists but I  wrote a python script to adjust my Fan Speed in real-time. You should  also know that I don't know Python, all I did was search some functions  and how the Syntax works with python and with the help of my PHP  background I managed to get it running. I don't know if this is the  correct way to control the fan speed, but it works for me. (it might not  work for your configuration)

```
import os
import math
import time

lastprobed = 0
while True:

    output = os.popen("aticonfig --od-gettemperature")

    for i in output.readlines():
        temp = i

    currentTemperature = math.floor(float(temp[42:47]))

    print(currentTemperature)
    
    if lastprobed != currentTemperature:
        if currentTemperature <= 55:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 25%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 25\"")
        elif currentTemperature <= 60:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 50%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 50\"")
        elif currentTemperature >= 65:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 100%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 100\"")        
    else:
        print("Temp did not change, no adjustments!")
    lastprobed = currentTemperature


    time.sleep(3)
```It's an endless while loop with a 3 second sleep. I used the os  functions to run command line commands to get the temperature first then  find in that output string the part where the temp number is and  convert it to a float then floor the value. Then there is a standard if  structure to adjust the fan speed in every loop.

I don't know if this could cause any damage to the card it self but for a temporary solution it works just fine.

Now are there any Real Python developers here? I could use some help to  find a better way to grab the temperature value without relying on a  command line command. Is there a Python module that I could import to  use with graphic cards? Maybe an ATI API for Python?

UPDATE:
Added more "functionality", like the variation and changing the speed in steps with the currentSpeed variable.
```
import os
import math
import time

lastprobed = 0
currentSpeed = 0
while True:

    output = os.popen("aticonfig --od-gettemperature")

    for i in output.readlines():
        temp = i

    currentTemperature = math.floor(float(temp[42:47]))

    print("Current temperature: " + str(currentTemperature))
    
    if lastprobed != currentTemperature:
        vari = abs(lastprobed - currentTemperature)        
        if vari >= 2:
            print("Temperature variation: " + str(vari))
            if currentTemperature <= 55:
                if currentSpeed != 25:
                    print("Temp is: " + str(currentTemperature) + " setting fanspeed to 25%")
                    os.system("aticonfig --pplib-cmd \"set fanspeed 0 25\"")
                    currentSpeed = 25
            elif currentTemperature <= 60:
                if currentSpeed != 50:
                    print("Temp is: " + str(currentTemperature) + " setting fanspeed to 50%")
                    os.system("aticonfig --pplib-cmd \"set fanspeed 0 50\"")
                    currentSpeed = 50
            elif currentTemperature >= 65:
                if currentSpeed != 100:
                    print("Temp is: " + str(currentTemperature) + " setting fanspeed to 100%")
                    os.system("aticonfig --pplib-cmd \"set fanspeed 0 100\"")
                    currentSpeed = 100
            lastprobed = currentTemperature
        else:
            print("Temperature Variation to low, skip adjustment. Variation: " + str(vari))
    else:
        print("Temp did not change, no adjustments!")
    #lastprobed = currentTemperature

    print("Current fan speed is set to: " + str(currentSpeed))
    print("============== BREAK LINE =================")

    time.sleep(3)
```

---

### Post by shelbydz on 2011-09-22
awesome. 

thanks

---

### Post by Tosho on 2012-05-22
I can run the script from terminal with : python script.py . But how can I run it from start-up in the background ?

---

