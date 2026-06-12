---
title: "/dev/mapper/ubuntu--vgswap_1 is not ready yet or not present"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by steve185 on 2015-01-29
Installed Ubuntu 14.10 on an old ASUS laptop a couple of months ago. Everything was working fine until last week, when I attempted to boot and got the above message. It will take me to a command line interface where I can log in, but GUI will not load. I get the following messages:

[  86.186987] systemd-logind[1655]: failed to start unit [email]user@1000.servic[/email]e: Unknown unit: [email]user@1000.servic[/email]e
[  86.187040] systemd-logind[1655]: failed to start user service: Unknown unit: [email]user@1000.servic[/email]e

It appears my data is intact, but I can't DO anything with it. Is there a way to repair the install, or can I at least save the data that is on the system? I am a fairly new user of Linux, and don't know my way around the command line that well. I can enter commands that are presented here, but don't know what the Linux commands are. Been a long time since I used the command line, and that was MS-DOS!

---

### Post by JeQhdMD on 2015-01-29
Did you try "startx" via command line?

Re your data, use a live linux CD or usb.   Use the file mgr program to copy your data to usb stick.   A great live CD is "Porteus" . . based on Slackware.   Can get it from distrowatch.com.

---

### Post by steve185 on 2015-01-29
"startx" gives the following error:

/usr/bin/x: error while loading shared libraries: libxshmfence.so.1: cannot open shared object file: No such file or directory

---

### Post by JeQhdMD on 2015-01-30
See link below:    looks like this is a serious bug in systemd . . . fix being worked on but that's been the case for several months.   This bug affects a relatively small group of users running nvidia and ati chipsets on buntu 14.10.

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)

Was probably triggered by a routine update of system including kernel.   A kernel roll-back may help (see Grub bootloader options).

Intel based systems not affected.

Suggest you save your key data files using a good live CD (even your install dvd should work).   _Then download and install ubuntu 14.04 LTS which is not affected._

There is a suggested work-around, and that is to install "systemd-sysv" which will then prompt for removal of sysvinit-core.    I am not familiar enough with these startup systems so do this only if you have nothing at stake (i.e., your data saved before, and no issue with doing a reinstall of 14.04 "Trusty Tahr".

As you can access the Terminal (command prompt ala windows), to install:  sudo apt-get install systemd-sysv (worth a shot if your data is copied off to usb-stick . . . )

[COLOR=#0000ff]**_More detailed info from the Debian bug reporting process:_**[/COLOR]

[COLOR=#000000][FONT=serif][COLOR=#3C3C3C][FONT=sans-serif]**From:** Gasha <gasha@pie-dabas.net>[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]**To:** [EMAIL="756247@bugs.debian.org"]756247@bugs.debian.org[/EMAIL][/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]**Subject:** Re: Bug #756247: systemd upgrade[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]**Date:** Fri, 17 Oct 2014 11:32:53 +0300[/FONT][/COLOR]
[/FONT][/COLOR]
After lots of testing and troubleshooting, i managed to fix my problem.
Maybe it helps others also.

I installed systemd-sysv package, and that in process requested to 
remove sysvinit-core.
I suspect, that it is dependencies problem, or missing actions in 
postinstall scripts or something.

root cause is dbus is not started with --systemd-activation flags, and 
systemd cannot register with dbus infrastructure.
for example "systemctl" command then return "Unknown error -1", cannot 
contact D-Bus.

Debian installation itself should be systemd aware, but it is broken, 
and that causes XFCE desktop to be unusable.

This should be checked when upgrading wheezy to jessie in future.

Gatis

---

### Post by JeQhdMD on 2015-01-30
Steve . . . any luck with the work-around suggested on debian.org by Gasha??

---

