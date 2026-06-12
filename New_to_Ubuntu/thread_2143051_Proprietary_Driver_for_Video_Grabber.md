---
title: "Proprietary Driver for Video Grabber"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by 27grains on 2013-05-07
I was emailed a driver compiled for Ubuntu 12.10 64

I have been to IRC and emailed the creator and I can not get the driver installed.

VLC does not see and capture cards.


Where is the proper forum to ask for help?
Is it possible to email the tarball to an expert to see if it is written  correctly?

Inside of the main folder are  .svn, Bin, Include, Source.

The emailed instructions are:
[COLOR=#000080][FONT=Calibri]Here is the procedure on your linux.[/FONT][/COLOR]
[COLOR=#000080][FONT=Calibri]
1,into 'source' directory 
2&#65292;make
3&#65292;sudo modprobe vivi
4,sudo rmmod vivi
5,sudo insmod Drivers/XI100XE/XI100XE.ko 
6, ls /dev/video*
Then you will get a device as '/dev/video0'
I get errors and don't know how to look for "video0"[/FONT][/COLOR]

Thank You

---

### Post by TheJackal12 on 2013-05-07
Do you have the "build-essentials" package installed?

---

