---
title: "Live Compression"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by elysian2 on 2014-04-06
I'm wondering if there is something similar to Windows NTFS compression for Linux and if so, how to enable it in Ext4 Ubuntu. Windows live NTFS compression is usually able to compress my VMs by ~40% allowing me to store 200GB of data on a 128GB SSD.

[IMG]http://oi39.tinypic.com/10i9wzb.jpg[/IMG]

---

### Post by sudodus on 2014-04-06
I think ***encrypted home***, that you select when you install your system or create a new user, will not only encrypt but also compress the files in the home directory of that particular user. But it is risky: if you forget the password, nobody can help you recover the files.

---

### Post by Double.J on 2014-04-06
Hi there, Welcome to the forums!

The issue isn't the applications, it's the filesystem; NTFS can be compressed in place, EXT2-4 can't. There were a few projects about this back in the day, but truth be told as disks soared up to the terabyte scales, demand reduced. I've been googling for you, but a lot of them do not look to have been worked on for quite a long time. As this is related to data storage and the actual file system itself, I'd not recommend any that I saw on a recent release (some were last worked on in 2008!) 

obviously linux is fantastic at compressing (archiving) individual files and directories, but I know of nothing currently available for FS in place compression.

If you do find something, please let us know! (and please be careful that the project is still being maintained and compatible with your kernel and filesystem)

Best of luck, 

Jj

---

