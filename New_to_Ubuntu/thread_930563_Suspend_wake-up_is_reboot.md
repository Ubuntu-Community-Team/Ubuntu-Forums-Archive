---
title: "Suspend wake-up is reboot"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by olhat on 2008-09-26
After suspend my computer dies totally. I have to restart through on-off switch and reboot.   

System is Asus M2A-VM, amd64-dual and nvidia 8600gt  with 4G of memory and Ubuntu 8.04 with all updates.  Windows XP sleeps and wake-ups no problem.  

When googling one gets really scared since many people seem to get file system corruption as a result of clicking suspend.  That doesn't seem to happen with me though (fingers crossed:)).  Can one expect the suspend to work at all?

---

### Post by didiercool on 2008-09-26
Ya, I've learned to just not use suspend.  As far as I understand, that's the best option (unless, or course, you happen to be a programming wizard, and if that be the case, be my guest.)

~peace

---

### Post by olhat on 2008-09-29
I had to try anyway. Removed all usb sticks and got it to suspend and then the whole filesystem, mbr, grub and everything "censored by overdrank"ed up.:guitar:

---

### Post by maruchan on 2008-10-17
Why not look around at some of the suspend problems? I installed uswswap and my problems went away :)

---

### Post by homerhomer on 2008-11-05
I have the same thing. 

If you computer is 64bit with one cpu you might want to follow this bug in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515)

( sigh in and let the devs know that this affect you too ) 

Thanks

---

