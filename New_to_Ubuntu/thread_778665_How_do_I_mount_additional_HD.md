---
title: "How do I mount additional HD"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jd3010 on 2008-05-02
Hello,

Just installed 8.04 and it works fine

I added two HD and the are seen in "My computer" but I cannot access them nor mount them.

What do I have to do to access these 2 HD and use them as additional Backup space ?

Furthermore can I use both of them in a single Volume or do I have to keep them in 2 volumes ?

thanks

---

### Post by Archmage on 2008-05-02
You need to mount them first. But most propabtly you need to format them before you do this. And you should know what filesystem you want.

If you want to combine the two I would suggest using LVM.

---

### Post by jd3010 on 2008-05-02
Thanks,

Sorry but too new with Ubuntu how do I format and how do I automatically mount them.

---

### Post by neurostu on 2008-05-02
When you say they are seen in "My Computer" is that in windows?

To mount a drive you must make a directory for it to be mounted to:
```

sudo mkdir /media/MountToHere

```

the command to mount somethings goes as follows:
```

sudo mount -t <file_System> <root_of_drive> /media/MountToHere

```

the root of the drive is something that you are going to have to figure out, it is probably something like sda1, sda2, sdb1, etc...

One thing you might trying to figure out where the drive root is, Open up The Partition Editory (System-->Administration-->Partition Editor)
This shows all the partitions with their names.

Notice my attachment, all the partitions on /dev/sda/ are shown, so to mount my 2nd partition I would type:
```

sudo mount -t ext3 /dev/sda2 /media/HDD2

```

You can also click the drop down box in the top right to examine sdb, sdc etc...

---

### Post by neurostu on 2008-05-02
You can format the drives by with the Partition Editor I told you about, just select the "Unallocated Space" and make a new partition. If you want it to be accessible by windows and linux select FAT32 or NTFS as the filesystem, if you only want it accessible by linux select EXT3.


Note: (This doesn't really apply to formating)
The Partition editor can sometimes be slow and doesn't have the best status bar, so once you start and operation ALWAYS let it finish, if you don't you can really screw up your partition tables and lose all data on the drive being worked on.

---

### Post by Fenris_rising on 2008-05-02
i jusy installed a new 320GB HDD myself. it to didnt show up, then i remembered it needs formatting. luckily i had downloaded gparted live CD.
i booted up with the live cd selected my new drive and in this instance applied ntfs formatting to it (im putting minimal XP install on a third drive). once done reboot (remove disk) and when the PC reboots your new drives will be available. there are really good tuts out there. google it. gparted is a powerful tool if your woried about stuffing it up detach your OS drives so only the ones you want to deal with are available for messing with. hope that helps.im a noob to so you can do it if i can. if in doubt read lots.

regards

Fenris.

---

### Post by neurostu on 2008-05-02
Again, the GParted live CD is great, but if you have Ubuntu installed you don't need the live CD. 

Ubuntu comes with the complete GParted software, and you as long as you aren't trying to mess with the partition that ubuntu is installed on you can do everything the live cd can do.

Just go to System-->Administration-->Partition Editor

---

### Post by Fenris_rising on 2008-05-02
lol i wish i had known that, cheers for the heads up there.

Fenris

---

### Post by jd3010 on 2008-05-02
Thnaks for all, 

I will try all this and come back to you all.

by the way gparted is great...

---

### Post by jd3010 on 2008-05-05
Hi all 


I formated in ext3 the 2 extra HD and it worked fine with Gparted.

What do I have to put into Fstab to automatically mount the extra HD .

thanks a lot

---

### Post by logos34 on 2008-05-05
> **jd3010 said:**
> Hi all 


I formated in ext3 the 2 extra HD and it worked fine with Gparted.

What do I have to put into Fstab to automatically mount the extra HD .

thanks a lot

This will show you:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jd3010 on 2008-05-05
Hello,

thanks this worked fine and everthing is qvailable now ...

One more question can I create 1 Volume with 2 physical Hard disks ?

Thanks a lot

---

### Post by logos34 on 2008-05-05
> **jd3010 said:**
> Hello,

thanks this worked fine and everthing is qvailable now ...

One more question can I create 1 Volume with 2 physical Hard disks ?

Thanks a lot

there's LVM, but I believe you'd have to reinstall.

[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management)
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by jd3010 on 2008-05-05
Many thaks ... links are perfect: I will read through them carefully

---

