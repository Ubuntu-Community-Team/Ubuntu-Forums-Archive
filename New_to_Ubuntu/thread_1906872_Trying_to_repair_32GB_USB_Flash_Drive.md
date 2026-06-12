---
title: "Trying to repair 32GB USB Flash Drive"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by auraithx on 2012-01-10
Hi all,

Spent the past hour or so trying to repair this drive. Here are results of all the commands I've found while searching google for a solution.

This is whats happening when I plug the USB in.
```
sudo tail -c 0 -f /var/log/syslog
```

```
Jan 10 09:37:15 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329217.968053] usb 2-6: new high speed USB device number 12 using ehci_hcd
Jan 10 09:37:15 mglasgow-HP-Compaq-dx7500-Microtower mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jan 10 09:37:15 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329218.103994] scsi16 : usb-storage 2-6:1.0
Jan 10 09:37:15 mglasgow-HP-Compaq-dx7500-Microtower mtp-probe: bus: 2, device: 12 was not an MTP device
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.105314] scsi 16:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 2
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.105395] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.108808] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.128161] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.128277] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.146742] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.146871] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.150014] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.150139] scsi: killing requests for dead queue
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.152976] sd 16:0:0:0: Attached scsi generic sg3 type 0
Jan 10 09:37:16 mglasgow-HP-Compaq-dx7500-Microtower kernel: [329219.154921] sd 16:0:0:0: [sdc] Attached SCSI removable disk
```

It's recongised in lsusb as 
```
Bus 002 Device 012: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
```

I can't see anything other than the drives I'm already aware about using 
```
sudo fdisk -l
```

But here are the results anyway incase I've overlooked something
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c30f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   621019135   310508544   83  Linux
/dev/sda2       621021182   625141759     2060289    5  Extended
/dev/sda5       621021184   625141759     2060288   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c635a24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1250261679   625129816    7  HPFS/NTFS/exFAT

```
It's also recognised in Disk Utility but I don't have many options (screenshot attached below)

When I try and format using any of the options I get this error message

```
Error creating partition table: helper exited with exit code 1: cannot open /dev/sdc: No medium found
```

Any help appreciated

---

### Post by lkraemer on 2012-01-11
auraithx,
You don't say why you are trying to repair the USB Flash Drive....
It appears to be a Windows Formatted USB Drive.  Did you format it
in Windows for use in Windows ONLY.  Typically all USB Flash Drives come
formatted as my 4G Centon Pro shown below, making them automount (usable) in *nix.  
> 
Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008136d

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1         492     3948512+   c  W95 FAT32 (LBA)**
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38)
larry@debian:~$


You could use Gparted to Delete the Partition (just make 100% sure you are on the correct /dev/sdx)
DOUBLE CHECK the SIZE, and Partitions...and remove the partition.  Then create another one and
format it to whatever format you require.  If you're using it for transfers to Windows from *nix,
and Vice Versa, you'll want something universal that Windows/*nix accepts. ie. FAT32
The easiest thing would be to format it in Windows, then try it in *nix. 

You can also use dd to wipe the USB Flash Drive.

REF:

[http://ubuntuforums.org/showthread.php?p=11576337#post11576337](http://ubuntuforums.org/showthread.php?p=11576337#post11576337)



LK

---

### Post by auraithx on 2012-01-11
Forgot to say the drive isn't recognised at all in Windows/MacOSX

Also it isn't recognised in gparted.

---

### Post by Mark Phelps on 2012-01-11
Good Luck on that.  I've gone through several different USB flash drives, including some memory cards, and when they go bad (and they always DO), I've been unable to fix ANY of them.

Have tried all the available Windows tools, and even Linux tools -- nothing seems to work.

Maybe you'll have better luck.

---

### Post by satanselbow on 2012-01-11
Is it a known good drive? I recently purchased a 16GB miniSD that was faulty from day one and had to send it back :(

If you have access to windows then the HP USB TOOL is still *often* effective for reviving seemingly dead USB sticks ;)

---

### Post by lkraemer on 2012-01-11
auraithx,
I'm wondering if you can use dd to zero the partition &/or drive,
since the USB Flash Drive shows it mounts?

What does this command show:
```

