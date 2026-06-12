---
title: "cannot mount windows partition"
date: 2017-11-23
forum: New to Ubuntu
---

### Post by latitude.d630 on 2017-11-23
Hi 

I've forgotten the password for an old laptop running xp so i'm trying to clear it using a bootable usb drive and the "chntpw" package. It seemed to be going fine until i tried to mount the windows partition (sda2 i think) when it gave the error message:

"Mount is denied because the NTFS volume is already exclusively opened. the volume may already be mounted, or another software may use it which could be identified for example with the help of the 'fuser' command."

i'm totally new to Linux so i don't understand what the fuser command is giving back 

"sudo fuser /dev/sda2" gives back "5011"

I've also tried mounting the hard drive via the "computer:///" tab but that gives the error message:

"Unable to access "ST9160823AS" can't mount file" 

As i say i'm totally new to Linux and any help would be greatly appreciated

---

### Post by ajgreeny on 2017-11-23
It sounds as if your old XP partition was not closed cleanly, or XP not shutdown properly, so Ubuntu thinks it is still in use, maybe hibernated.

This has become a big problem for the uninitiated dual booting Ubuntu user who has not turned off the fast-start hibernation which is now the default in Windows 10 as the Windows partituions are again unusable to Ubuntu.

If you can still get into the Windows XP system from bootup, do so, then shutdown XP fully, and you should be able to mount the partitions in Ubuntu again.

---

### Post by latitude.d630 on 2017-11-23
thanks ajgreeny!

 works now

---

### Post by ajgreeny on 2017-11-23
Great news.
Please mark as Solved from the Thread Tools menu up top.
It is very useful for users searching the forums.

---

