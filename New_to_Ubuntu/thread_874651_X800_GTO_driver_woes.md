---
title: "X800 GTO driver woes"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Coach Hoach on 2008-07-30
Alright, so I'm new to Linux in general, but I've been doing my reading.  It seems that the proprietary driver/black screen is a common error, but I can't manage to make any of the solutions work.  I have an X800 GTO AGP video card and can't manage to get the drivers working properly.  Can someone provide and/or link me to a step-by-step walkthrough on how to get this card working properly?

---

### Post by bobnutfield on 2008-07-30
How did you install the driver?  This is an ATI card and should use fglrx.  One of my machines has an ATI chipset (X1250), and I have always been successful using EnvyNG to install the driver.  Have you tried that?

---

### Post by Troll_the_Great on 2008-07-30
+1 to EnvyNG.If you don't know how to install it, open a terminal and type:
```
sudo apt-get install envyng-gtk
```
After that you can find it under Applications-System Tools-EnvyNG.This will automatically install the latest driver for you.
Hope this helps.
Cheers!

---

### Post by Coach Hoach on 2008-07-30
Thanks for the tip, but sadly it didn't work.  EnvyNG installed all and well, but after completing the driver installation and restarting my computer, I again get the fated black screen after I see the Ubuntu logo and orange bar.  Note: I did this first thing on a completely fresh install.  Does this have a prerequisite or anything of that sort?

---

### Post by Troll_the_Great on 2008-07-30
Have you tried recovery mode?At boot up, if you dual boot you should see the grub menu (if you don't, press Esc after the computer starts).This is how it should look:
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Mentes86
Choose recovery mode then choose "fix X server" and boot up normally.
Post back any results.
Cheers!

---

### Post by Coach Hoach on 2008-07-30
Doing the fix X server lets me get to the logon screen but after inputting my name/password the computer hangs at a beige screen and goes no further.  But wouldn't this option disable the ATI drivers anyway?  It doesn't seem that hardy likes this video card very much.  Should I just reinstall and not bother with any video card drivers at all?

---

