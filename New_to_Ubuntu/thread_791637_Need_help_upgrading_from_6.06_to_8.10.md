---
title: "Need help upgrading from 6.06 to 8.10"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Verminox on 2008-05-12
I am currently using Kubuntu 6.06 LTS  (dual boot with windows xp) but I've got the Ubuntu 8.04 LiveCD so I want to install that instead.

But I don't want to just use the upgrade feature because I want to make changes to my partitions first.

Here's what I'm thinking of doing:
1. Go to windows, and delete the 2 Linux partitions
2. Insert LiveCD, and boot from it.
3. Use GParted to resize partitions.
4. Install Ubuntu 8.04

My main question is this: 

By deleting the linux partitions I would be erasing GRUB, so techincally I'd have to run the windows 'fixmbr' command to be able to boot into windows.

However, I don't have a windows cd currently. So if I instead boot using the LiveCD and install ubuntu on the empty partitions, would GRUB come back and solve my problem eternally? Will GRUB then detect both the new Ubuntu installation and the old Windows one?

Basically I want a way to remove Kubuntu 6.06, resize partitions, and install Ubuntu 8.04 without requiring a windows CD.

Please help me. Thank you.

---

### Post by shae on 2008-05-12
I would suggest one change in this.  Just boot into the Live CD.  Use it to delete the partitions, resize, and install all in one fatal swoop.  No you should not need the Windows CD to run fixmbr because that is only needed if you no longer desire Ubuntu and want to return to just using windows.

---

### Post by Verminox on 2008-05-12
> **shae said:**
> I would suggest one change in this.  Just boot into the Live CD.  Use it to delete the partitions, resize, and install all in one fatal swoop.  No you should not need the Windows CD to run fixmbr because that is only needed if you no longer desire Ubuntu and want to return to just using windows.

Yes but if I boot using the LiveCD directly I cannot resize the Linux partitions using GParted. They have a lock sign in front of them and I can't make any changes to them.

---

### Post by axor1337 on 2008-05-12
download a disk called ubd [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)  boot to it use its gparted to delete the parts the re boot to hardy live disk  and install.  or go out to a torrent site and get a copy of your version of windoze and use it to fix mbr.

---

### Post by dje on 2008-05-12
In gparted using the Live CD right click on the partition you wish to resize/delete and select Unmount, then the lock sign should go and you will be able to resize/delete it

hope that helps,
dje

---

### Post by lswest on 2008-05-12
you should be able to boot to the CD, double-click the install icon, and at the partitioning step choose "manual" and configure it as you see fit there.  If it has a lock sign, the drives might be mounted, or in hibernate, and not shut down properly?

---

### Post by Verminox on 2008-05-12
Thanks. Actually it was my swap partition that was locked and I had to click 'swapoff' but now I'm able to delete the partitions. At least I won't need to use the Windows disk manager now :-D

Oh and another small question: Why are my hard drives named sda1, sda2, etc. instead of hda1, hda2, etc. ?

---

### Post by Kapitän Rotbart on 2008-05-12
[http://www.frihost.com/forums/vt-36885.html]("http://www.frihost.com/forums/vt-36885.html") shows some answers to that. [http://ubuntuforums.org/showthread.php?t=422336]("http://ubuntuforums.org/showthread.php?t=422336") has a few more answers. sda and hda identify partitions on different types of hard drives. Since Ubuntu 6.06, Linux (the kernel) has been developed and includes better drivers (for instance the one that detects the type of hard disc you have). Apparently the change was noticed between Ubuntu 6.10 and 7.04.

It's just one of the things that come with innovation (sometimes things change...nothing serious in this case).

---

