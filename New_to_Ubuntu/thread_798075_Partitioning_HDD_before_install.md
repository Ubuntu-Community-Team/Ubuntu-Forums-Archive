---
title: "Partitioning HDD before install?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Juggalo_5 on 2008-05-17
I'm new to Linux and such, and have been toying around with a Live CD and an Ubuntu partition on another computer, and am preparing to install Ubuntu on the computer I'm currently using. My intentions are to partition the HDD(250GB) into three peices, one 50GB partition for Windows XP Pro, one 50GB partition for Ubuntu, and one 150GB partition for shared storage, accessible and usable by both OS's. I have a few questions on the matter.

1-Is this a good way to go about partitioning my HDD?
2-How would I go about partitioning it properly for this setup?
3-How should the 150GB partition be formatted to ensure both OS can use it?

Any recommendations, answers, suggestions, or really any help on the matter is welcome and appreciated, I'm new to Linux, and even newer to partitioning :P

---

### Post by grannyw on 2008-05-17
Since you are new to Linux i suggest you to go for a guided partition the same partition with your Windows meanwhile.After that when you gather some experience you will be able to make additional partitions.

---

### Post by Juggalo_5 on 2008-05-17
Well, the thing is, that the Linux partition can't access the XP Partition, so if I want a file to be usable in both partitions, the file will have to exist on both partitions, effectively doubling the disk space that's used. Which is why I was wanting to make the 150GB partition.

---

### Post by Juggalo_5 on 2008-05-17
Is there an easier way to allow the Linux partition access to files on the XP partition?

---

### Post by Juggalo_5 on 2008-05-18
Shameless bump

---

### Post by starcannon on 2008-05-18
Heres a nice little how-to I picked up in google, give this a try it should get you rolling:

[Ubuntu tricks - how to mount your Windows partition and make it read/writable]("http://www.arsgeek.com/?p=585")

Oh and this other method is considered better and more stable, sorry I found it after I already posted originally

[Ubuntu Tricks - How to mount your Windows partition and make it read/writable with NTFS-3G]("http://www.arsgeek.com/?p=675")

 I also recommend taking the time to figure out the manual partition editor in the installer, its pretty straight forward and intuitive, all nice and graphical (just don't format or delete a partition you care about, and when setting up your Ubuntu partitions just create 3 of them, one will be a slash */* which is the root partition , another will be *swap* set its size to match your system ram amount if you want sleep/suspend/hibernate to work, and finally */home* this way if you have to ever reinstall Ubuntu all your good stuff that matters which is generally kept in /home will still be there when you get done with the reinstall (again you'll want to be sure to not format it in the future). It's not to bad once you've done it once, just wade your way through it once and be sure NOT to delete or format you MS Windows XP partition.

---

### Post by drubin on 2008-05-18
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Take a look at this site there is a section about portioning. might help you out

---

### Post by nhasian on 2008-05-18
Hello Juggalo_5,

Sounds like you are in the same spot i was in about two weeks ago.  I'm new to linux as well and am happily running Ubuntu 8.04 Hardy Heron on my laptop as my primary operating system.  I still have Vista on a separate partition in case i would one day ever need to boot back to it but honestly i've been able to do everything in linux since changing over.

First let me say that you can access your windows partition after booting into ubuntu simply go to Places on the Menu and click on the drive to mount it.  I had Windows Vista installed on DriveC and another partition called DriveD to share data between both linux and windows.  if you need to access an NTFS drive frequently then you probably want to auto-mount it on startup.  to do this you must edit your /etc/fstab file and add a line to mount the partition on startup. 

```
/dev/sdb1	/media/DriveD ntfs defaults,umask=007,gid=46 0 1
```

I had to use sdb1 because the partition i was mounting was the 2nd serial-ata drive in my system. and you can set the mountpoint whatever you like, I was just using DriveD so it would be the same in both windows and linux.  you can read/write to an NTFS partition in linux no problem so you can just make the shared partition NTFS.  You can do FAT32 instead of NTFS but I recommend against it because of the 4 gigabyte filesize limitation that FAT32 has.

I should mention that although i originally did have a shared data partition I discovered that some programs in linux didnt work properly when using the NTFS partition.  I think it has something to do with permissions or file statuses. In the end I just deleted the shared NTFS partition and created a new EXT3 partition instead just for linux.  I know that there are some software packages to allow windows to access an EXT3 partition but i've never used it so I dont know what kinds of limitations it may have.

NOTE: I've come across some posts that say you need to install NTFS-3G to be able to read or write NTFS partitions but I've installed Ubuntu 8.04 now on several computers and havent needed that extra software.  I just prefer not to install extra software if I dont need it.





> **Juggalo_5 said:**
> My intentions are to partition the HDD(250GB) into three peices, one 50GB partition for Windows XP Pro, one 50GB partition for Ubuntu, and one 150GB partition for shared storage, accessible and usable by both OS's. I have a few questions on the matter.

1-Is this a good way to go about partitioning my HDD?
2-How would I go about partitioning it properly for this setup?
3-How should the 150GB partition be formatted to ensure both OS can use it?


---

### Post by The Cog on 2008-05-18
Ubuntu CAN read/write NTFS. It's nothing special in the latest version 8.04 Hardy.

If doing a manual partition, don't forget to make a swap partition of a couple of gigs. You can use the installer partitioner - choose manua partitioning.

And make complete backups just in case - partitioning is a good opportinuty for disastrous finger trouble, especially with an unfamiliar partitioning tool.

---

