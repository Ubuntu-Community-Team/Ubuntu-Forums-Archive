---
title: "Windows 8.1 and Ubuntu"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by petar4 on 2014-10-24
Hello :)
I would like to install Ubuntu and Win 8.1 on my laptop. I tried to do that but I had problems with partitions. Now I have Ubuntu 14.04 on my laptop. Can I install Win now, or erase Ubuntu, install Win first and then Ubuntu?
I have 1 TB HDD + 8 GB SSHD, so I'm not what to do with SSHD?

---

### Post by Neeraj_Hanumante on 2014-10-24
> I would like to install Ubuntu and Win 8.1 on my laptop.
I do have two OSs in my system.
First install win8.1 and leave unallocated space for ubuntu.
Win8.1 will consume 2 partitions out of four. This leaves two primary partitions for ubuntu.
Go ahead and install ubuntu with root in one primary partition and home in other. If you want to make more paritions, the rest of the partitions should be logical extended. Installing ubuntu later will allow Grub to take care of booting.

> I tried to do that but I had problems with partitions.
Try running this command in terminal and add the output in your post.
> sudo fdisk -l

> Now I have Ubuntu 14.04 on my laptop. Can I install Win now, or erase Ubuntu, install Win first and then Ubuntu?
It seems like your system is new and may need very less effort for backup. It may be possible to install win8.1 now, but it will be easier to go for fresh install as I wrote above.

---

### Post by petar4 on 2014-10-24
Should I create swap area?

---

### Post by Neeraj_Hanumante on 2014-10-24
> **petar4 said:**
> Should I create swap area?

Yes ... as thumb rule go for a swap size more than twice of RAM ...

---

### Post by Bucky Ball on 2014-10-24
Always easier to install Windows first. You can install Windows second, though. When you're done, you'll need to re-install grub. Easiest way is with Boot Repair. Good luck.

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

And 2Gb /swap is all you need. If you intend to hibernate a lot, the same size or larger than your RAM. The 'double the size' idea is archaic. ;)

Depending on what you use your machine for, you may barely even touch your /swap in general use, if at all. You can use Gparted in Ubuntu to leave unallocated space or create an NTFS partition for Windows to go on so when you get there you know what's what. Good luck. ;)

PS: There are a LOT of permutations on partition setup for Ubuntu apart from the example given. The /home partition is optional. Generally, all you need is:

/ = where the OS and settings go; and
/swap = 2Gb

With a /home partition, it would look like:

/ = 20Gb (is fine)
/home = where data goes, so big as you like;
/swap = 2Gb

In the first example, you'd want to make / big as all data goes there in a directory called /home, not a partition called /home. BUT, you can put symlinks in the /home directory to directories on different partitions on different drives, which means you / only needs to be 20Gb. A digress ...

---

### Post by petar4 on 2014-10-24
I have new problem now. I fixed my partitions, installed Win and Ubuntu, but when I start my laptop, I can only chose Ubuntu from GRUB?

---

### Post by Bucky Ball on 2014-10-24
Did you use boot repair to reinstall grub as outlined in my previous post??? :-k

You don't give a lot of information for us to help. There is no Windows to choose on your grub menu or you choose Windows and it doesn't boot. What?

Boot to Ubuntu, open a terminal and:

 ```
sudo update-grub
```

Reboot. As you're probably using EFI this might not work.

---

