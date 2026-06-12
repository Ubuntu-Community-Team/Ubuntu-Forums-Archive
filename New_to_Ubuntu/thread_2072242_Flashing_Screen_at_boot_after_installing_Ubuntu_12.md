---
title: "Flashing Screen at boot after installing Ubuntu 12.04"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by Steveo1983 on 2012-10-17
I'm new to linux.  I tried Ubuntu 12.04 64-bit on the live cd last night, then installed it replacing a bad copy of windows 7.   It asked me restart and to take cd out after install.  Upon it restarting the os starts up and before it comes to the log in screen it the screen flashes that purplish orange color and I hear the drum sound.   It just keeps flashing and nothing happens.   i tried to run off the live cd and install drivers for my HD 6850 and haven't been able to do so.  I also tried to press any key during the boot off the live cd and x'ed the nomodeset and I've opened the terminal and tried all but the last two option in this link [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) Not sure how to get to do the last two.   Anyone know what's the problem?   I thought maybe my video card needs a driver.   Any help would be appreciated.   My system specs: i3 2100 cpu, Sapphire HD6850 1 gb gpu, 4 gb 1333 ddr3 RAM, msi p67A-G43 (B3) mobo, WD Vraptor 160 Gb HDD, Antec 550w PSU.

---

### Post by Gnawnsense on 2012-10-17
Hi Steve! I'm an absolutely new Ubuntu user, too. On my first week, really. But, when I installed, I was having the same issue with the purple flashing screen that goes orangeish eventually. 

I've been searching for the last 10 minutes on the forum post that included the fix that worked for me, however, I can't find it.

One thing of note is, with this issue going on, you should be able to boot up into safe mode and fix the issue, which involved editing a text file that I now can't locate. But interestingly enough, when I attempted to boot myself into safe mode, it asked me at some point if I wanted to cancel and boot normally, I selected yes, and it booted normally.

My boot splash screen was what was causing the problem. And adding "noapic" at the end of one of the lines was part of the fix, but hopefully someone a little more knowledgeable can give you the precise info.

But you aren't alone in this odd issue. Just experienced the purple and orange flickering the other day. I'd continue searching around until you get a reply with some info :)

---

