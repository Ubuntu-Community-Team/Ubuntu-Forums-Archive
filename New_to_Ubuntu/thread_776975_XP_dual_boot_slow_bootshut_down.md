---
title: "XP dual boot slow boot/shut down"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-05-01
i installed XP first, then ubuntu. everything seems to be running ok...except that windows takes a bit long to startup and extremely long to shut down. i dont know if its stuck at shut down or not. i click on shut  down and im still in windows, but i cant start up any programs. i can click shut down again or restart as many times as i want, but it dosnt do anything... is dual boot causing this?

---

### Post by martrn on 2008-05-01
> **waggingwabbit said:**
> i installed XP first, then ubuntu. everything seems to be running ok...except that windows takes a bit long to startup and extremely long to shut down. i dont know if its stuck at shut down or not. i click on shut  down and im still in windows, but i cant start up any programs. i can click shut down again or restart as many times as i want, but it dosnt do anything... is dual boot causing this?

Ubuntu boots grub, then boots grub stage 2 then vmlinux then the kernel and any init script.

Windows boots up, boots grub, boots the windows boot manager, boots the windows kernel enables the redgistry hives, boots up needed windows services, boots a antivirus programs, boots up any installed spyware, then proceedes to a login screen.

How could possiable dual booting effect the inefficiencies of windowze ?

[TO ADD]
The only way dual booting would effect windows, is if it is on the same hard drive and has become defragmented, or there is no space for a windows swap file.

---

### Post by Paqman on 2008-05-01
Yeah, i'd say partitioning is the only thing that could have affected Windows. Go and run all the normal maintenance tools available in Windows (Cleanup, scandisk, defrag)

[Auslogics Disk Defrag](http://www.auslogics.com/disk-defrag) is a good free tool that's a lot faster than the terrible defrag tool that comes with Windows.

---

### Post by martrn on 2008-05-01
> **Paqman said:**
> Go and run all the normal maintenance tools available in Windows (Cleanup, scandisk, defrag)

And also run the antivirus tools, spyware removal tools, and find some windows system checker tools as well.

---

