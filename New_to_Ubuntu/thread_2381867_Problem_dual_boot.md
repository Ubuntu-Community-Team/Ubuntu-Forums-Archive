---
title: "Problem dual boot"
date: 2018-01-06
forum: New to Ubuntu
---

### Post by ramadani-f on 2018-01-06
Hello everyone,

I just installed ubuntu 17.10 on a new hard disk. I have windows 10 on an ssd.

Since i installed ubuntu, i can't boot windows.

I tried a lot of methods that i found on forums, i changed the boot order on bios, i tried update grub, boot repair, windows automatic repair from DVD, etc ..

When i boot i get the grub selection with ubuntu and no windows.

This is the link that i get frome boot repair :
[http://paste.ubuntu.com/26331631/](http://paste.ubuntu.com/26331631/)

Can anyone look at this link and help me ?

Thanks

---

### Post by oldfred on 2018-01-06
Best not to use Boot-Repair's auto fix when you have multiple drives and different installs on each drive.
With BIOS/MBR you want each system to have boot loader in MBR of its drive.
Boot-Repair just installs one grub to MBR of every drive.

You are not showing a bootable Windows.
If sdc1 is your Windows install, it is missing the BCD.

Windows often has a separate 100MB boot partition with bootmgr & BCD, did you delete that?
You will have to use Windows tools to rebuild a new BCD, if you do not have backups.
You do not have to have the separate Windows boot partition and you do have bootmgr in the sdc1 partition.

---

### Post by ramadani-f on 2018-01-06
Thanks a lot for the answer, i will try this method

---

