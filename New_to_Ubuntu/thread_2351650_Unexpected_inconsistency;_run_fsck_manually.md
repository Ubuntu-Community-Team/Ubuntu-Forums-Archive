---
title: "Unexpected inconsistency; run fsck manually"
date: 2017-02-05
forum: New to Ubuntu
---

### Post by igorsrb on 2017-02-05
Ubuntu 16 ( I update it religiously) not loading following problems with BIOS/visual signal every so often. 

Got the following:

```

/dev/sda5 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
Fsck exited with a status code 4
The root filesystem on /dev/sda5 requires a manual fsck

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built in shell (ash)
```

Any help is greatly appreciated.

Thanks

---

### Post by TheFu on 2017-02-05
Unmount the partition using it and run **sudo fsck /dev/sda5** manually.
If it is the / partition, then you'll need to **sudo touch /forcefsck** and reboot. It will be checked after the reboot.

Or

You can boot from alternate media (optical or flash drive) and run it manually.

"16" isn't enough to tell us the correct version.  16.04 is an LTS and has 5 yrs of support.  16.10 is NOT an LTS and will be supported until June/July this year.  Most people should stay on 16.04.x for the most support and greatest stability until 18.04 is released.

---

### Post by Bashing-om on 2017-02-05
igorsrb; Hello; Welcome to the forum.

The partition sda5 deserves a close inspection.
From a liveDVD(USB) booted in try ubuntu mode - terminal:
Post back the results - Between code tags - of terminal commands:
```

sudo parted -l
sudo fdisk -lu
sudo blkid

```
So we know what we are working with.
Then we do as the system advises and run a manual file system check from the live environment.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-04-15
```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  496GB   496GB   primary   fat32           boot, lba
 2      496GB   986GB   490GB   extended
 5      496GB   982GB   486GB   logical   ext4
 6      982GB   986GB   4192MB  logical   linux-swap(v1)
 3      986GB   1000GB  14.5GB  primary   fat32           lba


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba
```

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2bfb4dc8

Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1  *          2048  967784881 967782834 461.5G  c W95 FAT32 (LBA)
/dev/sda2        967786494 1925206015 957419522 456.5G  5 Extended
/dev/sda3       1925206016 1953524079  28318064  13.5G  c W95 FAT32 (LBA)
/dev/sda5        967786496 1917016063 949229568 452.6G 83 Linux
/dev/sda6       1917018112 1925206015   8187904   3.9G 82 Linux swap / Solaris

