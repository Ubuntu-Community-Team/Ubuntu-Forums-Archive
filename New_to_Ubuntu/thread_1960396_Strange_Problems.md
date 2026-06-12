---
title: "Strange Problems"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by Boab1993 on 2012-04-17
I am fairly new to ubuntu
 
I built my own computer around a month ago and decided to install ubuntu on a blank hard drive. The hardware was fully compatible but ubuntu was not responding when prompted to start the setup, it just hung. Eventually i found out by trial and error that setting the system in 'nomodeset' for the setup worked and after reading up on how to change startup commands editied the splash in grub2, changing the 'quiet splash' line to 'quiet splash nomodeset'. The computer now runs perfectly on ubuntu 11.10.
 
However im trying to create a multi-boot system with windows XP and the same problem appears to occur with windows, it runs till the setup gets to 'setup is now starting windows'
 
Im wondering if the hardware isnt compatible without driver updates or if there is a way i can change the start-up similar to how i did with ubuntu.
 
Thanks 
 
Hardware;
 
Amd Llano A6-3670K 2.7GHZ(FM1)
Gigabyte GA-A55M-S2V AMD A55(FM1)
Intergrated Radeon 6530D Graphics
500W Power
Viewsonic VW2014wm

---

### Post by MG&amp;TL on 2012-04-17
I confess to having no idea; but you might get more response on a windows forum-try [http://forums.cnet.com/windows-xp-forum/](http://forums.cnet.com/windows-xp-forum/)

-the only thing I can think of is that windows does not like partitioning-it much prefers to be setup on its disk and then partitioned later.

---

### Post by anewguy on 2012-04-17
+1  Use the LiveCD, start disk utility, and post back what your disk shows for partitions.  Windows will require a non-Linux partition, preferably bare.  Sometimes it wants to be the 1st partition on the disk.  You will also lose the ability to boot Ubuntu after you install Windows until you boot the LiveCD and run update-grub again.  The tested and recommended way to do this is to install Windows first and run 2 defrag's.  Then boot the Ubuntu LiveCD and choose install.  When it asks how you want Ubuntu installed, select other/manual and this will start the disk partitioner.  1st shrink the size of the Windows partition to make room for Ubuntu.  Then create a swap partition and then 1 or more partitions for Ubuntu.  Now just let the installation continue.  When you're done you'll get a menu at boot so you can choose between Windows and Ubuntu.

If you have any questions, please post back.

Dave ;)

---

### Post by Bucky Ball on 2012-04-17
> **anewguy said:**
> The tested and recommended way to do this is to install Windows first and run 2 defrag's.  Then boot the Ubuntu LiveCD and choose install.  When it asks how you want Ubuntu installed, select other/manual and this will start the disk partitioner.  1st shrink the size of the Windows partition to make room for Ubuntu.  Then create a swap partition and then 1 or more partitions for Ubuntu.  Now just let the installation continue.  When you're done you'll get a menu at boot so you can choose between Windows and Ubuntu.

If you have any questions, please post back.

Dave ;)

Windows first on first drive, first partition is how it likes it. BUT, DON'T resize Windows with Linux software. This can cause real problems. Do it with Windows software (depending on Win version this is possible within Win). Either way, before resizing Windows defrag til you can defrag no more!

When you install Windows just install it on a 30Gb partition (not the whole disk) and leave the rest free. This is easy to do from the Win installer. Then install Ubuntu on the free space. No need to resize Win partition. 

Four primary partitions is the max but you can have three and an extended and put as many logical drives inside the extended as your machine can handle (if you want).

---

### Post by Boab1993 on 2012-04-18
Sorry for the late reply.

Can i run disk utility without having windows installed? 
Also my partition according to g-parted is just the main hard disk  (500GB) under ubuntu and a swap, it says unmounting it isnt possible  because of its mount point "/", so i assume id have to re-install ubuntu  and partition it from there? but ive been told that its bad to  partition windows on ubuntu anyway.

However i posted the same question on the general help forum and someone told me that because my motherboard is FM1 the reason windows crashes during setup install is cause this chipset is new and i need drivers for it? 

Ive tried downloading the ones for both VGA and Windows Xp but they're windows files and wine seems to run up with fatal errors while running them, ill try gettng some .dll shells and see how it goes on that front

Thank you all for your help

---

### Post by flurospar on 2012-04-18
> **Boab1993 said:**
> Can i run disk utility without having windows installed?

Yes.

> **Boab1993 said:**
> 
Also my partition according to g-parted is just the main hard disk  (500GB) under ubuntu and a swap, it says unmounting it isnt possible  because of its mount point "/", so i assume id have to re-install ubuntu  and partition it from there?

For such cases , use the Live CD.

> **Boab1993 said:**
> but ive been told that its bad to  partition windows on ubuntu anyway.

You must always first install Windows and then Linux, because Windows setup will overwrite Linux's bootloader with its own. Then you can't boot/access the Linux partition.

> **Boab1993 said:**
> Ive tried downloading the ones for both VGA and Windows Xp but they're windows files and wine seems to run up with fatal errors while running them, ill try gettng some .dll shells and see how it goes on that front

You must run Linux drivers on Linux. Wine is meant not for running drivers but other windows applications. Search for Linux drivers for your hardware. Don't run the Windows versions with Wine, they'll never work!

---

### Post by anewguy on 2012-04-18
> **Bucky Ball said:**
> Windows first on first drive, first partition is how it likes it. BUT, DON'T resize Windows with Linux software. This can cause real problems. Do it with Windows software (depending on Win version this is possible within Win). Either way, before resizing Windows defrag til you can defrag no more!

When you install Windows just install it on a 30Gb partition (not the whole disk) and leave the rest free. This is easy to do from the Win installer. Then install Ubuntu on the free space. No need to resize Win partition. 

Four primary partitions is the max but you can have three and an extended and put as many logical drives inside the extended as your machine can handle (if you want).

You can resize an XP partition with no problem as long as you run at least 2 defrag's before you start.  Windows will run a chkdsk next time it starts and all will be fine.  This has worked countless times for me with never a problem.  However, you are 100% correct when it comes to Windows 7.  You must use the Windows 7 tools to shrink a Windows 7 partition or you'll have a real mess.  Plus with Windows 7 you have to watch out for dynamic partitions. 

Dave ;)

---

### Post by Bucky Ball on 2012-04-18
> **anewguy said:**
> You can resize an XP partition with no problem as long as you run at least 2 defrag's before you start.  Windows will run a chkdsk next time it starts and all will be fine.  This has worked countless times for me with never a problem.  However, you are 100% correct when it comes to Windows 7.  You must use the Windows 7 tools to shrink a Windows 7 partition or you'll have a real mess.  Plus with Windows 7 you have to watch out for dynamic partitions. 

Dave ;)

Yep, totally. I forgot to mention XP is fine with this. Cheers. ;)

---

### Post by anewguy on 2012-04-18
> **Bucky Ball said:**
> Yep, totally. I forgot to mention XP is fine with this. Cheers. ;)

Hope you're doing well friend! ;)

Dave ;)

---

### Post by Boab1993 on 2012-04-25
Sorry for the late reply i was out of town for a while.

Thank you all for your help, it has been finally fixed.
Turns out the chipset drivers were the problem after all, and i had to use a virtual machine to install them.
After that the set-up ran fine and i now have windows fully installed on my desktop

Again thanks for the help

Boab1993:D

---

