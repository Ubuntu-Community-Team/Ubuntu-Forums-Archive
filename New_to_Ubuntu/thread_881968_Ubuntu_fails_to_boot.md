---
title: "Ubuntu fails to boot"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Kaspersky_ on 2008-08-06
Ubuntu fails to boot. GRUB is installed, and does load. I get up to the part where it shows the Ubuntu logo and the loader bounces back and forth. It just takes a really long time then it boots into BusyBox.

I'm partitioned like this:

```

Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        7352    49287420   83  Linux
/dev/sda3            7353        7474      979965   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

I'm booting from sda and the two linux partitions are ext3. sda1 is mounted on / and sda2 is mounted on /home. All the partitions are primary.

I have no idea why it won't boot.

---

### Post by Troll_the_Great on 2008-08-06
Have you tried booting in recovery mode?

---

### Post by halitech on 2008-08-06
can you boot into the live cd okay?

---

### Post by Kaspersky_ on 2008-08-06
I can boot into the live cd okay and I haven't tried booting in recovery mode.

---

### Post by bobnutfield on 2008-08-06
After grub starts loading the system, press ALT-F1 to bring a text screen up.  Note the messages when it stops loading.

---

### Post by Kaspersky_ on 2008-08-06
Exactly what does the GRUB look like?

Edit: I only have one operating system GRUB doesn't show up except the small message it shows when it is saying press esc. for something and it gives me 3 seconds.

---

### Post by Troll_the_Great on 2008-08-06
> **Kaspersky_ said:**
> Exactly what does the GRUB look like?

It should look like:

Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Memtest86

You could have other old kernel too.If you don't see Grub, hit ESC when the computer starts.
Cheers!

---

### Post by Kaspersky_ on 2008-08-06
When I used Alt + F1 during boot I get a bunch of repetitive error messages (or that's why I think):

```
ata2.00: status: { DRPY ERR }
ata2.00: error: { ICRC ABRT }
ata2.00: exception: Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
```

```
Buffer I/O error on device sda, logical block 0
```

```
ldm_validate_partition_table(): disk read failed
```

```
checkroot= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/ modules is /dev
ALERT! /dev/disk/by-uuid/31545ca2-99c7-4d49-a105
388394f16e4c does not exist. Dropping to shell.
```

---

### Post by bobnutfield on 2008-08-06
Does not look good, though someone else may correct me.  It looks like your hard disk may be failing.  Run the live cd, do not mount your hard drive, open a terminal and type:

> sudo fsck /dev/sda

If it is only a corrupt file system, this will tell you that, but you may have to reinstall.

---

### Post by Kaspersky_ on 2008-08-06
```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I don't care if I have to reinstall. I would just like to be able to boot Ubuntu without the live cd correctly and have the limitations of a live cd.

---

### Post by halitech on 2008-08-06
I agree with you Bob, I think we need to start planning a funeral for his poor drive :(

---

### Post by Kaspersky_ on 2008-08-06
That drive had Windows installed previously and it was booting up fine and dandy. I've never been able to boot Ubuntu unless it was with the live cd.

---

### Post by bobnutfield on 2008-08-06
> checkroot= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/ modules is /dev
ALERT! /dev/disk/by-uuid/31545ca2-99c7-4d49-a105
388394f16e4c does not exist. Dropping to shell.

This is the worrying part.  Your original install identified the disk by its UUID, and while looking for it during the boot, it cannot read it.  The bad superblock message will also be received in just that manner on any disk that cannot be read.  You might try running e2fsck as suggested in the out put or try re-installing.  I have had a similar experience which did in fact mean a failed hard drive, but I could be wrong.

---

### Post by halitech on 2008-08-06
not to say Linux is any better but I have a drive that windows absolutely refuses to install on (gives a message about S.MA.R.T failure) on boot but as soon as I get Ubuntu installed on it, message goes away and it works fine (still not trusting it with any important info though, crazy yes, stupid no ~L~ ) 

Still sounds like a bad drive to me followed by a bad install.

---

### Post by Kaspersky_ on 2008-08-06
I have done all that I needed to do for the install to work correctly, but still Ubuntu fails to boot. I think that the disk is the problem. It's a self burned disk, and the .iso is from the Ubuntu website. I'm going to try to get a legit live cd from a friend to see if that's the problem. I'm also going to download the .iso again and burn it at the slowest speed possible but I'm going to do an md5checksum on it before I burn it to a disk. I did do a 'check cd for defects' test and it came out clean.

---

### Post by bobnutfield on 2008-08-06
Well, I hope it works out for you.  If you did a media check on the cd you have, it is unlikely to be the problem, but, who knows, I have seen it happen.

---

### Post by Kaspersky_ on 2008-08-06
Does anyone have any other fixes that thay may propose so I don't have to go through a hefty amount of trouble to get a new disk.

---

### Post by Daveski on 2008-08-31
> **Kaspersky_ said:**
> Does anyone have any other fixes that thay may propose so I don't have to go through a hefty amount of trouble to get a new disk.

Are you able to access the drive while booted into the LiveCD?

Also you could try:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

If this does not work, try **all_generic_ide** instead of **noapic**

---

