---
title: "How do I add an exception to etc/modules?"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by Manhippo on 2012-09-04
Hi folks,

I'm trying to persuade a 3 mobile dongle to work with ubuntu 11. The problem is that it is not showing up in the networking dialogue. I've been trawling the forum, and have been following this fix

[http://ubuntuforums.org/showthread.php?t=1994588](http://ubuntuforums.org/showthread.php?t=1994588)

I've id'd my dongle and added the relevant line to etc/modules, and the dongle is no longer appearing as a usb drive in the file manager, but it is also still not showing up in the networking menu...

So, total newbie question, but, do I need to do something different to add the line as an exception, or is the code in question an exception in and of itself.

The line I added to /etc/modules is

usbserial vendor=0x12d1 product=0x1f01

As I say, it has done something, as the dongle no longer shows as a usb drive, but it hasn't made ubuntu recognise it as a mobile internet device.

The really frustrating thing is that there appears to be a folder on dongle with some kind of linux installation script, but I can't get it to run from nautilus, and I can't work out how to access the dongle from terminal. Needless to say, despite the fact there is code on their stick written for linux, 3 offer zero support or documentation beyond a poorly worded text file that says 'run ./install from terminal'. Tried it, nada.

Any help greatly appreciated,

J

---