[COLOR=#ff0000]** Partition 2 does not start on physical sector boundary.**[/COLOR]
Partition table entries are not in disk order.




Disk /dev/sdb: 14.6 GiB, 15640600576 bytes, 30548048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x02b9d71a

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 30548047 30546000 14.6G  c W95 FAT32 (LBA)


```

```
/dev/sda1: LABEL="FD_BETA9SR2" UUID="3873-1AF8" TYPE="vfat" PARTUUID="2bfb4dc8-01"
/dev/sda3: UUID="B498-74ED" TYPE="vfat" PARTUUID="2bfb4dc8-03"
/dev/sda5: UUID="e76ac860-e581-46e6-ab26-933e2b6cc202" TYPE="ext4" PARTUUID="2bfb4dc8-05"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="1272-E8C8" TYPE="vfat" PARTUUID="02b9d71a-01"
/dev/loop0: TYPE="squashfs"
/dev/sda6: UUID="8fca17e0-decf-4a43-b073-2e96424e6fe8" TYPE="swap" PARTUUID="2bfb4dc8-06"


```

---

### Post by yancek on 2017-04-15
sda5 is your Ubuntu partition so the methods suggested in post # 2 above should work.

---

### Post by igorsrb on 2017-08-17
so pretty much the same problem came back a few months later

```
   Model: ATA ST1000LM024 HN-M (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/4096B
 Partition Table: msdos
 Disk Flags:  
 
 
 Number  Start   End     Size    Type      File system     Flags
  1      1049kB  496GB   496GB   primary   fat32           boot, lba
  2      496GB   986GB   490GB   extended
  5      496GB   982GB   486GB   logical   ext4
  6      982GB   986GB   4192MB  logical   linux-swap(v1)
  3      986GB   1000GB  14.5GB  primary   fat32           lba
 
 
 
 
 Model: Verbatim STORE N GO (scsi)
 Disk /dev/sdb: 15.6GB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags:  

 
 
 Number  Start   End     Size    Type     File system  Flags
  1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba
 
```




```
   Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes

 I/O size (minimum/optimal): 4096 bytes / 4096 bytes

 
 
 
 
 Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0x2bfb4dc8
 
 
 Device     Boot      Start        End   Sectors   Size Id Type

 /dev/sda1  *          2048  967784881 967782834 461.5G  c W95 FAT32 (LBA)
 /dev/sda2        967786494 1925206015 957419522 456.5G  5 Extended
 /dev/sda3       1925206016 1953524079  28318064  13.5G  c W95 FAT32 (LBA)
 /dev/sda5        967786496 1917016063 949229568 452.6G 83 Linux
 /dev/sda6       1917018112 1925206015   8187904   3.9G 82 Linux swap / Solaris
 
 
 Partition 2 does not start on physical sector boundary.

 Partition table entries are not in disk order.
 
 
 
 
 
 
 
 
 Disk /dev/sdb: 14.6 GiB, 15640600576 bytes, 30548048 sectors
 Units: sectors of 1 * 512 = 512 bytes

 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x02b9d71a
 
 
 Device     Boot Start      End  Sectors  Size Id Type

 /dev/sdb1  *     2048 30548047 30546000 14.6G  c W95 FAT32 (LBA)

 
```





```
   

/dev/sda1: LABEL="FD_BETA9SR2" UUID="3873-1AF8" TYPE="vfat" PARTUUID="2bfb4dc8-01"
 /dev/sda3: UUID="B498-74ED" TYPE="vfat" PARTUUID="2bfb4dc8-03"

 /dev/sda5: UUID="e76ac860-e581-46e6-ab26-933e2b6cc202" TYPE="ext4" PARTUUID="2bfb4dc8-05"

 /dev/sdb1: LABEL="UBUNTU 16_0" UUID="1272-E8C8" TYPE="vfat" PARTUUID="02b9d71a-01"

 /dev/loop0: TYPE="squashfs"

 /dev/sda6: UUID="8fca17e0-decf-4a43-b073-2e96424e6fe8" TYPE="swap" PARTUUID="2bfb4dc8-06"
```

---

### Post by Bashing-om on 2017-08-17
igorsrb; Hello once again.

Boot to grub -> 'e' key for edit mode -> boot parameter screen.
Here arrow down to the line starting with linux and just before $vt_handoff add fsck.mode=force .
ctl+x to continue the boot process ( remove quiet splash if you want to see the boot messages) .
See:
[https://www.freedesktop.org/software/systemd/man/systemd](https://www.freedesktop.org/software/systemd/man/systemd)

This will check every filesystem you have on the machine.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
> **Bashing-om said:**
> igorsrb; Hello once again.

Boot to grub -> 'e' key for edit mode -> boot parameter screen.
Here arrow down to the line starting with linux and just before $vt_handoff add fsck.mode=force .
ctl+x to continue the boot process ( remove quiet splash if you want to see the boot messages) .
See:
[https://www.freedesktop.org/software/systemd/man/systemd](https://www.freedesktop.org/software/systemd/man/systemd)

This will check every filesystem you have on the machine.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


what exactly do you mean by $vt_handoff? the /casper/vmlinuz.efi?

the line reads

linux          /casper/vmlinuz.efi   file=/cdrom/preseed/ubuntu.seed boot=casper_quiet  \ splash ---

---

### Post by Bashing-om on 2017-08-17
igorsrb;

My referral is in regards to the actual installed system.
With the addition of fsck.mode=force as a boot parameter, the check runs before the file system is mounted .

[INDENT][INDENT]clear as mud ?
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
bear with me now and explain to me like I am a 5 year-old

so I add the fsck.mode=force before the linux line

```

set gfxpayload=keep
[COLOR=#ff0000]**fsck.mode=force**[/COLOR]
[COLOR=#000000]linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper_quiet \ splash ---
```[/COLOR]

---

### Post by Bashing-om on 2017-08-17
igorsrb; K;

In small steps . you are to boot the installed hard drive system to grub,
Now, if it is a EFI system as soon as the firmware screen clears, spam the escape key - there is but a 3 second window of opportunity for grub to see the escape key.
IF it is a legacy system then it is a shift key that grub recognizes . As soon as the bios screen clears depress and hold a shift key.

Advise when you are at the installed system's grub boot menu .

[INDENT][INDENT]longest journey, even
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
I booted to grub already, got to edit mode with the e key, found the line starting with linux. It's the next step I wasn't clear about.

Do I insert the code "fsck.mode=force" and where and what exactly is " [COLOR=#000000]$vt_handoff " is what I am not clear.

[/COLOR]

---

### Post by Bashing-om on 2017-08-17
igorsrb;

nope;
In the installed boot parameter's screen is the line similar:
> 
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff


[INDENT][INDENT]small steps
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
not in mine, this is all I got


set gfxpayload=keep
[COLOR=#000000]linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper_quiet \ splash ---
initrd /casper/initrd.lz[/COLOR]

---

### Post by Bashing-om on 2017-08-17
igorsrb;

That ^ is the live environment .

I say again you want to boot into the install on your hard drive .

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
okay, got it, 

so I type the "[COLOR=#000000]fsck.mode=force" as a separate line before the

linux /boot/vmlinuz-4.4.0-92-generic root=UUID=e76ac860-e\581-46e6/ab26-933e2b6cc202 ro quiet splash $vt_handoff

and then I boot it with ctrl-x or F10[/COLOR]

---

### Post by Bashing-om on 2017-08-17
Agoigorsrb; progress made :)

But, no - not on a separate line.
Make it so:
> 
linux /boot/vmlinuz-4.4.0-92-generic root=UUID=e76ac860-e\581-46e6/ab26-933e2b6cc202 ro quiet splash fsck.mode=force $vt_handoff

such that the term fsck.mode=force is inserted in the present line before $vt_handoff.

Now if you desire to see what the system is doing as it boots up , then delete the quiet splash terms .

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
got it, I'll try it without the quiet splash just to watch it do its thing

thanks for bearing with me

---

### Post by igorsrb on 2017-08-17
Inodes that were part of a corrupted orphan linked list found.

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
[ 5.385041] random: nonblocking pool is initalized
Fsck exited with a status code 4
done.
Failure: File system check of the root filesystem failed
The root filesystem on /dev/sda5 requires a manual fsck
[5.471021] hidraw: raw HDID events driver (C) Jiri Kosina
[5.478717] usbcore: registered new interface driver usbhid
[5.481547] usbhid: USB HID core driver

---

### Post by Bashing-om on 2017-08-17
igorsrb; YuK .

OK, we take the directive and run a more in depth check/repair.

Now we MUST boot up from the liveDVD(USB).

Once booted up from this live environment post back:
```

sudo parted -l

```
So that I know that the target for the file system check remains as "sda5 " .
Then I will provide the command to run the repair from this live environment.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
```

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  496GB   496GB   primary   fat32           boot, lba
 2      496GB   986GB   490GB   extended
 5      496GB   982GB   486GB   logical   ext4
 6      982GB   986GB   4192MB  logical   linux-swap(v1)
 3      986GB   1000GB  14.5GB  primary   fat32           lba


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba



```

---

### Post by Bashing-om on 2017-08-17
igorsrb; Great .

Target ID remains as "sda5"
Run from the liveDVD(USB):
```

sudo e2fsck -f -y -v /dev/sda5

```
Where fsck will try and auto fix the errors.

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by igorsrb on 2017-08-17
fixed a tonload of orphaned inodes, deleted one, I think it worked, thanks a million

---

### Post by Bashing-om on 2017-08-17
igorsrb; Great !

Fingers crossed.
Reboot into the install and see what you have now .

[INDENT][INDENT]could be all rosy
[/INDENT][/INDENT]

---

