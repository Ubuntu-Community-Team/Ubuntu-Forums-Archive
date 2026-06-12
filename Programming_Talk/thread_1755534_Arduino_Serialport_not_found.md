---
title: "Arduino Serialport not found"
date: 2011-05-11
forum: Programming Talk
---

### Post by Theadamlt on 2011-05-11
Hi all,

I recently changed from Windows 7 to Ubuntu, and i have a problem using my Arduino duemilanove. I plug it in a usb port, starting the Arduino IDE, witch i downloadet from ubuntu softwarecenter. I Then go to "Tools > Board" and select the right boarb. But here is the problem: The "Serialport" menu is greyed out. I can't upload my code to the arduino. Im runnig Ubuntu 11.04 with kernel ver. 2.6-38-8. I treid running ```
ls /dev/ttyUSB0
``` in the terminal with the result of: ```
ls: cannot access /dev/ttyUSB0: No such file or directory

```

Does anyone have a suggestion?

Thank you in advice
Adam

---

### Post by teachop on 2011-05-11
After plugging in the Arduino, do a dmesg and see what is happening - if it mounts you will see the device path in there.  Also, try the command "lsusb" and see if it shows up.  I have used the Arduino bootloader with no issues in 11.04, so it is possible!

---

### Post by Theadamlt on 2011-05-12
Hi, thanks for the suggestion. Lol i found the solution: I tried with another USB cable. Thats it :)

---

### Post by marcusm11 on 2011-05-15
I'm new to arduino so i could be doing something wrong, but i'm getting a very similar problem.
When i first connect the board i can upload a new sketch, but after making changes i can not up load anything again. This is when the error message about serial ports not being found happens.
I tried everything listed above and can't figure it out. Anyother ideas?

---

### Post by teachop on 2011-05-15
> **marcusm11 said:**
> When i first connect the board i can upload a new sketch, but after making changes i can not up load anything again. This is when the error message about serial ports not being found happens.
What do you have to do to get it working again?

Also, what is the model of the Arduino?

---

### Post by marcusm11 on 2011-05-17
Its an Arduino Uno.
I'm not sure what actually resets it but its always the first sketch i try. so probably just restarting the computer

---

### Post by Tux Aubrey on 2011-05-17
This is a known issue with the original Uno and the Mega firmware.  It happened to me with my original Uno (but not with one I bought a few months later).  You clearly have the original firmware.

See this Arduino article first: [http://arduino.cc/en/Hacking/DFUProgramming8U2](http://arduino.cc/en/Hacking/DFUProgramming8U2)

But use the "non-soldering" technique to boot into DFU mode - shown best here: [http://arduino.cc/forum/index.php/topic,52447.0.html](http://arduino.cc/forum/index.php/topic,52447.0.html)

It sound complicated, but it takes less than a few minutes to run through the steps to upgrade the firmware once you have the DFU programmer and new firmware downloaded.

---

### Post by marcusm11 on 2011-05-18
would this be a linux issue? I followed the article you pointed to but the images didn't display the layout for an SMD edition. tried it on a windows machine and after sorting out driver issues it seems to be fine witout messing with th DFU

---

### Post by Tux Aubrey on 2011-05-18
> **marcusm11 said:**
> would this be a linux issue? 

Absolutely (my bad for assuming we were all doing Arduino on Ubuntu!). But SMD should not be an issue for putting an Uno into DFU mode.

By the way, the non-invasive workaround is to unplug and reset each time you get the serial error.  I just got tired of doing it that way and went with the permanent fix.

---

### Post by marcusm11 on 2011-05-19
I also found that there are some rxtx driver files that can be updated but again I'm too much of a noob to tackle something like that without a step-by-step. But I have found a super easy, noob friendly fix that even I could handle. If you run the Arduino IDE as  a super user Its all good.
I played around with it all night last night and didn't have to reset a thing.

Now I just need to find a cool project to put my mind to



Thanks for all the help

---

### Post by naga2raja on 2012-08-20
Just start arduino IDE as a root user

```
 sudo arduino 
```

---

