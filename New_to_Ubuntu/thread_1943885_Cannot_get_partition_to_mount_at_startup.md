---
title: "Cannot get partition to mount at startup"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by jgw111 on 2012-03-20
I've just switched to Linux for work, and the computer is now set up with 3 partitions: one with Windows7 (not relevant to this post), one with Linux (Ubuntu 11.10), and a common storage partition.

I'm trying to get the storage partition to automount at startup simply so I can place a link to it on the desktop rather than hunting through various file directories. But every option I've run across online doesn't work.

I've added the following to rc.local:
```
mount /dev/sda2 /media/STORAGE
```

I've made sure /etc/fstab has the partition properly included:
```
/dev/sda2                      /media/STORAGE  ntfs  auto,nls=iso8859-1,umask=000  0  0
```
(I added the "auto" myself; everything else was already in place.)

I even tried adding "sudo mount /dev/sda2 /media/STORAGE" to the "Startup Applications" list.

Nothing. Works. I suspect there is some deeper problem, because when I type "sudo mount -a" all the terminal, the partition doesn't get mounted (yet everything I've read claims it should; it is the "all" function, after all). But if I manually use "sudo mount /dev/sda2 /media/STORAGE", it works just fine.

What exactly am I doing wrong? Since none of the tutorials I've read address this point I assume it's something basic, but I don't have enough experience to know what.

Thank you for your help.

---

### Post by dmouck on 2012-03-20
Does /var/log/syslog or /var/log/messages say anything about the error? Also, I'm pretty sure you only need to have the entry in /etc/fstab; you do not have to add anything to /etc/rc.local

Also, here are the mount options from [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") for an NTFS partition:

rw,auto,user,fmask=0111,dmask=0000

---

### Post by Mark Phelps on 2012-03-20
I know this is not central to your current issue -- but it's a consideration for the future ...

Since you're sharing a data partition between Ubuntu and Win7, and you're automounting the partition at Ubuntu startup (and mounting it read/write I presume), then do NOT Hibernate Win7 when you're not using it.

If you do Hibernate Win7, do not be surprised if changes to the shared data partition "vanish" when you boot back into Win7, or if the filesystem is corrupted instead.

If you're going to share a partition with Win7, you need to do a "shut down" when you exit Win7.

---

### Post by Morbius1 on 2012-03-20
> when I type "sudo mount -a" all the terminal, the partition doesn't get mountedWhen you type "sudo mount -a" it will either mount the partition silently returning you to the prompt in the terminal or give you an error message. Did it give you an error message?

You might want to run the following commands to see:

How your system sees the partitions:
```
sudo blkid -c /dev/null
```What is currently mounted and where:
```
mount
```It could be that the partition in question is not at /dev/sda2 or there is not /media/STORAGE folder to mount to although that doesn't quite fit all your symptoms.

*BTW: Today, UUID's are used to specify the partition instead of /dev/sda2. The output of the blkid command above will tell you what the UUID is for your specific partition. So the line in fstab would end up looking something like this ( example ):*
```
UUID=0424FBBE24FBB0B2 /media/STORAGE ntfs auto,nls=iso8859-1,umask=000  0  0
```

---

### Post by Morbius1 on 2012-03-20
[COLOR=Blue]EDIT: Something that might fit your symptoms though:[/COLOR]
> But if I manually use "sudo mount /dev/sda2 /media/STORAGE", it works just fine.It's not an ntfs partition. The output of "sudo blkid -c /dev/null" will tell you that.

---

