---
title: "trackpad issue"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by Max Clark on 2012-07-22
Hi, I've just installed ubuntu 12.04 on my dell studio 1745 laptop, dualbooted with Windows 8.

I'm having a few issues with the trackpad, to start with the mouse worked on the installer, as did the wireless driver (Broadcom STA thingy). Anyway after going from the installer to ubuntu proper neither the wireless driver nor the trackpad worked, so i hooked it up to a wired connection downloaded the wireless driver and hey presto both worked perfectly.

However (cue dramatic music) next time i booted the laptop up, while the wireless still worked like a gem, the trackpad stopped working. I managed to fix it by reinstalling the wireless driver and both worked perfectly until the next restart when yet again no trackpad.

Fair enough i know I can fix it temporarily by reinstalling the wireless driver, but I was wondering if anyone out in ubuntu expertland knew of a more permanent fix (other than a USB mouse, which is my current solution)...

thanks in advance.

---

### Post by anewguy on 2012-07-22
It sounds like a kernel module is loaded by reinstalling the driver but not being loaded on reboot.  Here's what I would do:

[LIST]
[*]open a terminal window
[*]type:  lsmod > mylsmod.txt
[*]now, if possible, temporarily connect a wired or wireless mouse
[*]reboot the PC, but DON'T do anything else - don't reinstall the driver
[*]open a terminal window and type: lsmod > mylsmodafter.txt
[*]if you look through both of those files you will probably find something in the first that isn't in the second.  Make note of it.
[*]you can close the terminal window and reinstall the driver now
[/LIST]

This gave us a list of the loaded modules while it was working and a list of the loaded modules after a reboot when it wasn't working.

Post back the name of the module.

You can also attach both files to the reply if you want to and we'll look at them.

---

### Post by Max Clark on 2012-07-22
ok heres what ive got;

---

### Post by anewguy on 2012-07-23
Hummmmm.....I checked the first list aginst the 2nd and really don't see anything (the hid and usbhid in the "after" list are for human interface device - i.e., the mouse you were using).

Got me stumped for now.

I am curious - is this Dell using an Alps touchpad?

---

### Post by Max Clark on 2012-07-23
its synaptics im afraid

anywho, did another lsmod with my quick fix don't know whether this is of any help

---

### Post by NikTh on 2012-07-23
Hi , 
please open a terminal and give the results of this command 
```
synclient -l 
```**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane.**

Also try to check if you have any FN+F? keys combo for disable/enable track-pad.

Thanks

---

### Post by anewguy on 2012-07-23
Looks like it's using the psmouse module to drive your touchpad - as used in many Dell's for an Alps touchpad.

I'm sure you'll still need the wired mouse plugged in temporarily to do this, so leave it plugged in and reboot, but don't do anything else.  Open a terminal window and type:

sudo modprobe psmouse

unplug the wired mouse and see if your touchpad works now.  If so, post back and we can make it permanent.

Also have 2 other modules loaded that I didn't find in the other lists as well:  arc4, which I'm not sure what it does, and joydev, which is supposed to be for joysticks/gamepads.

---

