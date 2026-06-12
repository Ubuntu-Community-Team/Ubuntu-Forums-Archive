---
title: "Partition table gone - fix utility?"
date: 2016-02-24
forum: New to Ubuntu
---

### Post by soundgeek on 2016-02-24
My old PC was running fine with Lubuntu in 3 partitions on the second (slave) IDE disk, with dual boot via GRUB of WinXP on the first (master) disk. Other partitions on the same second disk are windows partitions.

On booting now I don't get the grub screen. It just hangs with the disk LED on.

I tried a re-install from the DVD. This picked up the partitions correctly, but the install failed.

Booting an old Partition Magic CD shows there is no partition table on the slave disk. SCANDISK shows no faulty sectors.

I'm not familiar with Linux utilities. Is there a utility on the Lubuntu installation disk (14.05?) that will scan the second disk & re-construct the partition table?

---

### Post by grahammechanical on 2016-02-24
The Lubuntu/Ubuntu live session has GParted. It is a partition manager. Load that and see if it shows the partitions. At this point I would not assume that the failure is due to the partition table being gone. I would not expect an old version of Partition Magic to show Linux partitions. Especially, if it is a Windows version of the application.

You could have a drive failure. Use the live session to backup your files. The live session also has Disks utility which will give some information about hard drives. And if the drive has built in SMART data the Disks utility will show that information.

At what point did the install fail? It is useful to know things like this to assess the actual problem. You may need to restore the XP boot loader on the XP disk and then use the BIOS to select the XP disk to boot from so as to load XP. Which brings to mind this question:

On what disk is Grub installed? If, it is installed on the slave disk then you should still be able to load XP. You do not say if you can do that. But if Grub is installed on the Master disk then it may be the master disk that is failing.

Regards

---

### Post by soundgeek on 2016-02-24
Thanks for responding grahammechanical.

> **grahammechanical said:**
> The Lubuntu/Ubuntu live session has GParted. It is a partition manager. Load that and see if it shows the partitions.
GParted took a while to run, but shows all the expected partitions for sda and sdb, so it has found the partitions somehow.


 > **grahammechanical said:**
> At this point I would not assume that the failure is due to the partition table being gone.
 I would not expect an old version of Partition Magic to show Linux partitions. Especially, if it is a Windows version of the application.

You could be right there!

 > **grahammechanical said:**
> You could have a drive failure. Use the live session to backup your files. The live session also has Disks utility which will give some information about hard drives. And if the drive has built in SMART data the Disks utility will show that information.

'Disks' runs ok & the info it gives looks sensible. It says: "SMART is not enabled".


 > **grahammechanical said:**
> At what point did the install fail? It is useful to know things like this to assess the actual problem. You may need to restore the XP boot loader on the XP disk and then use the BIOS to select the XP disk to boot from so as to load XP.

I'm sorry I can't remember the point at which it failed. It was well after specifying the partitions & I think it had copied system files. I hadn't made notes. I had re-installed once in the past in order to fix a boot sequence problem and it all went fine.

 > **grahammechanical said:**
> Which brings to mind this question:
On what disk is Grub installed? If, it is installed on the slave disk then you should still be able to load XP. You do not say if you can do that. But if Grub is installed on the Master disk then it may be the master disk that is failing.
Regards

GRUB was installed wherever the install puts it! I'm guessing on sda. If I try to boot SDA at the moment, it fails to launch GRUB, so I don't even get WinXP as an option, let alone try to launch it.

All I get is disk activity (disk LED on) and it hangs there until I switch it off.

So maybe the boot sector/GRUB is corrupt. It is an old PC, pre-dating UEFI.

---

### Post by Bashing-om on 2016-02-24
soundgeek; Hello;

At this point it would be a good idea to see what it is that we are working with .
Post back the results of terminal commands:
```

sudo fdisk -lu
sudo blkid

```
with the thought in mind to re-install grub to the identified/known hard drive.
See then what results when booting this hard drive.

[INDENT][INDENT]just what I would do
[/INDENT][/INDENT]

---

### Post by soundgeek on 2016-02-25
> **Bashing-om said:**
> soundgeek; Hello;

At this point it would be a good idea to see what it is that we are working with .
Post back the results of terminal commands:
```

sudo fdisk -lu
sudo blkid

```


Sounds good Bashing-om :)

