---
title: "External HD powered off without permission, now cannot mount"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by swarup on 2008-10-02
I have a Maxtor 150 GB external HD which is around 7 years old and which works wonderfully. But just now I was working in Vista and someone pulled out the power plug of the external HD by mistake, thus effectively disconnecting the drive without permission. The external HD is now not recognized by Vista, and when I boot into Ubuntu, it correctly identifies the name of the HD, but cannot mount it. When I plugged the drive in while in Vista, Vista gave the message that the external HD's directory is corrupt. Can something be done to fix the situation so I will again be able to mount the HD and salvage the info? Thanks!

I have attached the screenprint of the error which Ubuntu gives when I try to mount the HDD.

---

### Post by nothingspecial on 2008-10-02
Post the output of 
```

sudo fdisk -l
```

---

### Post by swarup on 2008-10-02
> **nothingspecial said:**
> Post the output of 
```

sudo fdisk -l
```

```
:~$ sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd05e00eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19929   160079661    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2               6        1311    10485760    7  HPFS/NTFS
/dev/sdb3   *        1311       18178   135481344    7  HPFS/NTFS
/dev/sdb4           18179       19452    10233405    5  Extended
/dev/sdb5           18179       19392     9751423+  83  Linux
/dev/sdb6           19393       19452      481918+  82  Linux swap / Solaris

Disk /dev/sdc: 1008 MB, 1008730112 bytes
16 heads, 32 sectors/track, 3848 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x5f8cfffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              16        3848      981056    e  W95 FAT16 (LBA)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x703aaf88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS
:~$ 



```

---

### Post by nothingspecial on 2008-10-02
I`m guessing your external is this 

```
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x703aaf88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS
:~$

```

If it is then try this

```
sudo apt-get install ntfsprogs
```

Then fix your drive like so


```
sudo ntfsfix /dev/sdd1
```

---

### Post by swarup on 2008-10-02
No, I am sorry-- I had several other items also connected when I ran the "sudo fdisk -l". There was a 1000 GB HDD also connected, and a 1 GB flash drive. The external HD to which I refer is about 150 GB size. So that would make it the sda drive I believe. (Because the HDD to which I refer has only 1 partition on it, and that is NTFS. My internal HDD has Vista/Hardy dual boot, so that should be the sdb).

I've now disconnected the other two drives (sdc and sdd), but in the meantime for some reason lost the online connection on that computer. So I'm writing you from my laptop. When I get the desktop reconnected, I'll redo the "sudo fdisk -l". But knowing that the HDD is as I believe listed above as sda and not sdd, then should I just do the "sudo apt-get install ntfsprogs", and then change the second command to:

```
sudo ntfsfix /dev/sda1
```

---

### Post by nothingspecial on 2008-10-02
Do you have ubuntu on an external drive?

---

### Post by swarup on 2008-10-02
> **nothingspecial said:**
> Do you have ubuntu on an external drive?

Nope. So on review of the terminal output, I'm pretty confident that the drive of concern is the sda drive. Because sdb has to be my internal HDD. My internal HDD is the only HDD which has Ubuntu on it.

I believe sda is the drive of concern, sdb is my internal HDD, sdc is the flashdrive, and sdd is the other external HDD (which is running fine).

So assuming the drive of concern is sda, then should I just do the "sudo apt-get install ntfsprogs", and then change the second command to:

```
sudo ntfsfix /dev/sda1
```

---

### Post by swarup on 2008-10-02
If I try:

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```

Is there any risk to the drive in doing so? If not, I'll certainly try it now and see what happens. And if it doesn't work, then nothing is lost. But if there is risk involved in the above i.e. that it could damage the drive, then I'd better do more research in other directions before trying anything i.e. I could contact the drive manufacturer and see what they recommend etc.

---

### Post by nothingspecial on 2008-10-03
If you type ```
mount
``` in the terminal it will show you where all your drives are mounted for example here`s mine -

```
 mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-15-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)
```

You can see at the bottom my external drive is mounted at /media/disk and is /dev/sdb1. So I would type```
 sudo ntfsfix /dev/sdb1
``` if I had your problem. Of course your drive wont show. But it will tell you which ones it isn`t. My root folder  "/" (in which all other directories are contained is at the top ```
/dev/sda1 on / type ext3
```

When you unplug a ntfs drive without unmounting it creates an error log. When you plug it back in Ubuntu can see there is something wrong with the file system and wont mount it to prevent it corrupting its own filesystem. ntfsfix clears the log. Here`s a bit of reading.

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

[http://www.linux-ntfs.org/doku.php?id=ntfsfix](http://www.linux-ntfs.org/doku.php?id=ntfsfix)

I have no idea what would happen if you performed ntfsfix on the wrong drive, but I wouldn`t risk it. Notice in the second link it says

[SIZE="4"]Make sure you run ntfsfix after you unmount your volume, or you will face corruption of your volume![/SIZE]

The problem I have with this is that evey linux installation I have ever made has placed root on sda, this is why I asked if Ubuntu was on an external drive. However that may not be a problem.
Another option is to plug it into a windows machine and safely remove it to see if that clears the log. 

Please don`t do this unless you are sure. And certainly don`t do it on a mounted file system.

I hope this helps.

---

### Post by swarup on 2008-10-03
I confirmed very carefully which drive I needed to fix, in accordance with your directions. And it was very clear that it was sda1. I don't know why, but my root is on sdb and not sda. Anyhow, I just ran ntfsfix. Here is the output:

```
:~$ sudo ntfsfix /dev/sda1 
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 0...OK
Correcting differences in $MFTMirr record 1...OK
Correcting differences in $MFTMirr record 2...OK
Correcting differences in $MFTMirr record 3...OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Did not find any restart pages in $LogFile and it was not empty.
Remount failed: Operation not supported.
:~$ 
```

From what I understand, the final step in the repair happens when one boots into Windows. So I'll go there now, and see if Windows can mount the drive and recognize the files. But whatever happens, I want to thank you for all your kind help. It was really great. Thank you! :)

ADD: Well, I went into the Windows side, but and it ran chckdsk on bootup, but once I got into Vista it unfortunately still could not read the disk. It still recognizes it as it did before, but cannot open it.

The good news is that this morning I took a new external HDD and gave the order to clone the bad drive over to the new one. It worked! The new clone works perfectly, and all the files a working fine. Even video files which were on the drive, have been recovered and work fine. 

The original HDD is still, as I mentioned, not working. But perhaps I'll be able to format it and then restore all the original material back to it. Thanks again for all your help!

---

### Post by nothingspecial on 2008-10-03
As long as you`ve got your data that`s all that matters. Glad I could be of help.

---

