---
title: "Ubuntu 14.04 LTS slows down and freezes or logs out on Python codes"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by grandukekj on 2015-09-16
Hi, I have recently switched over to Linux system with Ubuntu 14.04 LTS 64bit.
It was all awesome and cool, except when I was confronted with system errors.

1) when I run a Python 3 script, which works perfectly fine on other machines (Windows/Mac/Linux),
   it stops in the middle of the code, the whole machine freezes for a brief moment, and logs out to the Ubuntu log-in screen.
   When I log back in, Ubuntu asks me whether to report the system error. The error says something like this:
   [B]Sorry, Ubuntu 14.04 has experienced an internal error 
   /usr/bin/Xorg[/B]
   I tried reinstalling lightdm. It does not solve the problem.
   Every time I run the script, exactly same thing happens.

2) When I run a Python script that essentially has nothing close to astronomic computation but a small for loop (6x7),
    it seems to work fine until the first 4 loop cycle. Then, the machine suddenly makes noise (similar noise to when
    you play game and it is loading...), mouse cursor disappears briefly, and the whole system slows down significantly.
    After pushing ctrl+C for several times and closing the terminal running the script, the system is still very slow. Also,
    strangely, when I run Geany editor at this point, the GUI is different than before - it looks like a Windos 95 design,
    as opposed to the Windows 7 design it originally has before the error. When I reboot, everything comes back to normal.
    
    I tested the exact same script on other machines, and it works totally fine.

3) This is a very minor problem regarding Wine. I have installed a software through Wine with its Windows version installer.
     It is an instant messenger called Kakao Talk. The program starts up fine, but after a few minutes, the software GUI turns completely gray
     and I have to fore-quit. 

     I did tweak the settings so that the Wine runs on 32bit mode, following the instructions on Stackoverflow...

I am new to Unix system and have no idea where to start searching on Google.
Please help me!!!!!!!!!!!!!!!!

---

### Post by mystics on 2015-09-16
I'm a little confused given the third statement. Are you trying to run Python in Wine? Or is that completely unrelated to the first two problems?

---

### Post by grandukekj on 2015-09-18
> **mystics said:**
> I'm a little confused given the third statement. Are you trying to run Python in Wine? Or is that completely unrelated to the first two problems?


All three issues are independent of each other :)
or so I think at least.

---

### Post by sotiris2 on 2015-09-18
Can you post dmesg output as soon as possible after any of the problems occur? That is if you recover without rebooting as I understand you do.  Do the scripts write or read to/from the disk?

---

