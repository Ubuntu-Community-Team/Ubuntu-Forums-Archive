---
title: "Erratic cursor and highlighting behavior--gedit"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by mark allyn on 2012-11-21
Hello everyone,
 
Yesterday I downloaded and installed 12.10 using WUBI onto a HP 32-bit Win7 laptop.  I have been trying to edit a GTK program using gedit (and also xedit).  Both exhibit similar behavior. 
 
There are two problems.  First, the cursor misbehaves, intermittently jumping around (usually regressing several lines) and inserting text I'm writing.  So, I have to hit "UNDO" or else go back and erase the offending insertion.  It's really blooming annoying.  The second problem is that frequently text will be highlighted for no reason that seems related to what I am typing.  This will then produce an erasure of text that is fine. 
 
The HP keyboard on this laptop has always been a stinker, but I've not previously had these problem with it.
 
I don't see anything on "system settings" that is related to the problem.  Any suggestions?  
 
Cheers,
Mark Alyn

---

### Post by mark allyn on 2012-11-30
Hello everyone,
 
Since creating this thread I have searched high and low on the internet.  I found a few posts describing the same problem, but there were never answered.  So the problem remains.  My guess is that it is related to the fact that Ubuntu was installed inside Windows 7 rather than alongside.  Unfortunately, my Windows laptop has no spare partitions and as far as I can tell re-using a partition for Ubuntu is a very messy affair and prone to failure.
 
However, this morning I bypassed the laptop keyboard with a wireless keyboard.  This solves the problem, albeit in a very ugly way.
 
I would appreciate anyone with insight into why the wireless bypass works getting back to me.
 
Cheers,
Mark Allyn

---

### Post by mark allyn on 2012-12-01
Hello everyone,

After seeing that wireless keyboard fixed the problem, I thought the solution might be to disable the touchpad.  I did this by using "xinput set-prop 12 "Device Enabled" 0" command.  Turning off the touchpad has done the trick.

Cheers,
Mark Allyn

---

