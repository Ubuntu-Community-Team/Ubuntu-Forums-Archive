---
title: "Virtual Box ERROR:FAILED TO START VIRTUAL MACHINE"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by prap19 on 2008-10-01
Hi
 i have UBUNTU 8.04(Hrady Heron) with GNOME 2.6.24-19-generic. I have just installed Virtual box from ADD/REMOVE PROGRAMS.When i add an image of OS from DVD it gets added but on starting it ,it gives the following error:

[COLOR="Red"]
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/COLOR]


[COLOR="Black"][B]CAN anyone help me on what could be the problem and what all i need to install or reinstall with detailed codes since i am an amateaur in UBUNTU.
[/B][/COLOR]

---

### Post by Peter09 on 2008-10-01
The part of the error message that says 

> Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups

is worth checking.

Go to System->Administration->Users and Groups

Check if you are in the vboxusers group.

---

### Post by Therion on 2008-10-01
[How to Get Virtual Box Up and Running](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html) -- This tutorial explains all.  Including why you're getting that error message and what to do about it.

---

