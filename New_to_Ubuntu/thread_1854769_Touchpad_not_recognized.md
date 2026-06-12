---
title: "Touchpad not recognized"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by benpearsonnelson on 2011-10-05
My touchpad is not recognized.  My cursor jumps all over the place when I try to type.  I searched and found pages and pages of similar problems and proposed solutions, but none work for me.  I am using 11.04, I have no touchpad options under "mouse preferences".  I installed touchpad indicator, but it does not disable my touchpad.  I also downloaded touchfreeze and psmouse-elantech-v6 but after extracting the files from the .tar.gz, I have no idea how to install this software.  I installed synaptiks but it reported back no touchpad was found.  I tried following a couple of step by step instructions, but they seen to assume a touchpad that does not appear in the code.  I found a command line I could use in terminal to disable the mouse (i.e., touchpad) but that does not do me much good since I need to be able to navigate within documents and other places, that as far as I know, require a cursor.  I am using an Acer Aspire 5560.  I have fashioned a little piece of cardboard that I can place over my touchpad which works fine,  but I am going to have a hard time evangelizing linux when people see my fix.  If anyone can help me, I would greatly appreciate it.

---

### Post by simontaylor on 2012-10-25
did you find a solution for this problem?

best,
Simon

---

### Post by squakie on 2012-10-25
It's an old thread, so if you are having the problem you may want to start your own.  That being said, if you are having this problem you may want to look for the xserver-xorg-input-synaptics package and be sure it is installed.  You also may want to install the tpconfig package.

There is also another possibility:  Depending on the make and model of the laptop it might be using an Alps touchpad instead of a synaptic-based touchpad.  I ran into that on some Dell laptops - I just don't remember off the top of my head what I had to do to fix it.

---

### Post by simontaylor on 2012-10-25
thanks squakie,

main problem is sensitivity - asus u43jc - erratic jumping cursor annoying when typing.

have tried: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64")

and: [http://ubuntuforums.org/showthread.php?t=1615564&page=12]("http://ubuntuforums.org/showthread.php?t=1615564&page=12")



Best,
Simon

---

### Post by squakie on 2012-10-25
You may already have it installed, but tpconfig allows you to configure a touchpad - I don't know if that includes sensitivity or not.  ;)

---

### Post by simontaylor on 2012-10-25
checked xserver-xorg-input-synaptics - installed
installed tpconfig - terminal gave mismatch to LSB values...?

---

### Post by simontaylor on 2012-10-25
synclient gives no synaptics driver loaded

---

### Post by squakie on 2012-10-26
Well, let's take a look at another thing:

- reboot 
- immediately after the reboot, look at the /usr/log/Xorg.0.log file (you could do less /usr/log/Xorg.0.log) and search for things like synaptic or alps or touchpad and see if there are some error messages there.  That may give us a hint as to where to look.

Also:

- have you tried the gconf editor?  There is a place there for the touchpad and normally (if this hasn't changed in 12.xx) you can set some of the touchpad options there

- do you have any kind of mouse attached as well?  I've had my wireless mouse left turned on even though I was using the touchpad and the result was that the vibrations from typing was moving my wireless mouse just very little but enough to make the cursor go nuts on the screen.

---

