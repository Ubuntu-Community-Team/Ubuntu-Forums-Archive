---
title: "How Do I Partion My Hard Drive???"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by josh_melvin on 2008-05-21
Hey!

I am wondering how i can use the ubuntu partition editor so i can have a dual boot with windows vista and ubuntu, anyone know how???

---

### Post by Therion on 2008-05-21
[Setting up Dual Booting](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm).

If you already have Linux installed, used the drop down menu on that page for instructions on dual-booting when Linux has already been installed first.

---

### Post by meborc on 2008-05-21
well.. i assume you have vista installed!?

if so you must defragment your windows partition so that all the data is in the beginning of the partition... you can find more info on that on the net... now you need ubuntu install cd... when you boot from the cd and start the installation choose MANUAL partitioning... you will see your vista partition... you can now make it smaller so free space is added to the end of the vista partition... then select the free partition and make (at least) 2 partitions: small one (gig max) for swap and the rest for ext3 (/ - root)

then continue with the installation as usual... be sure to backup everything you don't want to loose

more info here - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

(edit: getting old... late again)

---

### Post by josh_melvin on 2008-05-21
> **meborc said:**
> well.. i assume you have vista installed!?

if so you must defragment your windows partition so that all the data is in the beginning of the partition... you can find more info on that on the net... now you need ubuntu install cd... when you boot from the cd and start the installation choose MANUAL partitioning... you will see your vista partition... you can now make it smaller so free space is added to the end of the vista partition... then select the free partition and make (at least) 2 partitions: small one (gig max) for swap and the rest for ext3 (/ - root)

then continue with the installation as usual... be sure to backup everything you don't want to loose

more info here - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


(edit: getting old... late again)

No i have ubuntu installed first

---

### Post by nick_h on 2008-05-21
Here is a guide you may find useful:
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

When you install Vista you may lose your grub - if this is the case read [How to install Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351)

---