sudo blkid

```

Try un-mounting the drive with:
```

umount /dev/sdb*

```

TO ZERO out a USB Flash Drive:  **CAUTION!  MAKE SURE YOU HAVE THE CORRECT DRIVE**
```

sudo dd if=/dev/zero of=/dev/sdX bs=1M

```
Where X is substituted with your Drive.

TO ZERO out a USB Flash Drive Partition (#1):  **CAUTION!  MAKE SURE YOU HAVE THE CORRECT PARTITION**
```

sudo dd if=/dev/zero of=/dev/sdX1 bs=1M

```
Where X is substituted with your Partition.


REF:
[url]
http://robotbutler.org/article/36
[/url]

LK

---

### Post by auraithx on 2012-01-11
> **lkraemer said:**
> auraithx,
I'm wondering if you can use dd to zero the partition &/or drive,
since the USB Flash Drive shows it mounts?

What does this command show:
```

sudo blkid

```

TO ZERO out a USB Flash Drive:
```

sudo dd if=/dev/zero of=/dev/sdb

```

TO ZERO out a USB Flash Drive Partition (#1):
```

sudo dd if=/dev/zero of=/dev/sdb1

```

LK

```
mglasgow@mglasgow-HP-Compaq-dx7500-Microtower:~$ sudo blkid
/dev/sda1: UUID="4cf61bcc-7364-48ea-af6a-5507e335f274" TYPE="ext4" 
/dev/sda5: UUID="e17b1f5d-0eb8-4c29-b6b0-c6a0a196943a" TYPE="swap" 
/dev/sdb1: LABEL="TOSHIBA EXT" UUID="065E505E5E504917" TYPE="ntfs" 
```

To which I proceeded to to copy/paste your command (without thinking)

```
sudo dd if=/dev/zero of=/dev/sdb1

```

And wiped my 640GB hard drive filled with HD movies and TV shows. :(

---

### Post by wigout on 2012-01-11
Well that sucks.

The "ZERO" out option should have been surrounded by a warning- which a mod or the author of the post should now include.

You will not be able to recover that 640gb hd now- it is "zeroed" out.

That being said, if you know which device letter is assigned to your dead usb device and you are interested in reformatting it (removing all chance of recovering files from it) I see that zeroing out the drive in question is a last ditch effort to bring an errant drive back in line.

In your first example, your dead device was "/dev/sdc". To find out what letter your device is assigned, unplug it, then
ls /dev/sd*
plug it back in and
ls /dev/sd*
and the new device in the list will be your dead device.
[B]WARNING- This command zeros out / erases forever the contents of your drive- only use on a drive from which you do not hope to recover files
[/B]dd if=/dev/zero of=/dev/sdc bs=1M
[B]WARNING- This command zeros out / erases forever the contents of your drive- only use on a drive from which you do not hope to recover files
[/B]Then try to format the dead usb device using Disk Utility or whatever.

Good luck- I am having my own damned usb problems at the moment.

-wigout

---

### Post by Mark Phelps on 2012-01-11
> **wigout said:**
> Well that sucks.

The "ZERO" out option should have been surrounded by a warning- which a mod or the author of the post should now include.


Hey ... let's at least be FAIR to the person who suggested the Zero out option, OK?

The OP specifically entered the WRONG device name. They manually entered "sdb1" -- which clearly shows as their NTFS partition!  The command then simply did what it was told to do.

It wasn't the lack of a "warning" that caused the damage; it was a mistake on the part of the person entering the command.

---

### Post by lkraemer on 2012-01-11
auraithx,
MAN, I'M SORRY!  I can see why that happened.  I've changed my post accordingly.

LK

---

### Post by jmate24 on 2012-01-11
you should have also run this below before you zeroed out the drive:

```
lsusb
```

and found if it was connecting.

also some drives have special software that may not make them usable unless you install it or use it to format the drive.

and where did you by this drive? was it newegg, tigerdirect, at the store, or somewhere else?

---

