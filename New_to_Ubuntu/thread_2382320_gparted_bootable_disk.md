---
title: "gparted bootable disk"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by aftermoon on 2018-01-11
Hello, this is my first hour in linux which means i m extremely new to this community,   ( :
my pc cant boot normally, saying " no bootable device ". so i checked the partitions via gparted, then i realized i have no idea what to do.
---so here is the screenshot.
question 1- is there any unnecessary partition that i can remove?
question 2- how can i make that 464gb sized partition active and bootable or mount it? because i installed linux in it. and i think this is the reason i have boot errors
question 3- should i select legacy or uefi in bios settings?

thank u in advance !!

---

### Post by ajgreeny on 2018-01-11
I know nothing about encryption but I suspect your problem is a result of having two esp partitions, both with the boot flag.

It may help us a lot more if you go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2018-01-11
Marking a partition as 'boot' or 'active' is not and has never been necessary for any Linux as it is for windows so that isn't the problem.  Posting the output of boot repair as suggested would be your best next step to get help.  Also, having a separate boot partition isn't at all necessary unless you are using LVM and would just complicate matters for someone new to Linux/Ubuntu.

---

### Post by oldfred on 2018-01-12
You have a standard UEFI install using LVM. Normally used on desktops with full drive encryption. Otherwise LVM is often used on servers.

You need to remove all the boot parameters on sda3 which is the container for all your LVM partitions.
And only boot in UEFI boot mode.

LVM is a very advanced volume/partitioning system, not recommended for very new users unless you must have full drive encryption.
If you need the full drive encryption you have jumped into the deep end of the pool and need to quickly learn to swim, or learn about LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

