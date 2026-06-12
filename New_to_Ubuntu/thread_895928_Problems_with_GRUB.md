---
title: "Problems with GRUB"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by know-it-some on 2008-08-20
In order to avoid using LILO on a new ubuntu server I need help troubleshooting why GRUB will not install.  When the server just had four separate SAS drives the GRUB boot loader would install just fine.  Unfortunately, once all of these drives were united by an Adaptec SCSI RAID card, and an arrary created, GRUB would no longer install at the end of the installation process.  

LILO does install but then boots to a screen with something like: LILO 99 99 99 99 99 99 99 ... so on and so forth and then halts. I'd love to get GRUB on there if possible.  Does anyone feel like assisting me? Thanks.

---

### Post by caljohnsmith on 2008-08-20
> **know-it-some said:**
> Unfortunately, once all of these drives were united by an Adaptec SCSI RAID card, and an arrary created, GRUB would no longer install at the end of the installation process.  

Can you give some more details about Grub not installing? What errors do you get if any?

---

### Post by know-it-some on 2008-08-20
Excellent, here are some more details:  The specific error I get is this:

[!!] Configuring grub
Unable to install GRUB in /dev/sda
Executing 'grub-install /dev/sda' failed.

This is a fatal error.
<Go Back>    <Continue>

When I hit continue, I am given the information that an installation step failed, and that the step in question is: Install the GRUB boot loader on a hard disk.

---

### Post by caljohnsmith on 2008-08-20
I'm not particularly experienced with RAID setups, but I have lots of experience troubleshooting Grub problems. So until someone happens along who has alot of both RAID and Grub experience, I think we have a good chance of figuring out a solution to your problem. :)

You say:
> GRUB would no longer install at the end of the installation process.
Does that mean you are reinstalling your entire server software, and trying to install Grub at the end of the installation? If so, you could skip the Grub installation and do it manually afterwards, since installing manually might have a higher chance of success.

To give me a better idea of your setup, please post the output of:
```
sudo fdisk -lu
```
And please give me details of where you want your /grub or /boot/grub directory, and also which HDD MBR (master boot record) you are trying to install Grub to.

---

### Post by know-it-some on 2008-08-20
> **caljohnsmith said:**
> I'm not particularly experienced with RAID setups, but I have lots of experience troubleshooting Grub problems. So until someone happens along who has alot of both RAID and Grub experience, I think we have a good chance of figuring out a solution to your problem. :)

Awesome, thanks for the help!

> 
Does that mean you are reinstalling your entire server software, and trying to install Grub at the end of the installation?

Yep.  The GRUB install seems to be assumed, and is automatically tagged on at the end of a regular ubuntu server installation.  This is when it fails, and when you hit continue, you are offered the chance to install LILO, install GRUB again, or skip it altogether.  I usually end up choosing lilo so I can at least boot into the OS, but I much prefer GRUB.

>  If so, you could skip the Grub installation and do it manually afterwards, since installing manually might have a higher chance of success.

I am willing to give that a try but I am not sure how to go about it.

> To give me a better idea of your setup, please post the output of:
```
sudo fdisk -lu
```

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2997.8 GB, 2997876686848 bytes
255 heads, 63 sectors/track, 364471 cylinders, total 5855227904 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cd75842

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1  4294967295  2147483647+  ee  EFI GPT
```

> And please give me details of where you want your /grub or /boot/grub directory, and also which HDD MBR (master boot record) you are trying to install Grub to.

I am open to suggestions.  I do not have a strong preference and I probably do not have enough experience to really say where I want it.  But I would think /boot/grub would be best since it is logically grouped with booting related files, and as far as the HDD MBR, there is one HD detected and that is the /dev/sda which is really a RAID0 array. This array is comprised of four disks attached to the aforementioned ASR2405 Adaptec RAID card.

---

### Post by caljohnsmith on 2008-08-20
OK, your fdisk output shows one HDD (your RAID array), but it only shows one partition sda1. From the error it gave:
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

It looks like fdisk doesn't know how to correctly handle your RAID setup, because I would assume you have more than one partition, correct? If so, what is your partitioning structure? And what command(s) do you use to see your partitions and/or mount them?

If you were to boot a Ubuntu Live CD, do you know how to mount any of your RAID partitions? Or access your RAID drive at all? Like I said I'm not particularly experienced with RAID, so we'll need to figure out some of the RAID stuff together before I can give you instructions of how you might manually install Grub.

---

### Post by know-it-some on 2008-08-20
> **caljohnsmith said:**
> OK, your fdisk output shows one HDD (your RAID array), but it only shows one partition sda1. From the error it gave:

It looks like fdisk doesn't know how to correctly handle your RAID setup, because I would assume you have more than one partition, correct? 

This is what I can tell you about my partitioning setup.  During install, when I select 'Guided: Use entire disk', the only disk available to select is: "SCSI1 (0,0,0) (sda) - 3.0TB Adaptec AR1".  I select it, of course, and then:

```

The following partitions are going to be formatted:
  partition #1 of SCSI1 (0,0,0) (sda) as ext3
  partition #2 of SCSI1 (0,0,0) (sda) as swap

```

> If so, what is your partitioning structure? And what command(s) do you use to see your partitions and/or mount them?

I have not needed to see the partition or mount it as it is mounted automatically when I boot into the OS.  I only have one data partition and the second partition is swap.

> If you were to boot a Ubuntu Live CD, do you know how to mount any of your RAID partitions?Or access your RAID drive at all? 

I would assume by creating a directory within mnt and mounting them as I would any other storage device. something like:

$ mount /dev/fd0 /mnt/floppy

---

### Post by caljohnsmith on 2008-08-20
So just to clarify, do you actually have your server software installed now (minus Grub), or are those two partitions you set up empty?

If you haven't installed your server software, go ahead and do that and skip the Grub installation part. Once your server software is in place, please boot a Live CD and try the following:
```
sudo mount /dev/sda1 /mnt
```
Does that return an error? If not:
```
ls -l /mnt
```
And also do:
```
sudo grub
grub> find /bin/echo
grub> quit
```

---

### Post by know-it-some on 2008-08-21
Due to the physical location of the server I'll now have to do this next week.  more then.  Thanks!

---

### Post by know-it-some on 2008-08-21
Okay, I actually have some new info form Adaptec that may make this whole question moot.  Apparently if you are going to be booting off an array attached to one of their cards then you need a boot controller driver in order for GRUB to be able to boot an OS on the array.  Why this would not also apply to LILO I am not certain, but since LILO works as is I am going to just stick with it and let this point drop in favor of other challenges.  A thanks is in order to caljohnsmith anyway due to his willingness to help. Thanks again!

---

### Post by caljohnsmith on 2008-08-21
Glad you at least have a working solution at this point. :)

---

