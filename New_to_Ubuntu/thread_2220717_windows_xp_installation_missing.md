---
title: "windows xp installation missing"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by endoch on 2014-04-29
hello,

im newbie in linux.
i have an old compaq presario v2200 installed with windows xp.
my harddisk is 40 gig.

then i installed ubuntu 12.04 with 20 gig partition:
Model: ATA FUJITSU MHV2040A (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  20.0GB  20.0GB  primary  ext4         boot




Error: /dev/zram0: unrecognised disk label  

endoch@laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


now, how can i check if my windows installation is still on the other 20gig harddisk and get it back so i can do dual boot windows xp and ubuntu on my laptop?

any feedbacks are welcome.
thanks,

---

### Post by Impavidus on 2014-04-29
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It may be able to recover your Windows or at least provide good diagnostics. But if you quoted the full output of **sudo fdisk -l** in your post, then your Windows partition is gone. You may be able to recover some files using recovery tools, although I hope you had backups.

---

### Post by endoch on 2014-04-29
hello Impavidus,

thanks for your reply.
here is my fdisk -l output
Disk /dev/sda: 40.0 GB, 40006680576 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78138048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe434e434


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39060609    19530273+  83  Linux

does it means that i lost my windows installation?

cheers,

---

### Post by kyle19 on 2014-04-29
.

---

### Post by Vladlenin5000 on 2014-04-29
Please ignore the previous post, no need for that.
No, currently there's no Windows in your PC and we know that just by checking the output you just gave.

---

### Post by Warren Hill on 2014-04-29
You certainly won't be able to get everything back but you might be able to recover some of it.

I hope you either had good backups or didn't have anything on the PC you don't mind losing but If not your best hope of recovering data is here:

[DataRecovery - Community Help Wik]("https://help.ubuntu.com/community/DataRecovery")i

---

### Post by endoch on 2014-04-29
thankyou [COLOR=#000000]Vladlenin5000 and Warren Hill,

its ok, its a fresh windows install, i dont have any important there.

if im not mistaken, currently i only use my 20Gig from 40Gig? how can i use all of 40Gig that i have?

thanks,
 [/COLOR]

---

### Post by Mark Phelps on 2014-04-29
> i only use my 20Gig from 40Gig? how can i use all of 40Gig that i have?

You only have one partition, so you are using the entire disk already.

---

### Post by endoch on 2014-04-29
Hello Mark,

thanks for your info. i've got all the info i need then.

gonna mark this thread as solved.

cheers,

---

