---
title: "Not booting/detecting hdd"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by micromidgetmonkey on 2013-01-03
For starters please forgive my total lack of knowledge, not only of ubuntu but of computers in general. I recently replaced the corrupted drive in my pc with a sata 3 Toshiba and decided to give mint a whirl (relevant bear with me). I was trying to boot from a flash drive and it would very rarely work, maybe one time in ten. even when it did it wouldn't detect the new hdd. Got annoyed with this eventually and returned to Ubuntu. Worked fine the first time, detected drive and everything, returning to it this morning however and has started throwing up the same issues, although it is more likely to boot than mint the boot media is often not detected and the hdd has now stopped coming up at all. I've trawled the internet and found numerous similar issues but no that quite conform to this. Any help and advice you might be able to give would be greatly appreciated.

---

### Post by TheFu on 2013-01-03
A few things are not perfectly clear.
* Are you trying to boot from a flash drive?
* Are you trying to boot from a spinning hard drive that is internally connected with a SATA cable?
* Are you trying to boot from a USB2 external spinning hard drive?

1 problem at a time, please.

Next, providing some log files would be helpful. These are usually found in the /var/log/ directory with names like "boot.log" and "messages" and "syslog" - basically, if it is part of the operating system and it logs anything, it will be in a file under /var/log/ .... somewhere.  Applications may or may not log there since end-users don't have permissions to write to files there. Apps might log to /tmp or  into an application specific log/ directory somewhere under your HOME/.

If you cannot boot from either flash or HDD, how do you install the OS?  Use that same DVD/CD and boot it again.  Look to see if your HDD(s) are seen by that OS.  You want something like /dev/sda or sdb or hda or hdc ..... all in the /dev/ directory. Again, this will be in the log files.  If you don't find that, then the HDD isn't being seen by the OS and you probably have a hardware issue - motherboard, disk controller, sata cable ... probably.

OTOH, there may be a fairly easy fix to all this.  Run **boot-repair** on the system. You may need to install it. It will try to fix the most common issues for booting Windows and Linux systems and it should setup a grub boot menu with reasonable settings.  I don't know if it works for WUBI installs, but it definitely works for partition installations. I used it about 10 times 2 weeks ago when swapping a new HDD at Mom's place.

Try the boot-repair first. If that doesn't solve it, start looking inside log files for the specific issue and posting **relevant parts** here. We don't want/or need to see entire log files.

---

### Post by micromidgetmonkey on 2013-01-03
Thanks for the response, sorry I wasn't clearer. I'm running ubuntu from a 4 gig stick, the hdd is internal, connected by sata cables, and brand new, straight out of the box to the machine. My confusion is initially from the fact that booting from the stick is so hit and miss, it seems to be fifty fifty whether the computer realises there's anything to boot from, though when it does it works fine. Running boot-repair now here's hoping...

---

### Post by micromidgetmonkey on 2013-01-03
Update,
Boot repair appears to be doing nothing beyond 'scanning systems', similarly gparted refuses to go beyond 'scanning all devices', and I don't apear to have permission to view the log files, most perplexing.

---

### Post by TheFu on 2013-01-03
> **micromidgetmonkey said:**
> Update,
Boot repair appears to be doing nothing beyond 'scanning systems', similarly gparted refuses to go beyond 'scanning all devices', and I don't apear to have permission to view the log files, most perplexing.


Try 
$ **sudo boot-repair**

Always remember that Linux is a multi-user OS and expects most end-users to be just that - end-users.  When you are doing administrative things, you need to ask for elevated permissions. That is what **sudo **does, provided your account has permissions to do that.  Most accounts on a Linux system do not get **sudo **access.

---

### Post by TheFu on 2013-01-03
> **micromidgetmonkey said:**
> Thanks for the response, sorry I wasn't clearer. I'm running ubuntu from a 4 gig stick, the hdd is internal, connected by sata cables, and brand new, straight out of the box to the machine. My confusion is initially from the fact that booting from the stick is so hit and miss, it seems to be fifty fifty whether the computer realises there's anything to boot from, though when it does it works fine. Running boot-repair now here's hoping...

