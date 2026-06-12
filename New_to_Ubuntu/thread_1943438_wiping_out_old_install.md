---
title: "wiping out old install"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-19
I've been playing with 11.10 for awhile, and recently hit a problem (posted in another thread) that has me considering a re-installation. I might choose 10.04 this time.

My question is, how do I go about clearing the old system from my drive? The drive is partitioned for Windows 7 as well, so I can't clobber the entire thing. How can I remove all vestiges of ubuntu before re-installing?

Thanks.

---

### Post by sudodus on 2012-03-19
How was your Ubuntu system installed? Was all of it sitting in one partition, the root partition **/** ? Or did you also have a /home partition or a /boot partition?

If you have only / , you can simply install the new version of Ubuntu onto that partition using the 'manual' method to select/edit partitions. This way the old system will be wiped.

Check what it looks like with the following commands
```
sudo fdisk -lu
```
```
df
```
and post the output of the commands if you want help to interpret it.

If your Ubuntu uses several partitions, it is better to reformat those file systems with gparted (from a live CD or USB drive, for example the Ubuntu install CD/USB drive).

---

### Post by Vaphell on 2012-03-19
during installation pick manual partitioning and simply reuse your old linux partition(s) to install new system. Don't touch anything labeled ntfs and everything should be peachy.

---

### Post by mzimmers on 2012-03-19
> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b4abd76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   122879999    61336576    7  HPFS/NTFS/exFAT
/dev/sda3       122882046   250068991    63593473    5  Extended
/dev/sda5       233869312   250068991     8099840   82  Linux swap / Solaris
/dev/sda6       217665536   233859071     8096768   82  Linux swap / Solaris
/dev/sda7       122882048   201459711    39288832   83  Linux
/dev/sda8       201461760   217663487     8100864   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                   3955868     73828   3882040   2% /
udev                   3947556         4   3947552   1% /dev
tmpfs                  1582348       840   1581508   1% /run
/dev/sr0                714028    714028         0 100% /cdrom
/dev/loop0              678784    678784         0 100% /rofs
tmpfs                  3955868         8   3955860   1% /tmp
none                      5120         4      5116   1% /run/lock
none                   3955868       104   3955764   1% /run/shm
ubuntu@ubuntu:~$ 


Thanks for the help.

---

### Post by sudodus on 2012-03-19
```
Disk /dev/sda: 128.0 GB, 128035676160 bytes
 255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x3b4abd76
 
 Device Boot Start End Blocks Id System
 /dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
 /dev/sda2 206848 122879999 61336576 7 HPFS/NTFS/exFAT
 /dev/sda3 122882046 250068991 63593473 5 Extended
 /dev/sda5 233869312 250068991 8099840 82 Linux swap / Solaris
 /dev/sda6 217665536 233859071 8096768 82 Linux swap / Solaris
 /dev/sda7 122882048 201459711 39288832 83 Linux
 /dev/sda8 201461760 217663487 8100864 82 Linux swap / Solaris
 
 Partition table entries are not in disk order
 ubuntu@ubuntu:~$ df
 Filesystem 1K-blocks Used Available Use% Mounted on
 /cow 3955868 73828 3882040 2% /
 udev 3947556 4 3947552 1% /dev
 tmpfs 1582348 840 1581508 1% /run
 /dev/sr0 714028 714028 0 100% /cdrom
 /dev/loop0 678784 678784 0 100% /rofs
 tmpfs 3955868 8 3955860 1% /tmp
 none 5120 4 5116 1% /run/lock
 none 3955868 104 3955764 1% /run/shm
```
OK, you are booting from the live disk, so df doesn't tell, what partitions are (were?) used by the old installed system. But we have valuable info from fdisk:

The whole extended partition is dedicated to linux. And you have three swap areas, which is a waste of space. I suggest that you

1. ***Backup*** at your internal drive to an external drive or at least backup all your private data (from Windows as well as from Ubuntu). Editing partitions is risky...

2. Run ***gparted*** from your live session, and delete partitions inside your extended partition: sda6,sda7,sda8 leaving only sda5 (the swap partition at the end of the drive).

3. Make an ext4 partition of all the free space in the extended partition. This partition should then be mounted as the root file system **/** during installation, with the manual method (I think it is called manual in Ubuntu 10.04, in 11.10 it is called 'something else').

---

### Post by mzimmers on 2012-03-19
I had to boot from liveCD: I can't log into my account when booted from the hard drive. That's a big part of why I'm going to re-install.

I don't have anything worth preserving on ubuntu, and I don't (yet) have a backup disk, so I may have to take the risk of skipping step 1.

So, I have a liveCD for both 11.10 and 10.04; should I do this from 10.04 if that's the version I'm likely to change to?

Thanks.

---

### Post by sudodus on 2012-03-19
> **mzimmers said:**
> I had to boot from liveCD: I can't log into my account when booted from the hard drive. That's a big part of why I'm going to re-install.

I don't have anything worth preserving on ubuntu, and I don't (yet) have a backup disk, so I may have to take the risk of skipping step 1.

So, I have a liveCD for both 11.10 and 10.04; should I do this from 10.04 if that's the version I'm likely to change to?

