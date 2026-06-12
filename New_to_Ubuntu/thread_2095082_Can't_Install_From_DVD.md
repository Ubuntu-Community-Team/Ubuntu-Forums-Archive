---
title: "Can't Install From DVD"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by netpaid on 2012-12-15
Problem:  

I have downloaded and burned to disk the 32 bit and 64 bit versions of 12.10 . I have tried both versions. Here's what happens...

I insert DVD, shut down laptop, turn back on.  I get two icons at bottom of screen:
  
                            keyboard = person (i think)

nothing happens, DVD stops running.  Reboot.  Get the icons at bottom, nothing happens so I hit the space bar (Itried the enter button and that does nothing). 
 
Now I get a Ubuntu menu...then the language choices. I choose English, hit 'enter' and am back on the menu.  I choose to Install, hit enter...screen goes black then cursor is found at top left flashing and DVD shuts down within 10 seconds.

I left it for several hours on the 6th try as I had to run out.

My system:

Win7 home premium
SP1
Intel(R) Core(TM)2 Duo CPU  T9600
4.00 GB 
64 bit

---

### Post by audiomick on 2012-12-15
I'm stumped about what might be wrong, but just in case it is relevant, tell us what video card you are using.

Also, can you boot into the "try without installing" option?

---

### Post by netpaid on 2012-12-15
Thanks for the reply back!

Same exact thing happens when I 'boot into the "try without installing" option'

Another step I took was opening the .exe file while running in windows.  i was given an option to install another boot up option, which now lets me choose which operating syatem to launch when I start up.

Video driver....hmmmmmm...sorry but I'm not 100% on this!  

But maybe this?  NVIDIA GeForce GT 220M

---

### Post by Cheesemill on 2012-12-15
Try booting with the nomodeset option set.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by audiomick on 2012-12-16
> **netpaid said:**
> Another step I took was opening the .exe file while running in windows.  i was given an option to install another boot up option, which now lets me choose which operating syatem to launch when I start up.

That sounds like a wubi install
[https://help.ubuntu.com/community/Wubi]("https://help.ubuntu.com/community/Wubi")

I'm not sure, but I think you should probably remove that before you try to do a proper install.

---

### Post by debodas on 2012-12-16
What program did you use to burn the ISO to a disk?
If you can, burn the ISO to another blank disk using imgburn (its free), and try again.

Sounds to me like the disk wasn't burned fully, which is why you're having issues.

---

### Post by audiomick on 2012-12-17
> **kingnick42 said:**
> ... burn the ISO to another blank disk...


Check the md5sum of the .iso before you do (or has someone already mentioned that?)
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

and use the slowest burning speed available.

---