Ok - that helps me to understand better.  You have to tell the BIOS where to boot from.  
b) There must be a partition on the HDD that is marked as "bootable", use gparted or parted to create partitions.  
c) If the HDD is over 1.5TB and you never plan to install WinXP, you probably want to use the newer partitioning method - GPT - instead of the older, less flexible type, MBR.  GPT has too many pluses when compared to all the MBR minuses. It really is better, just be aware that you need to use parted and gparted to manage partitions on GPT HDDs, not fdisk.  If you run 12.04 and later, this happens automatically unless you type in "fdisk" yourself. These tools also handle 4K-sector disks the way you want for best performance.

For example, here is how I've partitioned my XBMC Ubuntu box.
```
$ sudo parted -l
Model: ATA ST3300620AS (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  20.0GB  20.0GB  primary   ext4            boot
 2      20.0GB  300GB   280GB   extended
 5      20.0GB  230GB   210GB   logical   ext4
 6      230GB   251GB   21.0GB  logical   ext4
 7      251GB   272GB   21.0GB  logical   ext4
 8      298GB   300GB   2096MB  logical   linux-swap(v1)

```
This HDD uses the MBR partition format as shown by the "msdos". It is only a 300G HDD. Linux can boot from either a primary or logical partition, Windows used to only boot from primary, but can read data, programs, etc from logical partitions just fine.  
Part-1 = Linux OS and Apps (no data)
Part-2 = Extended partition that holds all the remaining logical partitions
Part-5 = /home ... note how it is larger?
Part-6 = Spare partition for another Linux OS and Apps
Part-7 = Spare partition for another Linux OS and Apps
Part-8 = Swap, shared by all Linuxen when booted

If I wanted MS-Windows7, I'd probably make a 30G or 60G primary partition to load into, then I'd have a data partition formatted as NTFS that would be shared between Windows AND Linux OSes since Windows can't read-write to ext4 or most other Linux file systems.

As you can see, I was willing to "waste" about 40G to have different play areas for versions of Linux to try out.  If your HDD is large, this is highly, highly recommended. At least 1 spare is a good idea.

Also, running any Linux from a USB stick is hard on the USB memory. It will cause it to die much quicker due to all the writes. Flash memory loves to be read, but dislikes being written. That wears it out.

I hope you remembered to use **sudo boot-repair** and that it worked for your needs.

---

### Post by micromidgetmonkey on 2013-01-03
Unfortunately GParted refuses to progress pass the 'scanning all devices' stage and all other options are blacked out and boot repair is still encountering the same issues even when entered in the terminal as **sudo boot-repair** . Other problems I've encountered; The bios boot priority only reliably recognises the usb 2.0 readers, seems hit and miss wether it recognises internal drives, disc drives and the flash drive I'm trying to boot from. Additionally when it does spring into life (from the flash drive) there's a Floppy disk option under devices in the home menu but nothing else, confusing as the machine does not boast a floppy drive...
Finally even with sudo I can't access the logs for some reason.

Considering installing the hdd in another pc and checking it for issues before installing ubuntu and putting it back, or just running the whole shebang from an external drive.

---

### Post by TheFu on 2013-01-03
All these issues tells me
* look for a newer BIOS for your MB.
* Are you using on-board SATA or an add-on card?  

Or some hardware may be failing. Could be almost anything, including the graphics card, power supply, mother board, RAM, SATA controller, or even the new HDD.  Try as many components in other computers as you can to eliminate them as concerns.

I'm confused about not being able to read the log files. Is there an error?  
Do you clearly understand what I'm suggesting?

A command like:
$ sudo more /var/log/syslog
is necessary.

I try to "burn-in" new HDDs for a few weeks using **dban** for 24/7 workloads before any real use happens.

Finally, if you are in a non-GUI environment, I don't know how **boot-repair** will work, if it works at all. I've only used it on GUI installations.

Not being able to review log files using sudo is something that I've never seen on a running Linux system.  Did you encrypt the entire OS by any chance?

---

