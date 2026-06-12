---
title: "Interrupted the mkfs"
date: 2017-09-09
forum: New to Ubuntu
---

### Post by sed_faster on 2017-09-09
HEllo folks,

When a was do:
[quote]
sudo mkfs -c -t ext4 /dev/sdc1
(quote]
I interrupted the program through ctrl-C. I need formatted the system, but never the system start god health. When I started the system I have this screen: [https://imgur.com/a/1CRCO](https://imgur.com/a/1CRCO)

How can I resolve this?

Thanks, sorry about my English

---

### Post by SeijiSensei on 2017-09-09
First, install the package **smartmontools** if you haven't yet done so, then run

```
sudo smartctl -a /dev/sdc
```

to get a report on the health of the drive.  If it's not failing, then rerun mkfs with the test for badblocks enabled ("-c") as you did before.  This could easily take a day so you must be patient.

---

### Post by sed_faster on 2017-09-09
Thanks,
I ran the sudo mkfs -c -t ext4 /dev/sdc1 and the system yet still formatted the disk (1TB). Later I will give more feedback

---

### Post by sed_faster on 2017-09-09
I can't see the disk through sudo fdisk -l 
How can I search disc?
thanks

---

### Post by sed_faster on 2017-09-09
The BIOS can't see the disk :( Maybe I burned the disk when I interrupted the first process mkfs through ctrl-c. This is possible?

I interrupted the process, through ctrl-c when on terminal I has this prompt:
```

$ sudo mkfs -c -t ext4 /dev/sdc1
mke2fs 1.42.13 (17-May-2015)
Creating filesystem with 244190390 4k blocks and 61054976 inodes
Filesystem UUID: 436a8ae0-5df6-459f-a090-5faec728049e
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848

```

---

### Post by SeijiSensei on 2017-09-10
If you interrupted the process while it was writing superblocks, fsck didn't get to finalize the filesystem.

Still that doesn't explain why the drive is not seen by the BIOS.  What did smartctl say?  From the earlier output and these symptoms, I don't think this device has long to live.

---

### Post by sed_faster on 2017-09-14
I buy another disk and after run
```

sudo mkfs -t ext4 /dev/sdc1

```

and reboot the system this script appear on a screen: [https://imgur.com/a/1CRCO](https://imgur.com/a/1CRCO)

I can login in system because the system was on this loop! What this is means?

---

### Post by SeijiSensei on 2017-09-14
Is /dev/sdc1 mount through /etc/fstab?  If so, comment out that line and reboot.  Still get the same error?

It looks to me like the problem is on the primary drive not on the external one.

---

### Post by sed_faster on 2017-09-14
The fstab don't have comment to this device!

> 
It looks to me like the problem is on the primary drive not on the external one.
I don't understand this phrase. Can you explain another way, please?
thanks

---

### Post by SeijiSensei on 2017-09-14
The device you formatted is an external drive, correct?  If you don't connect the device, do the errors persist?

I think the errors might be on the drive that contains Ubuntu and the boot sector, not the external device.

---

### Post by sed_faster on 2017-09-14
No, this disk is connected by SATA cable.
If you turn the disk off, the system switches on normally.

This pc has 3 disks. The ubuntu server is on an 80GB disk connected via IDE cable. The rest are by the sata cable.

It  turns out that after creating the partition with fdisk and formatting  with mkfs and rebooting the system gets stuck on that screen with that  message. After about 5 minutes the system switches on.

I can mount the partition but when I try to make a mkdir folder, the system crashes with this message: [https://snag.gy/EG7Bpa.jpg](https://snag.gy/EG7Bpa.jpg)

How can I resolve this problem?
thanks

---

### Post by sed_faster on 2017-09-14
I am do right things when I create the partition and format with type ext4t?

---

### Post by SeijiSensei on 2017-09-14
"Status DRDY" usually means the drive has physical problems.

I'll mention that the earlier output listed ata4 as the problematic device.  Here it's ata3. That could just result from the order in which the devices were attached.

You didn't use the "-c" switch this time around. I wouldn't have done so either with a new drive. Your might try formatting the device again with the bad blocks testing enabled.

---