```

lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x077a077a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    28676024    14337981    c  W95 FAT32 (LBA)
/dev/sda2        28676025    78156224    24740100    f  W95 Ext'd (LBA)
/dev/sda5        28676088    78156224    24740068+   b  W95 FAT32

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb39605f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    25591805    12795871+  83  Linux
/dev/sdb2        25591806   320159384   147283789+   f  W95 Ext'd (LBA)
/dev/sdb5        28676088    78156224    24740068+   b  W95 FAT32
/dev/sdb6        78156288    88405694     5124703+  83  Linux
/dev/sdb7        88405758    98655164     5124703+   b  W95 FAT32
/dev/sdb8        98655228   209262689    55303731    b  W95 FAT32
/dev/sdb9       209262753   319870214    55303731    b  W95 FAT32
/dev/sdb10      319870278   320159384      144553+   6  FAT16
/dev/sdb11       25591808    28674047     1541120   82  Linux swap / Solaris

Partition table entries are not in disk order
lubuntu@lubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="1_1" UUID="1E2B-13DF" TYPE="vfat" 
/dev/sda5: LABEL="1_2" UUID="14FD-9187" TYPE="vfat" 
/dev/sdb1: UUID="88b0bfec-fbfc-4b2e-a074-3e50e30a6dad" TYPE="ext4" 
/dev/sdb5: LABEL="2_2" UUID="A473-72A7" TYPE="vfat" 
/dev/sdb6: UUID="cfebb5b1-d755-4d3d-9308-611d858ab753" TYPE="ext4" 
/dev/sdb7: LABEL="2_4" UUID="33E8-4441" TYPE="vfat" 
/dev/sdb8: LABEL="2_5_INSTALL" UUID="7BA5-CED0" TYPE="vfat" 
/dev/sdb9: LABEL="2_6" UUID="0B22-2F6E" TYPE="vfat" 
/dev/sdb10: SEC_TYPE="msdos" UUID="52DC-FCBD" TYPE="vfat" 
/dev/sdb11: UUID="9108dea7-a7b4-4bee-89e7-94fd1b46c50f" TYPE="swap" 
/dev/sr0: LABEL="Lubuntu 14.04.2 LTS i386" TYPE="iso9660" 
/dev/zram0: UUID="4bcbca06-0069-439a-801e-5278074f5451" TYPE="swap" 
lubuntu@lubuntu:~$ 


```

---

### Post by Bashing-om on 2016-02-25
soundgeek; Yuk ..

The good news is that 'fdisk' and 'blkid' see the partitions.

Is grub's boot code installed to this second (sdb) drive ?
What results when attempting to boot with the boot priority in bios set to boot this 2nd hard drive as the 1st boot priority ?

Do we consider installing the boot code to sdb ?
Maybe take a check and mount the 'buntu partition(s) from the liveDVD and verify that your data is still there .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by soundgeek on 2016-02-29
I can see a grub directory on the sdb disk. I used to boot sda, grub would kick in and default to Lubuntu.

all the partitions mount  & the data looks ok :)

I've just gone a bit wild & ran boot-repair: [http://paste.ubuntu.com/15246368/](http://paste.ubuntu.com/15246368/)

The result is that the PC boots... WinXP! No grub or option to boot Linux.

I'm not sure what to do now.

---

### Post by Bashing-om on 2016-02-29
soundgeek; Welp;

How about we install grub to the sdb drive, and in bios boot this drive ?
Leave Windows on sda alone ?
> 
=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

As XP is no longer supported, I do not know what one can do to RE-install Windows boot code onto the sda drive; IF Windows boot code is messed up on that drive.

[INDENT][INDENT]just what I would do
[/INDENT][/INDENT]

---

### Post by soundgeek on 2016-03-01
> **Bashing-om said:**
> soundgeek; Welp;

How about we install grub to the sdb drive, and in bios boot this drive ?
Leave Windows on sda alone ?

As XP is no longer supported, I do not know what one can do to RE-install Windows boot code onto the sda drive; IF Windows boot code is messed up on that drive.
[INDENT][INDENT]just what I would do
[/INDENT]
[/INDENT]


The boot-repair has fixed the WinXP boot fine.

I would like to boot sda as now/before and have grub allow me Linux as default and WinXP as an option, but I don't know how to do that. There's a boot/grub directory on sdb. I'm surprised boot-repair did not find that.

Thanks again for your support. I may escape windows yet!

---

### Post by soundgeek on 2016-03-01
I've re-installed without formatting /home. Grub has returned & with a Win XP option too.

I've still no idea how the boot sector got lost.

Thankyou for guiding me Grahammechanical and Bashing-OM :)

---

### Post by Bashing-om on 2016-03-01
soundgeek; Great ...

Pleased you found a solution. As to how the boot code got corrupted.... strange things happen.
The good thing is that with 'buntu; it is always fixable - one way or another.

[INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

