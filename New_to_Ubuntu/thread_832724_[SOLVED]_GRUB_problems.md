---
title: "[SOLVED] GRUB problems"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by quanta4135 on 2008-06-18
I set up a dual-boot with Vista on my laptop, but after several successful boots into Ubuntu 7.10 through GRUB I booted into windows to access the internet (my installation has no internet access through my router, and no sound). After restarting my Toshiba logo shows up, but when GRUB goes to load this line is shown: "GRUB Loading Stage1.5"
The computer then goes and reboots itself and constantly goes on in this loop. I have already searched the forums but I am unable to find a thread which adequately deals with this problem. Any help will be greatly appreciated.

---

### Post by Bodsda on 2008-06-18
Boot the windows recovery disk, get to the recovery command prompt, and type

```
 fixmbr
```

then boot the Ubuntu live cd and reinstall grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this works for you.

---

### Post by meierfra. on 2008-06-18
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

---

### Post by quanta4135 on 2008-06-18
Thanks, that worked great. Now I've just got to work out all of the hardware problems that are starting to surface when I use Ubuntu.

---

### Post by meierfra. on 2008-06-18
Did you  boot into Vista after you fixed the problem, to see whether the problem recurs?

---

### Post by quanta4135 on 2008-06-18
Yes I did, and the problem did not reappear. However, I am having issues with my graphic card, sound card, and my wireless connection, so I'm kind of frustrated with my Ubuntu. Still, thats nothing with what I've dealt with in Vista.

---

### Post by sharks on 2008-06-18
For graphics card , it may be restricted. so go to system--administration and restricted drivers manager. it may work for u. ot install the necessary drivers.

For sound,go to system ---preferences and sound and select ur sound system.

---

