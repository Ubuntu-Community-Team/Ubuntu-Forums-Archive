---
title: "How to increase Ubuntu disk size"
date: 2016-12-08
forum: New to Ubuntu
---

### Post by giridhar.07 on 2016-12-08
I seek advice in dealing with the size of my Ubuntu partition. I run Ubuntu 16.04.1 LTS and Windows 10 as dual boot on my laptop.

My Linux partition is 49 GB. I find it small for my computing needs. I have a 120GB empty partition (NTFS) that I would like to merge with my Ubuntu partition.

---

### Post by Jeroen_Mathon on 2016-12-08
Hey giridhar.07,

I recommend against merging because NFS will give you several issues on Linux(Stability whise).

Furthermore i recommend you shrink the NSF partition and grow the Ubuntu partition using [http://gparted.org/livecd.php](http://gparted.org/livecd.php) 
Please take in account that this is a lengthy process because it will need to move all the data from the partition being shrunk ahead.

Depending on the size of your NSF partition this can take a while.

---

### Post by yancek on 2016-12-08
Is the ntfs partition contiguous with the Ubuntu partition?  That would simplify things.  Obviously, you won't be able to use Ubuntu on an ntfs partition although you can share data between windows/Ubuntu on it.  Post an image from GParted showing your drive partitions.

---

### Post by oldrocker99 on 2016-12-08
I have a 32 GB partition, and it has served my needs for quite some time.

Just sayin'.

---

### Post by giridhar.07 on 2016-12-08
[COLOR=#000000]Hello [/COLOR][COLOR=#000000]yancek,

I am attaching the screenshot of GParted for your reference. I want to add /dev/sda8 to my  linux partition.[/COLOR]

---

### Post by giridhar.07 on 2016-12-08
Hello oldrocker99,

Few days ago I ran out of disc space on Ubuntu and it wouldn't boot. I received help on this forum to fix it. I don't want to encounter that issue again. Hence I want to increase the Linux partition size.

I agree with your remark. Changing my computing lifestyle might make this request irrelevant. However I would still like to pursue my intention. As a new Linux user, I want to welcome this knowledge.

---

### Post by leunam12 on 2016-12-10
I would:
1-Download Clonezilla and burn to DVD or USB. (burn image)
2-Boot Clonezilla and backup entire hard drive to another hard drive.
3-Boot Ubuntu live session from USB.
4-Run gparted.
5-Delete Swap partition (sda7)
6-Expand Linux partition using the unallocated space (120.85 GiB)
7-Create a new Swap partition.
8-Reboot.

If it boots and everything is as you want, you have succeeded. If it fails, boot clonezilla again and restore your hard drive to the original state and seek for another solution.

---

### Post by Impavidus on 2016-12-10
leuman12's idea should work fine, but there's one thing to keep in mind. When you delete and later recreate the swap partition, its UUID will change, so you'll have to edit the /etc/fstab to reflect that change. That's quite easy and even if you don't do that, the computer will continue to boot (altough it will give you a warning).

---

### Post by giridhar.07 on 2016-12-15
Thank you leunam12 for your suggestion. Apologies for my delayed response. I was travelling and had limited internet connection.

I am currently working on an important project and need my laptop. I will certainly try your recommendation after 2 days and post the results on this thread.

---

### Post by giridhar.07 on 2016-12-15
Thanks Impavidus for your pointer.

---

