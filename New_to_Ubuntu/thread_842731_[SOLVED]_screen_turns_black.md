---
title: "[SOLVED] screen turns black"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by azery on 2008-06-27
I recently installed the new ubuntu (8.04) but I'm having a number of problems. Being new to Linux, I'm looking here for some help. I'll post different problems in different topics, in order improve the readability of the answers.

The first problem is my screen:

When using Linux, the screen turns black from time to time. It only stays black for  approx. 1 second, after which every thing seems normal again. Then, let's say a minute later, the screen flickers again.

The flickering happens independently of the program I'm using, although firefox seems to cause the flickering coming more often (might be an impression)

hardware:

AMD Athlon XP 1700+
radeon 7500
nec multisync lcd 2070 NX, connected via digital cable (not the VGA thing)
resolution 1200x1600, 60 Hz. (default set by ubuntu)

Note that the problem is not present with windows XP.

---

### Post by phidia on 2008-06-27
What driver are you using for the ATI card? 
After one of these screen flickers open a terminal and type dmesg | tail
maybe there will be some useful output there or in /var/log/xorg.

---

### Post by azery on 2008-06-27
dmesg | tail yields

[   70.443795] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   71.325593] NET: Registered protocol family 17
[   72.017241] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   72.017660] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   72.017994] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   72.392690] [drm] Setting GART location based on new memory map
[   72.392747] [drm] writeback test succeeded in 1 usecs
[   77.329364] NET: Registered protocol family 10
[   77.330157] lo: Disabled Privacy Extensions
[   88.197785] eth0: no IPv6 routers present
No idea what it means, but at least it shows something about my video card and its AGP settings :-)

the only files I have are Xorg.0.log.old and Xorg.0.log. As they are quite long, you can find them in attachment.

thanks for helping out.

---

### Post by phidia on 2008-06-27
Are using compiz? If so turn it off and see if that stops the flicker.
There are a lot of threads on screen flicker and particularly with ATI video cards-so it might take some effort to track what's going on down.
There is a [thread here]("http://ge.ubuntuforums.com/showthread.php?t=769020") you can check out.

---

### Post by azery on 2008-06-28
I appear to be running compiz. I looked a little bit to the link you provided and I'll try some of the "solutions" that are provided there.

Strange that I did not find the info with google. I found similar issues, but all related to nvidia cards.

thanks for the feedback.

---

### Post by Chokkan on 2008-06-28
I have the same problem but I think I figured out that there is some problem with my monitor cable. The screen would turn black just as you described and sometimes I would get a NO SIGNAL message and the screen would fail to come on.

---

### Post by azery on 2008-06-30
The link mentioned above provided a workaround: disabling the eye candy (visual effects set to none) seems to remove the flickering.

thanks for all the help.

---

