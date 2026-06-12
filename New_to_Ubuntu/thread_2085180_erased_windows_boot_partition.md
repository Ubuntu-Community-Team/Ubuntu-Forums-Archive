---
title: "erased windows boot partition?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by keither on 2012-11-17
Hello.
This is a question regarding a pc with two hdd.

background (quick)
pc came with windows 7 on one hdd and an open slot for a second disk.
i bought/plugged a new hdd in the open slot and installed windows 7 on that one (long story, don't ask why)

During boot i would get a screen asking if i wanted windows 7 or windows 7. 

I wanted to install ubuntu 12 on the original disk as the new installation of windows is used more.

installing ubuntu i chose to wipe the first hard drive and do a clean install (assuming that Boot alongside windows 7 would have given me all kinds of partition frustration)

Now the PC boots straight into ubuntu. I was hoping for grub.
I can see the second disk with all my windows files on it but can't get it to boot.

I've tried:
-changing boot order in bios (bootmgr missing)
-recovery mode and all bootrec.exe fixmbr etc that is on every other forum.

i THINK what happened was the boot partition (or sectors, not too knowledgeable in how that part works) was on the original disk and held the boot information for windows on the second disk. Is that even possible?


i now have ubuntu 12 on one disk (formatted, clen install) and windows 7 on the second disk.

i would love to have a grub menu that asks which os i want to boot. Since i last used ubuntu there seems to have been a swing from grub to grub2 so i don't even know where to start.

I have it in my mind that there is a grub configuration file where i just need to add windows (on sdb) and that would fix it... but i don't know how to do this.

any help is appreciated.

---

