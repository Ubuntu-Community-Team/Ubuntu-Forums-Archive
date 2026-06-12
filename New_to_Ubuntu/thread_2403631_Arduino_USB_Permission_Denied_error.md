---
title: "Arduino USB Permission Denied error"
date: 2018-10-14
forum: New to Ubuntu
---

### Post by billd01 on 2018-10-14
Hi,

I have installed Arduino IDE 1.8.5 on Ubuntu 18.04.1 LTS. 

Every time I try to upload an Arduino sketch I get the error: avrdude: ser_open(): can't open device "/dev/ttyUSB0": Permission denied

I have followed the instructions here:
[https://www.arduino.cc/en/Guide/Linux#toc6](https://www.arduino.cc/en/Guide/Linux#toc6)

[COLOR=#4F4E4E][FONT=&quot]sudo usermod -a -G dialout <username> [/FONT][/COLOR]seems to work OK in the terminal, the command runs, and asks for my PW, but it does not provide USB access?
Even after I log out and back in again I still do not have USB access?

Any suggestions?

I am VERY, VERY new to Linux, ZERO experience.

thnx
billd

---

### Post by TheFu on 2018-10-14
which username did you use?
I don't have that group in my list.
The permissions on my USB-to-Serial connection is this:```

$ ll /dev/ttyUSB0 
crw-rw---- 1 root dialout 188, 0 Oct 14 08:22 /dev/ttyUSB0
```
so adding my userid to the *dialout* group, would let me read and write using the ttyUSB0 device.  Basic Unix permissions.

```
$ sudo usermod -a -G dialout thefu
``` is the correct command for me.
Oddly, when I type **id** to check my membership, it doesn't show up there after doing a **newgrp**, but the group file does show this:
```
$ egrep dialout /etc/group
dialout:x:20:thefu
```
So I'm in the group. newgrp forces that shell to re-read the group membership, but doesn't impact any other shells. I haven't logged out and back in. It isn't a convenient time. Will later today. Actually, Sunday is when I reboot, though logout/login should definitely be sufficient.

In the meantime, you should verify that your userid was appended to the /etc/group file like mine.

You can use sudo carefully (never with any GUI!!!!!) to write to the device.  If doing that requires using a GUI, don't.

---

### Post by billd01 on 2018-10-15
Hi, thnx for the info. I have confirmed that I am part of the root and dialout groups (using the users and groups utility). 
Plus I can successfully rw files on the same USB port  to a standard USB stick.

It seems to be a permissions issue for the Arduino IDE app. Do I need to grant access to the app?

Thnx
billd

---

### Post by TheFu on 2018-10-15
A regular userid shouldn't be a member of any root group.  That is a huge security fail.
BTW, I did reboot and my userid is a member of ,20(dialout) now. Odd. 

I know nothing about writing to arduinos. Is there some physical switch that needs to be set to allow external writes to it? It isn't a permissions issue on the Linux side.

---

### Post by billd01 on 2018-10-15
Hi, I started from scratch, removed and re-installed the Arduino IDE app (again, had already done it twice . . .), this fixed it.

I removed my self from root group (thnx for the advice), rebooted and confirmed Arduino IDE still has access to USB0.

Looks like I just had a failed initial installation for some reason.

Thnx for your help, I'm new to Linux and have learnt a lot in the last day.

cul
billd

---

