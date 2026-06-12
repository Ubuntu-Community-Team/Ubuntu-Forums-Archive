---
title: "Can't Update"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by k5495 on 2008-11-29
I am using a linux only computer that I have had for about 4 months.  I am running ubuntu 8.04

I have always been able to download and install updates.

Last week I tried to update and got this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I got some information from this forum and was able to open a terminal and put in this command:

sudo dpkg --configure -a

the computer then did something that took about 5 minutes.

I still have the red arrow that indicates that I have updates and I still get the same error message when I try to install updates.

Why did something go wrong in the first place?

What is package a and why would I want to do something with it.

How can I get back to downloading and installing updates the usual way??

How can I go back and find this thread again and see if there are any answers to it.

---

### Post by Xiong Chiamiov on 2008-11-30
> **k5495 said:**
> 
Why did something go wrong in the first place?
You (or something, but usually you) interrupted the system while it was trying to update.

> **k5495 said:**
> 
What is package a and why would I want to do something with it.
You're not configuring package a, but giving dpkg the -a flag, as well as --configure.

> **k5495 said:**
> 
How can I go back and find this thread again and see if there are any answers to it.
Top left of this thread, go to thread tools -> subscribe.  You'll probably want to change it to "instant email notification".

> **k5495 said:**
> 
How can I get back to downloading and installing updates the usual way??

[Open a terminal]("http://www.psychocats.net/ubuntu/terminal"), then enter the following commands:
```

sudo dpkg --configure -a && sudo aptitude update && sudo aptitude safe-upgrade

```
Don't interrupt it, and take note of which packages it wants to upgrade.  It should work just fine, but if not, take note of the last thing it says.

---

### Post by sharks on 2008-11-30
do this:

sudo dpkg --configure -a && sudo aptitude update && sudo aptitude safe-upgrade

---

### Post by k5495 on 2008-12-15
I used this command as suggested:

sudo dpkg --configure -a && sudo aptitude update && sudo aptitude safe-upgrade

My computer runs for a long time printing out a long string.  

This is the beginning and end of string:

Top of file

tory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/input/input4/subsystem/input8/device/subsystem/devices/usb2/2-3/ep_00/subsystem/usbdev3.3_ep00/device/driver/usb1/1-1/1-1:1.0/ep_81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/input/input4/subsystem/input8/device/subsystem/devices/usb2/2-3/ep_00/subsystem/usbdev3.3_ep00/device/driver/usb1/1-1/1-1:1.0/ep_81/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/input/input4/subsystem/input8/device/subsystem/devices/usb2/2-3/ep_00/subsystem/usbdev3.3_ep00/device/driver/usb1/1-1/1-1:1.0/driver/2-2:1.0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.



end of file

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/input/input4/subsystem/input8/device/subsystem/devices/usb2/2-3/ep_00/subsystem/usbdev3.3_ep00/device/driver/1-1/1-1:1.0/usb_endpoint/usbdev1.3_ep81/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/input/input4/subsystem/input8/device/subsystem/devices/usb2/2-3/ep_00/subsystem/usbdev3.3_ep00/device/driver/1-1/1-1:1.0/ep_81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
dpkg: error processing base-files (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 base-files





 Any suggestions on what to try next??

---

### Post by Tatty on 2008-12-15
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)  This should help you with your questions on packages.

It sounds like something has gone quite wrong here.

Try putting in this command on its own and see if it complains:
```
sudo dpkg --configure -a
```

---

