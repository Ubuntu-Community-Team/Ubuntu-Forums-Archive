---
title: "Noob issue working with HDDs"
date: 2023-08-06
forum: New to Ubuntu
---

### Post by phrenemy on 2023-08-06
I'm not understanding how to refer to HDDs on my system.
I'm newish to Ubuntu. 

I'm wanting to sync an HDD using syncthing, but I'm completely lost now.

What is the address of my mounted HDD?
Yesterday, it was at /media/<PC_USER>/Plex.
Today. no idea. It's not at the above path.

The HDD is set to automount, which I used "Disks" to set up the fstab. This HDD is mounted.
Disks gives a "Mounted at /mnt/<HDD_NUM>", with link.
The link goes to the HDD partition and has the label Plex.

Is this /mnt/<HDD_NUM>/ an absolute path for the HDD? 

Can it be aliased so syncthing (and other programs such as plex) can refer to the alias?

Is there a command I can use to find the absolute paths to mounted HDDs?

Thanks,

---

### Post by oldfred on 2023-08-06
While you want to use UUIDs to boot, best to use labels or names you select for mounting.
If you label partitions and it gets automounted to /media/$USER, it will then use label, not UUID.
You can understand a label, where UUID is not easier kept track of.

When you used Disks to create a default mount, it used UUID. Again better to use a name or label. But in Linux case whether capital or not makes a difference. I labeled a partition as Data, but mounted as data. Not the same. You can have different labels & mount points.
And the default settings that Disks uses are typically not the best depending on format, ext4, ntfs, etc.

Post this to see entry you added to fstab:
sudo cat /etc/fstab
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,parttype
Use Code Tags to preserve formatting. Easy to add in Forum's advanced editor and # icon.

Also with external drives mounting with fstab, you need extra settings. If you try to boot with it unplugged, you may not boot or have very slow boot as it has to look for drive & then timeout.

---

### Post by phrenemy on 2023-08-06
thanks. greatly appreciated. 
I guess changing the fstab in Disks defaulted to the uuid. I would have thought the system would automatically have these various HDD IDs aliased, so I was getting lost. Who knows, maybe I still am. lol.
This HDD is internal, but it is good to know about issues with external drives for later.

(This PC is really a test case for moving a different system over to Linux, which I prefer to Windows.)

---

### Post by TheFu on 2023-08-06
First, in every OS except MS-Windows, when we say "drive", we mean the whole drive.  That probably isn't what you mean.  You probably mean "partition", since that is what every OS uses for splitting up a HDD.  You always want a drive to be split into at least 1 partition, perhaps more, then a file system is placed onto the partition for the most simple uses.  Data recovery and other disk tools look for partition tables, so while it is technically *possible* to put a file system onto the entire disk, that is a terrible, terrible, terrible idea.  

So, Linux makes references SATA/SCSI HDDs and partitions pretty easy.
/dev/sdc  <--- that's the whole HDD
/dev/sdc1  <--- 1st partition on sdc
/dev/sdc2  <--- 2nd partition on sdc

There are 2 types of partition tables for Linux/MS-Windows. Those are MBR (aka MSDOS) and GPT.  GPT should be used always since around 2012.  No exceptions any more.  GPT is better in many, many, many, ways. To my knowledge, there's only 1 way that GPT is less good which related to cheap USB drive controllers.  GPT doesn't have workarounds for limitations that the msdos partition table has. GPT supports 128 primary partitions.  The most I've ever setup, more because I could, not any great reason, was about 40 partitions.  In day to day use, I've had systems with 12 partitions, but they were specialized.

The "sd" part of /dev/sdX just relates to the kernel driver being used to access the storage.  PIDE drives use "hd", as in /dev/hda and NVMe devices use nvme0n1 for the first NVMe device, nvme0n2 for the second.  Partitions under NVMe add p1, p2, p3, p4 .... for example:
```
nvme0n1                  disk         931.5G                        
&#9500;&#9472;nvme0n1**p1**              part  ext2       1M                        
&#9500;&#9472;nvme0n1**p2**              part  vfat      50M   43.9M    12%         /boot/efi
&#9500;&#9472;nvme0n1**p3**              part  ext4     700M    343M    42%         /boot
&#9492;&#9472;nvme0n1**p4**              part  LVM2_m 930.8G
```

That shows a 1TB NVMe SSD with 4 partitions. Clear?

If you use virtual machines, the kernel driver to access those is different, so the driver name provide "vd", with the whole drive being "vda" or "vdb" and partitions being "vda1", "vda2".  See how the driver gets involved.

Because everything is a file on Unix-like operating systems, we can do some very powerful things with access to disk devices and whole partitions. Beginners don't usually need to know that, but in 5 yrs, you might like to do some kewl things using that knowledge.

---

### Post by donald187 on 2023-08-06
> **phrenemy said:**
> thanks. greatly appreciated. 
I guess changing the fstab in Disks defaulted to the uuid. I would have thought the system would automatically have these various HDD IDs aliased, so I was getting lost. Who knows, maybe I still am. lol.
This HDD is internal, but it is good to know about issues with external drives for later.

(This PC is really a test case for moving a different system over to Linux, which I prefer to Windows.)

Incidentally, Disks will let you mount using various options (such as labels).  Select partition, settings (gear icon), Edit Mount Options, Identify As....  But posting the output of oldfred's commands and getting their feedback would be better as they say that Disks may not provide the best settings.

---

