---
title: "Liveusb doesn't boot, stops at terminal."
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ShatPank on 2011-10-07
Running an abnormal setup (a PSIxPDA) has a gma500, and and weird wifi bluetooth combo card (3dsp something or other). 
Anyway, I know this hardware runs a previous version of Ubuntu, but with 11.10 I cant get the liveusb to boot.

Plymouth works (seemingly correct resolution - 800 x 480... looks it anyways)

Starting network security device
Starting bluetooth       OK

Flash up and are in red.

Then I come to a black cli screen.

Welcome to Ubuntu Oneiric (development branch) (GNU/Linux 3.0.0-11-generic i686)
 * Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$

Typing the command "unity" gets:

WARNING: no DISPLAY variable set, setting it to :0
unity-panel-service: no process found
compiz (core) - Fatal: Couldn't open display :0


Typind sudo lightdm lists loads of "*starting *****" text and then seems  to hang after:
checking for running unattended-upgrades:
*Stopping cold plug devices
*Stopping log initial device creaton

Thats where it freezes.


*NOTE... I want to get unity 2d working as device only has 1.1ghz processor and 1gb ram.

---

### Post by effenberg0x0 on 2011-10-07
Hey, type this:

sudo service lightdm start

If you can't get to a graphical session, type this:

sudo cat /var/log/Xorg.0.log
sudo cat /var/log/syslog

And post the results here, so we can see whats going on.

Regards,
Effenberg

---

