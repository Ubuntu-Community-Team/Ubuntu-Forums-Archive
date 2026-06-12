---
title: "Samsung SPC A30M Webcam Won't work"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by zutronius on 2008-06-23
I bought a Samsung SPC A30M webcam and I have plugged it into my laptop. Camorama detects it, but shows only a black screen. I have ran lsusb command and have gotten this:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 001 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000 

I've been using Ubuntu for over a year, but still consider myself a novice. Can anyone help me get this webcam working?

I have tried the webcam with Skype and it shows that it is indeed being detected (as a Z-Star Vlmicro zco302 /dev/video0).

---

### Post by AndThenWhat on 2008-06-23
Here is a thread that I started and solved myself about Webcams that don't work out of the box: [http://ubuntuforums.org/showthread.php?t=831604](http://ubuntuforums.org/showthread.php?t=831604)

Basically, for some webcams compiling the gspca driver from source works because it creates a compatible kernel module for your system.

---

### Post by zutronius on 2008-06-23
Thanks. This might be a dumb question, but I'm not 100% sure how to compile. I saved the file in your thread to my desktop. What do I do next?

---

### Post by AndThenWhat on 2008-06-23
> **zutronius said:**
> Thanks. This might be a dumb question, but I'm not 100% sure how to compile. I saved the file in your thread to my desktop. What do I do next?

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

That basically sums it all up.  It's not that hard just a few lines of code

---

### Post by zutronius on 2008-06-23
...

---

### Post by zutronius on 2008-06-23
I got part way into the issue then ran into a problem.

This part: rying a v4l app
================
goes to gspcagui directory
be sure to have libsdl installed with the header
then
make
as root
make install
Plug your webcam and run
gspcagui -d /dev/video0
adjust video0 to your hardware
Press the G button and wait for the webcam probe
you can now play, the two windows are active 
mouse can be used to select a Region of Interess within the grabbing windows
then press the center of the pad to zoom:)
Picture and avi are implemented just press the button to start/stop




I cannot find a gspcagui directory and I'm also sure not sure about the be sure to have libsdl installed with the header part as well. Other than that, everything went alright and I still have a black screen when I try to use the webcam. :confused:

root@#$%@#%-laptop:/home/@$#$#/Desktop/gspcav1-20071224# gspcagui -d /dev/video0
bash: gspcagui: command not found

---

