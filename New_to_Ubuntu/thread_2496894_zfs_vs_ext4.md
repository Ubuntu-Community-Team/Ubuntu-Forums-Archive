---
title: "zfs vs ext4?"
date: 2024-04-16
forum: New to Ubuntu
---

### Post by howtolinux on 2024-04-16
hello, question, i have heard that zfs is better then ext4 and that i should switch over to it, my question is


why?


why and how is zfs better then ext4?


thank you

---

### Post by #&amp;thj^% on 2024-04-16
You need to decide that for yourself.
In terms of performance, both ZFS and Ext4 offer good levels of speed and reliability, but they also have their own unique advantages and disadvantages.

ZFS is a modern file system designed from the ground up to provide high-performance storage capabilities. It leverages advanced data integrity checksums, copy-on-write snapshots, and RAID support for optimal performance on all types of hardware. **ZFS is ideal for large enterprise setups where scalability is critical**. ZFS has proven to be highly reliable.

Ext4 became a widely used file system because of its ability to manage large files and being a *reliable* file system. While it may not have all the advanced features of ZFS, it is generally faster and lighter, making it a good choice for many common workloads.

I could go on and on but you need to decide for yourself: [https://history-computer.com/zfs-vs-ext4/](https://history-computer.com/zfs-vs-ext4/)

```
inxi -p | grep fs
  ID-1: / size: 439.7 GiB used: 6.97 GiB (1.6%) fs: zfs
  ID-2: /boot size: 1.68 GiB used: 95.4 MiB (5.6%) fs: zfs
    used: <superuser required> fs: vfat dev: /dev/sda1
  ID-4: /srv size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-5: /usr/local size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-6: /var/games size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-7: /var/lib size: 434.75 GiB used: 2.02 GiB (0.5%) fs: zfs
    fs: zfs logical: rpool/ROOT/ubuntu_racofh/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_racofh/var/lib/NetworkManager
  ID-10: /var/lib/apt size: 432.8 GiB used: 70.2 MiB (0.0%) fs: zfs
  ID-11: /var/lib/dpkg size: 432.77 GiB used: 45.8 MiB (0.0%) fs: zfs
  ID-12: /var/log size: 432.76 GiB used: 30.5 MiB (0.0%) fs: zfs
  ID-13: /var/mail size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-14: /var/snap size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-15: /var/spool size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-16: /var/www size: 432.73 GiB used: 128 KiB (0.0%) fs: zfs
  ID-17: swap-1 size: 4 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda3

```

I will say ext4 has been very stable and proven for most Desktop user's

---

### Post by howtolinux on 2024-04-16
thank you for your reply

the link you gave 

[https://history-computer.com/zfs-vs-ext4/](https://history-computer.com/zfs-vs-ext4/)

is not working, it says page not found, but i would love to read it, thank you

---

### Post by #&amp;thj^% on 2024-04-16
> **howtolinux said:**
> thank you for your reply

the link you gave 

[https://history-computer.com/zfs-vs-ext4/](https://history-computer.com/zfs-vs-ext4/)

is not working, it says page not found, but i would love to read it, thank you

Server must be down, it shows not found for me as well.

EDIT: This has better information: [https://www.pitsdatarecovery.co.uk/blog/zfs-vs-ext4/](https://www.pitsdatarecovery.co.uk/blog/zfs-vs-ext4/)

---

### Post by TheFu on 2024-04-16
> **howtolinux said:**
> hello, question, i have heard that zfs is better then ext4 and that i should switch over to it, my question is


why?


why and how is zfs better then ext4?


thank you

There are many, many, pros and cons for every file system and volume manager. They are beyond what anyone should post as a reply here.  Perhaps if you read the wikipedia articles about ext4 [https://en.wikipedia.org/wiki/Ext4](https://en.wikipedia.org/wiki/Ext4) and zfs [https://en.wikipedia.org/wiki/Zfs](https://en.wikipedia.org/wiki/Zfs) and perhaps a few other file systems, you'll be better able to decide which is likely to be better FOR YOUR NEEDS.  

The real question is, "Which file system is better for any specific need?"

And for a high-level overview of a bunch of different file systems, [https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems)

Read those three articles completely, then ask specific questions.  Or do you want someone who doesn't know you at all to say "use ZFS, it is best."    
OR
"use ext4, it is best."

In reality, only you can decide, and only after a little learning to understand why there are differences.

I consider data to be the most important thing on my computers.  I don't really care about the hardware, but I never want to lose data or have it corrupted.  All other considerations are less important to me, but stability, ease of use, flexibility, compatibility, and the software license used, each matter to me as well.  Your considerations are likely different and definitely in a different priority order than mine. We are all different.

---

### Post by Skaperen on 2024-04-16
> **1fallen said:**
> Server must be down, it shows not found for me as well.

i would not say the server is down.  i get a response saying that page does not exist.  that suggests that the resource changed location and no resource tracking is available.  a search for "zfs" did not reveal that article.

---

### Post by MAFoElffen on 2024-04-17
I have used and tested a lot of storage solutions on Linux.

I recommend to many Linux Users, that they should use a "Volume Manager', whether that is LVM2 or ZFS. Keep that in mind.

Ext4 is a filesystem. Ext4 is an advanced level of the ext3 filesystem which incorporates scalability and reliability enhancements for supporting large filesystems (64 bit) in keeping with increasing disk capacities and state-of-the-art feature requirements. One of the main features is "journaling". ext4 uses checksums in the journal to improve reliability, since the journal is one of the most used files of the disk. This feature has a side benefit: it can safely avoid a disk I/O wait during journaling, improving performance slightly. The storage overhead of the EXT4 filesystem is about 5%. 

You can use the Ext4 filesystem a few different ways. You can format a partition as EXT4. You can format an LVM LV as Ext4. Ext4 has been the standard filesystem for most of Linux Distro's since sometime between 2010 and 2012.

ZFS is a filesystem with it's own logical volume manager. That can also be described the other way around: As a Volume manager, with it's own filesystem. ZFS's filesysem is ZFS uses a copy-on-write transactional object model. All the block pointers within the filesystem use checksum or hashes of the target block, which is verified when the block is read. So it checks that it is written before it passes the commit. ZFS stores at least two copies of metadata each time data is written to disk. The metadata includes information such as the disk sectors where the data is stored, the size of the data blocks and a checksum of the binary digits of a piece of data. In doing that, data integrity is higher than in other filesystems, but it also uses more memory than other filesystems to implement that. My recommended memory overhead for ZFS is 8 GB for ZFS itself, plus  1GB per TB of actual disk. That is the recommendations, but... I've run many systems with less. The laptop I'm posting from is ZFS-On-Root, I run many VM's and LXD containers, has 6 TB storage, and until very recently, only had 8GB RAM. (Now 16 GB, which is twice the max of what it said was the max RAM for this Laptop. LOL) The management overhead space is 3.2% of the storage container. (Less than Ext4)

Both have been production proven and been around for decades.

Ext4 is easier to use and is "more common". (Which is important for "Support" below.)

ZFS takes some ramp up to learn. Most people just scratch the surface of what it can do. Just as the same can be said about LVM2. Learn to use what your toolset is, and what you want to do... Then be productive. Most people who install Ubuntu with that advanced option, it just works, with some automated scrub and trim jobs that run once a month. 

Support... On this forum, there is me, the a few others that I would trust to answer questions about ZFS, and ZFS issues when someone comes up with some. Most every Member that provides support in the Support Sections here can answer questions on Ext4.

Like others recommended: Read up. In your reading, include "Volume Managers" & their ability to do snapshots. Do your homework. See what fits what you do. You want to play with them and see for yourself? Install KVM, and create 2 VM's, each with what you want to try. See what works best for you before diving in head first into reinstalling your main system. That is how I evaluate, and/or learn new things = Hands On. And inside of a VM, if you do something tragic while you are learning, it's only a VM.

---

### Post by MAFoElffen on 2024-04-17
Afterthought... One additional burning mentionable factor.

Ext4, you have to have the filesystem unmounted to repair. <--> ZFS you can repair the filesystem Live/Online.

That's it. Anymore could take up pages and volumes.

---

