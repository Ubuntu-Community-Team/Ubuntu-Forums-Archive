---
title: "Unable to boot Ubuntu 14.04 after repartition"
date: 2016-04-07
forum: New to Ubuntu
---

### Post by flinner on 2016-04-07
Hi there,

I recently removed Windows XP from a laptop, which has Ubuntu 14.04 installed. I repartitioned to make use of the unallocated space and have since failed to boot. Getting a "Non-system disk or disk error" message.

I tried the procedure on Gparted [here]("http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem") and then Boot Repair with no success. The log file from Boot Repair can be viewed here:

[paste.ubuntu.com/15665946/]("http://paste.ubuntu.com/15665946/")

Would greatly appreciate any pointers to a solution.

Cormac

---

### Post by yancek on 2016-04-07
The link to the GParted instructions is broken.  Did you remove the media from the CD/DVD drive and change the boot order in the BIOS?

---

### Post by Dragonbite on 2016-04-07
Make sure the partition is bootable.

If you use a LiveUSB (or disk) and look at the partition in gparted there is an option for adding a flag to the partition and one of those choices is a boot flag.

I had that issue with a different distribution that the installation process never set the boot flag automatically, so I would have to do it manually.

I'm sorry I cannot be more precise in the steps to checking it, or of the 'fdisk' commands but I'm at work and not in front of a Linux desktop.

---

### Post by ajgreeny on 2016-04-07
Linux and Ubuntu do not normally needf a boot flag in order to boot the system, but you could certainly add one to the root partition just to make sure.

Have you reset the BIOS of the machine to boot with the hard drive as first priority device since reinstalling the OS?  That could easily give the error you see when trying to boot.

---

### Post by Bucky Ball on 2016-04-07
Yes, it all looks okay in your bootinfo, unless I've missed something. Check the BIOS to make sure that is set for the hard drive.

Did you actually run Boot Repair recommended repair? This is what it would do:

> The default repair of the Boot-Repair utility will reinstall the grub2 of sda5 into the MBR of sda.
The boot flag will be placed on sda5.

So you could try:

```
sudo grub-install /dev/sda
sudo update-grub
```

Reboot your machine and check you are booting from the hard drive in the BIOS.

---

### Post by kansasnoob on 2016-04-07
The boot info summary has two bits of info pointing to the same problem:

```
=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95aa95aa

Device Boot      Start         End      Blocks   Id  System
/dev/sda3            2048   486287359   243142656    5  Extended
/dev/sda5            4096   480139263   240067584   83  Linux
/dev/sda6       480141312   486287359     3073024   82  Linux swap / Solaris


**[COLOR="#FF0000"]Partition outside the disk detected[/COLOR]**.
```

```
[B][COLOR="#FF0000"]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently[/COLOR][/B].

```

FixParts should be able to fix that. Jump to the second part:

> It can repair mis-sized extended partitions. These partitions normally serve as placeholders for logical partitions, but some partitioning tools miscompute the size of the extended partition, which can cause problems. FixParts is designed in such a way that this type of repair occurs automatically, so if it's the only problem with your disk, you can launch the program and then immediately save the partition table (as described in the upcoming section Saving Your Changes), making no manual changes, and the program will fix the problem. 

But I'm hardly proficient using FixParts. I've used it a few times but always have to muddle thru the tutorial:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Please ask questions if need be before proceeding! In spite of being "new" to Ubuntu I'd post a question about using FixParts in the installation & upgrades section because a lot of those folks use tools like that every day.

Also, it's quite likely that you'll need to run boot repair again after FixParts is done fixing that partition error.

---

### Post by flinner on 2016-04-07
Thanks for all the responses. Will get back with an update tonight.

Cormac

---

### Post by flinner on 2016-04-09
Hi all,

I didn't reset the BIOS and I did run Boot-repair Recommended Repair.

I ran FixParts and got the following message at the start:
"FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes."

I printed the MBR partition table and got the following:
"** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 488397168 sectors (232.9 GiB)
MBR disk identifier: 0x95AA95AA
MBR partitions:
[TABLE="width: 500"]
[TR]
[TD]Number[/TD]
[TD]Boot
[/TD]
[TD]Start sector
[/TD]
[TD]End sector
[/TD]
[TD]Status
[/TD]
[TD]Can be logical
[/TD]
[TD]Can be primary
[/TD]
[TD]Code
[/TD]
[/TR]
[TR]
[TD]5
[/TD]
[TD]*
[/TD]
[TD]4096
[/TD]
[TD]480139263
[/TD]
[TD]  logical[/TD]
[TD]y
[/TD]
[TD]y
[/TD]
[TD]0x83
[/TD]
[/TR]
[TR]
[TD]6
[/TD]
[TD][/TD]
[TD]480141312
[/TD]
[TD]486287359[/TD]
[TD]  logical[/TD]
[TD]y
[/TD]
[TD]y
[/TD]
[TD]0x82
[/TD]
[/TR]
[/TABLE]

Any insights are welcome.

I then ran boot-repair as recommended and get similar errors as before about a partition outside the disk detected. Details in here:
[http://paste.ubuntu.com/15706042/](http://paste.ubuntu.com/15706042/)

When running GParted now, I get a Libparted Bug Found:
"Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting."

sda1 is the extended partition and has an lba flag - presumably added by the FixParts app?

Is the latter an additional thing to worry about?

Cormac

---

### Post by flinner on 2016-04-09
So I read in the [FixParts revision page]("http://www.rodsbooks.com/gdisk/revisions.html") that there was a bug in version 0.8.8 in relation to the message "Warning: 0xEE partition doesn't start on sector 1. This can cause problems in some OSes"

I updated FixParts to the latest and the above message went away.

If I eject the Live CD before running Boot-repair I get no errors regarding partitions outside the disk.

The boot order in the BIOS is:
Notebook Upgrade Bay
Notebook Hard Drive
USB floppy
USB CD-ROM

Cormac

---

### Post by yancek on 2016-04-09
> I repartitioned to make use of the unallocated space and have since failed to boot

What exactly did you do?  Looking at your fdisk output in boot repair you can see your Extended partition starts at sector 2048 and the Ubuntu system partition starts at 4096. Your xp would have been at the beginning of the disk and 2048 sectors isn't enough for your boot files much less the entire xp.  That would indicate that you moved the Ubuntu system partition to the left toward the beginning of the drive and your boot files aren't where they previously were.  You might be able to use a Live CD to chroot and update grub but I'm not sure that will work.  You could have saved yourself a lot of grief by simply deleting the xp partition(s) and creating a new data partition for Ubuntu. 

I don't know what "Notebook Upgrade Bay" is on your computer but it would seem that  "Notebook Hard Drive" ought to be first in boot priority?

---

