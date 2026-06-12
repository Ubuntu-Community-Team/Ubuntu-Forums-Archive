---
title: "[SOLVED] Best File System for Ubuntu Desktop x86?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by DerekFord95 on 2008-08-21
I'm Dual Booting, I gave XP 56.4 GB, and it's A NTFS. I'm giving Ubuntu the rest, about 186 GB. I was wondering what's the best file system for Ubuntu Desktop 32-Bit? Ext3, Ext2, Fat 16, Fat 32, JFS?

Also, it says I have no root file system? WHat do I use as the mount point? /, /home, /root, what?

Thanks Everyone! :D

---

### Post by Sealbhach on 2008-08-21
I think ext3 is the standard one. Wait for further opinions though.


.

---

### Post by tangibleorange on 2008-08-21
> **DerekFord95 said:**
> I'm Dual Booting, I gave XP 56.4 GB, and it's A NTFS. I'm giving Ubuntu the rest, about 186 GB. I was wondering what's the best file system for Ubuntu Desktop 32-Bit? Ext3, Ext2, Fat 16, Fat 32, JFS?

Thanks Everyone! :D

yes ext3 is ubuntu's default and if you're trying ubuntu for the first time, ext3 is definitely the way to go. as suggested above though, someone else may have a killer reason to go with something else..

basically, unless you have a reason not to, go with ext3, and also a 1.5GB swap partition (FS type linux-swap)

---

### Post by DerekFord95 on 2008-08-21
> **tangibleorange said:**
> yes ext3 is ubuntu's default and if you're trying ubuntu for the first time, ext3 is definitely the way to go. as suggested above though, someone else may have a killer reason to go with something else..

basically, unless you have a reason not to, go with ext3, and also a 1.5GB swap partition (FS type linux-swap)
Swap Partion, just a swap area that's not used at all, so it can be used if installing another OS's to store the temporary installation files and stuff?

---

### Post by tangibleorange on 2008-08-21
> **DerekFord95 said:**
> Swap Partion, just a swap area that's not used at all, so it can be used if installing another OS's to store the temporary installation files and stuff?

erm not quite sure what you mean, but a swap area is used by the operating system if the RAM becomes too full during operation and it needs to dump some of its data. like a pagefile in windows. you dont NEED one, but its highly recommended you make one, especially if disk space is not an issue. it does need to be bigger than 1.5GB (unless you hibernate regularly, in which case it must be 2x your amount of RAM).

and yes, it can be used by other linux-based operating systems if you choose to install another one.

---

### Post by DerekFord95 on 2008-08-21
Ok, and it says I have no root file system. What mount point do I use?

/
/home
/tmp
/root
/usr
/var
/srv
/opt

I don't know and I don't want to have my desktop location be /home/home/derek/desktop, so I don't know if I choose /, /home, /root, or what.

Please help on this. :)

---

### Post by WRDN on 2008-08-21
The mount point for the root partition is "/".

I would recommend you use ext3, as it can recover well if the system must be shutdown very quickly or there is a power cut etc. If you want a fast filesystem though, then ReiserFS would be a better choice, though this is not very good as recovering from the aforementioned conditions, from what I've heard.

---

### Post by Sealbhach on 2008-08-21
What I did was:

 make a root partiton - I suggest around 12GB (mount point = /)

Home partition - mine was 90Gb but as much as you wish (mount point = /home)

finally, a swap partion, around 2x your RAM (mount point = swap)

It's recommended to do it that way so that if you upgrade or re-install Ubuntu there is minimal disruption to your settings and personal files. It even preserves your Firefox bookmarks. 

I'd recommend a scheme like that.


.

---

