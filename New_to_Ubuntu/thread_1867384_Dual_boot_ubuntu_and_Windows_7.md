---
title: "Dual boot ubuntu and Windows 7"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Arendyl on 2011-10-22
I previously had a windows xp computer, I replaced xp with ubuntu 11.04. I bought a windows 7 installation disk, and I want to know how to install it. When I go to boot from the disk, it only gives me the option of "replace previous windows" or "advanced partitions". When i go to advanced, no options will be accepted. Any help is appreciated. Thanks

---

### Post by card_ace on 2011-10-22
I personally have only ever installed ubuntu after windows, but I think if you use ubuntu to shrink your linux partition and have unformatted space on your hard drive then you'll be able to use that.  like I said I've always started with windows then put on linux, so I can't promise that will fix it.

---

### Post by crip720 on 2011-10-22
As stated above you must have free space for Windows.  Windows will also wipe out your grub.  You will have to reinstall grub after, to dual boot.  Should have a Ubuntu cd handy.  Search  in these forums for reinstalling grub.  Good luck.  Colin

---

### Post by WilliamVallance on 2011-10-22
I installed Windows 7 fresh after Ubuntu 11.04 with these steps.

A. Use gparted to split the drive into two partitions.
B. Install Windows
C. Booted up with Live USB and used Boot-Repair
D. Rebooted and enjoyed my new dual boot system.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Arendyl on 2011-10-22
> **WilliamVallance said:**
> I installed Windows 7 fresh after Ubuntu 11.04 with these steps.

A. Use gparted to split the drive into two partitions.
B. Install Windows
C. Booted up with Live USB and used Boot-Repair
D. Rebooted and enjoyed my new dual boot system.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I downloaded Gparted,  But I have no idea how to create a new drive. I have a sizable hard drive, 230g, so that shouldnt be a problem.

---

### Post by Steve R. on 2011-10-22
I was researching this question in anticipation of installing Windows 7 over Windows XP that uses Ubuntu as the primary operating system. 

I ran across this Ubuntu article: [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by WilliamVallance on 2011-10-22
When I first tried GParted I found this site to help me out with pictures.  Remember you can only split your drive using the free space and not what already is written on.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Arendyl on 2011-10-23
When I try to install windows onto the new partition, its says unavailable, athat the dive need to be NTFS. Any idea how to do this?

---

### Post by Mark Phelps on 2011-10-23
You can't install Windows into an existing Linux filesystem partition.  You need to have UNFORMATTED space.  That means you have to shrink the existing partitions and leave some room.

When you boot then using the Win7 DVD, select the unformatted space and the installer will format it for you.

---

### Post by drillerccg on 2011-10-23
[http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)

should be very similar. I used this method last year and worked/works great.

edit: I just remembered I took the advice of the author and used his second article (mentioned in the first paragraph)

[www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)

---

### Post by pritam_par on 2011-10-25
Windows do not let you keep the Ubuntu together.  you have to install Windows first and then Ubuntu.

---

### Post by card_ace on 2011-10-27
you CAN install windows 2nd, its just a tad more difficult because Windows will overwrite the Grub for linux.  when finished you just have to reinstall Grub and everything works.

---

### Post by oldfred on 2011-10-27
Windows only knows how to boot from one active (boot flag) partition.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Mercdya on 2011-10-27
One way to Dual boot Ubuntu 11.10 with Windows 7 (no virtual box) is to use a program called wubi. I have tried other methods this one is by far the easiest. Download the wubi installer here [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Pros: Will start computer as a Windows computer with the option to use Ubuntu (not the other way around!!) Allows you to allocate up to 30GB for Ubuntu. Also allows for easy uninstall of Ubuntu through add and remove programs in Windows7 itself. Ubuntu seems to run much faster this way then through a virtual Machine

Cons: Did not see Advanced partitioning options. You will have to restart the computer to choose which Operating system you want to use.

---

### Post by card_ace on 2011-10-28
This may help with the partioning.  This is a screenshot of my setup.  The top two partitions, "Dell Utility" and "Recovery" are both setup by the factory and I haven't messed with them at all.
/dev/sda3   ntfs    is my Windows 7 partition
/dev/sda5   ext4    this is the main filesystem partition of Ubuntu
/dev/sda6   linux-swap   similar to the swap file on a Windows system (in case your system runs out of memory for programs, it stores them in a section of the harddrive)

---