Thanks.
Yes, that is a good version (I'm using it on my main computer)

---

### Post by ajgreeny on 2012-03-19
Not only do you have 3 swap partitions, but they are large by normal standards at what appears to be 8GB each.  The old idea of making swap 1.5x the size of ram installed is no longer true and a maximum of 4 GB is plenty for just about every situation.

This time when you reinstall I suggest you delete sda5 sda6 sda7 and sda8 leaving the single extended partition sda3 just as you have at the moment, about 60GB. In that you should put a swap of 4GB, root of about 10GB and leave the rest as /home.  See [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") for more information on this.  Just note that when the guide talks of manual partitioning, or however it is described, the installer of 11.04 and 11.10 now calls it "Something else"

---

### Post by mzimmers on 2012-03-19
I just deleted those three partitions, now at boot time, I get put into some command-line utility called "grub." It doesn't have a help or anything; I just hit restart and put a CD back in. Of course, this means I can't get into Windows 7, as I've lost my OS chooser, so it'd be good if I could get this fixed ASAP.

EDIT: I found the boot-repair utility, and ran it. Now it just drops me into Windows 7. The advanced options don't give me the choice of choosing a different OS, so I think I somehow managed to wipe out ubuntu. I tried booting from the 10.04 disk, and it gave me some weird error (screen flashing too quickly to read), so...I guess I'm going back to 11.10. 

More as it happens...

---

### Post by mzimmers on 2012-03-19
OK, I've reinstalled 11.10. Somehow, I still ended up with two of those swap partitions:

> Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b4abd76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   122879999    61336576    7  HPFS/NTFS/exFAT
/dev/sda3       122882046   250068991    63593473    5  Extended
/dev/sda5       233867264   250068991     8100864   82  Linux swap / Solaris
/dev/sda6       122882048   217661439    47389696   83  Linux
/dev/sda7       217663488   233859071     8097792   82  Linux swap / Solaris

Partition table entries are not in disk order


So...can I delete one? How do I know which, or does it matter?

What are these used for, anyway?

---

### Post by sudodus on 2012-03-20
> **mzimmers said:**
> OK, I've reinstalled 11.10. Somehow, I still ended up with two of those swap partitions:



So...can I delete one? How do I know which, or does it matter?

What are these used for, anyway?

At this stage, right after installation, it is probably easier to wipe all logical partitions inside the extended partition (not leaving one swap partition, because you create one, the way you install Ubuntu).

Try to leave the space inside the extended partition unused (no logical partition) and then reinstall Ubuntu 11.10 again. This time, let the installer program select this unused (empty) space and make the root partition and swap partition automatically.
     -o-
A swap partition is a place to write data which no longer fits in the RAM, because a new program or process needs to put some current data there. Later on, the swapped data can be re-entered into the RAM. It is also called virtual memory, and corresponds to a big file in Windows.

---

### Post by mzimmers on 2012-03-20
Thanks for the information. Can I recover that space without reinstalling? Or...is there an installation option that overlays my current system files, but leaves apps and other stuff as is?

---

### Post by sudodus on 2012-03-20
> **mzimmers said:**
> Thanks for the information. Can I recover that space without reinstalling? Or...is there an installation option that overlays my current system files, but leaves apps and other stuff as is?
Yes, you can, but I think it is not faster than a reinstall, but it might be more convenient.

Boot from a live session from your Ubuntu install drive again, and use gparted to delete the new swap partition, ***/dev/sda7***. Then expand the linux partition, ***/dev/sda6***, into that space (still using gparted). I think you can do it graphically by pulling the boundary with the mouse. Otherwise you can use the menu system.

Then click the green tick icon to start the actions. The grow-partition-size operation might be slow and a bit risky, but it usually works without problems.

---

### Post by mzimmers on 2012-03-21
Well, that was about as easy as can be. Someone mentioned that the 7.73 GiB I have in my /sda5 swap space is excessive. Do you agree, and if so, can I resize that and grab the space in the same way?

Thanks.

---

### Post by sudodus on 2012-03-21
> **mzimmers said:**
> Well, that was about as easy as can be. Someone mentioned that the 7.73 GiB I have in my /sda5 swap space is excessive. Do you agree, and if so, can I resize that and grab the space in the same way?

Thanks.

How big is your RAM? Do you intend to hibernate your computer (instead of shutdown)?

If you want to hibernate, you should have at least as much swap as RAM. Otherwise you can have less, even zero particularly if you do not plan to run any memory-hungry programs, and if you are good at shutting down programs, that you are not running actively (instead of leaving them on, occupying memory).

---

### Post by mzimmers on 2012-03-21
8 GB of RAM, and this is a desktop, so no need for hibernating, right? Can I really delete that partition entirely? I generally don't have a lot of stuff open at once.

---

### Post by sudodus on 2012-03-21
> **mzimmers said:**
> 8 GB of RAM, and this is a desktop, so no need for hibernating, right? Can I really delete that partition entirely? I generally don't have a lot of stuff open at once.
With 8 GB of RAM, yes, you can. If you start getting problems, you can edit your partitions again to create space for a small swap partition, but I don't think you need it.

I think that you can test running without swap by commenting out the line in /etc/fstab specifying how to mount the swap partition. Put a # character at the beginning of that line and save it. After reboot you should run without swap (check with the system monitor).
```
sudo nano /etc/fstab
```

---

