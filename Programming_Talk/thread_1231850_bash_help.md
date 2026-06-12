---
title: "bash help"
date: 2009-08-05
forum: Programming Talk
---

### Post by monkeyslayer56 on 2009-08-05
ok im trying to get bash to read from my USB serial port with 

```
#!/bin/bash
sudo cat /dev/ttyUSB0 | while read var1; do
echo $var1 
if [ "$var1" == "1" ]; then #check if value is 1 from the serial port
echo good
br g1 on #execute command on local PC 
fi
done

```
and it works and also prints the value witch is what i want BUT after so long of running cat errors and then i get the error 
```
cat: /dev/ttyUSB0: Input/output error

```
and i have to reboot to get anything on the serial to work again.
is there a way to read the port directly or a way to keep it from doing this. btw it also does this when i just run cat sometimes. if anyone can help please and thank you

---

### Post by jpkotta on 2009-08-05
You don't need root privileges to read/write serial ports.  You just need to be in the dialout group.
```
sudo adduser $USER dialout
```
Log out and log back in for the changes to apply.


You could just redirect stdin.
```
while read foo < /dev/ttyS0 ; do ... ; done
```

---

### Post by ahmatti on 2009-08-05
I have done something similar with cat and I had a similar problem with a cheap USB adapter if the input to serial port was fast, more than 30Hz or so I think... I was able to fix the problem by getting an adapter with built in fifo. Never had this problem with a "real" serial port, so I think it might be the adapter to blame. 

 Have you tried removing the adapter and plugging it back in instead of rebooting? It worked for me. I know it doesn't fix the actual problem, but might make debugging a bit easier.

You can also interface the serial port with e.g. Perl, Python or C, all of which will give you more control on what you are doing. Generally if there are IO errors with serial port adding small delays tends to help.

---

### Post by monkeyslayer56 on 2009-08-05
> **ahmatti said:**
> 
 Have you tried removing the adapter and plugging it back in instead of rebooting? It worked for me. I know it doesn't fix the actual problem, but might make debugging a bit easier.

You can also interface the serial port with e.g. Perl, Python or C, all of which will give you more control on what you are doing. Generally if there are IO errors with serial port adding small delays tends to help.
i've tryed the inplugging it and plugging it back in even waiting up to 30 min before plugginh it back in (i hate rebooting) and still no luck. i'll try adding delays and then maybe try it in python. also its not exactly a serial to usb adpter(well in a way yes) because its coming from my microcontroler directly with a USB cable so i can't just get a better adapter :(
and jpkotta i didn't fully understand you code and it errors when i replace the /dev/ttyS0 with /dev/ttyUSB0.

EDIT: i've tred pyserial and it works to an extent BUT it will only return teh vaule the serialport sent when i had the serial port terminal open to view. it won't update untill i open serial port terminal program and then close it again then pyserial will get that value.
heres my most recent try at it(ive tryed different arangment of varables too)
```
import serial
from time import sleep
import os  
q=1
ser = serial.Serial('/dev/ttyUSB1',9600)
while q==1:
    x=ser.read()
    print x

    if x=="1":
        os.system("br g1 on")
        print ("ok")
    sleep(1)   

```
also when i go through just in idle and define and import the stuff and i do print ser.read() it does the same thing, only returns what another program last saw

---

### Post by ahmatti on 2009-08-06
> **monkeyslayer56 said:**
> 
EDIT: i've tred pyserial and it works to an extent BUT it will only return teh vaule the serialport sent when i had the serial port terminal open to view. it won't update untill i open serial port terminal program and then close it again then pyserial will get that value.
heres my most recent try at it(ive tryed different arangment of varables too)


I didn't quite understand your explanation... Anyway, I haven't used pyserial, but from what I see in the docs your code seems to be OK. Are your sure that you have correct settings for the serial port i.e handshakes etc.. Like here [http://pyserial.sourceforge.net/shortintro.html](http://pyserial.sourceforge.net/shortintro.html), also I notice you don't have any timeout for the port, which is sometimes needed at least in other languages.

---

### Post by monkeyslayer56 on 2009-08-06
> **ahmatti said:**
> I didn't quite understand your explanation... Anyway, I haven't used pyserial, but from what I see in the docs your code seems to be OK. Are your sure that you have correct settings for the serial port i.e handshakes etc.. Like here [http://pyserial.sourceforge.net/shortintro.html](http://pyserial.sourceforge.net/shortintro.html), also I notice you don't have any timeout for the port, which is sometimes needed at least in other languages.
i figured out why pyserial was reading the wrong value (THANK YOU GOOGLE lol) i had to put ```
ser.flushInput()

```
after my IF statement and it would then read the new value. and it worked perfectly.
however now i have a new problem after running it for about 7 hours it used over 4 GB or memory. is there anyway to have it delet all stored values or something and start fresh every so long so it doesn't use as much over time. or is this a flaw in python 2.6 (i'll convert it to python 3 later today and run it and see if it gathers more memory over time)
thanks everyone for your help
edit: memory problem seams to now be solved by running python in terminal instead of idle

---

### Post by ahmatti on 2009-08-07
> **monkeyslayer56 said:**
> 
edit: memory problem seams to now be solved by running python in terminal instead of idle

Glad that you got if fixed and that the problem is not with pyserial. I also intend to use it for a project and was getting a bit worried...

---

