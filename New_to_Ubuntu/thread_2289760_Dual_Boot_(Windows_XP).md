---
title: "Dual Boot (Windows XP)"
date: 2015-08-06
forum: New to Ubuntu
---

### Post by CleanWater on 2015-08-06
Hello everyone!

I just tried Ubunt and liked it a lot. Then I  created two partitions on my HD and installed XP first, after this I  installed Ubuntu on the other partition.
Before installing Ubuntu, my XP was working normally.
I'm used to do this with XP and 7 and it never happened before.

What I have to do to make both systems works?

Sorry for this dumb question, but I couldn't find any asnwer for it anywhere.

Thanks in advance!

---

### Post by QIII on 2015-08-06
Hello!

Could you give us just a little information about how XP is not working properly?  Aside from the fact that it's no longer supported, I mean.

---

### Post by howefield on 2015-08-06
What are you saying, that you can boot into Ubuntu but not Windows ?

---

### Post by mastablasta on 2015-08-07
> **CleanWater said:**
> ..., after this I  installed Ubuntu on the other partition.
!

are you sure you installed it on the other partition?

you don't create two partitions for this. you create windows partition and leave the rest of disk blank (unformatted). then on Ubuntu install will offer to install to free disk space (which is the blank unformatted part).

---

### Post by crusoe2 on 2015-08-07
When you first turn on the computer are you presented with different options for OS boot? 
 
What do you see? 

If none of these are relevant to your situation then...
Are you booted into Ubuntu immediately after turning on the computer?

---

### Post by riverguy99 on 2015-08-07
Your easy solution to this would probably be to delete the Ubuntu partition you installed, leaving just your functioning XP on the machine.  Then install Ubuntu from whatever media you are using (a thumbdrive, for example), ***and let Ubuntu create its own partition as it installs***.  Be sure to click YES on allowing Ubuntu to install any necessary files or updates from the Internet in its install progress, and make certain that your machine is online before you start.  After Ubuntu finishes installing, your computer will default-boot to Ubuntu, but in the boot-up process, you will be shown a menu allowing you to choose which OS you wish to use (Ubuntu of XP).  If you ignore this choice, the computer will boot to Ubuntu.

---

