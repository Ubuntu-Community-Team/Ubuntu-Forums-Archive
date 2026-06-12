---
title: "Installing Ubuntu on a dedicated partiton without affecting Windows"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by dakukuu on 2011-10-17
I've heard of stories that installing ubuntu on a dedicated partiton messes up the Windows install and requires the Windows disc, which i do not have as my laptop had it pre-installed.

Is there a way of installation without requiring the windows disc? I am currently using a Wubi partiton and apparently it eventually messes up the NTFS partition. I'm not new to linux so any method will be okay, except buying another windows copy is not an option (Sorry to make life hard, but my money is limited). 

I posted this here because this is a really basic question that i don't know the answer too. Any help is appreciated.

---

### Post by Mark Phelps on 2011-10-17
> **dakukuu said:**
> I've heard of stories that installing ubuntu on a dedicated partiton messes up the Windows install and requires the Windows disc, which i do not have as my laptop had it pre-installed.
That only happens when folks make mistakes and reformat the Windows partition by mistake.  But, the Ubuntu install will overwrite the MBR.

> Is there a way of installation without requiring the windows disc? 
Ubuntu installs never require any Windows media.
> I am currently using a Wubi partiton and apparently it eventually messes up the NTFS partition.
Never heard of that happening.  Wubi installs create a single large file on the NTFS partition -- root.disk.  They also add an entry to the appropriate Windows boot loader.  Both are removed when you simply "uninstall" Ubuntu -- the same as you would do with any other Windows application.
>  I'm not new to linux so any method will be okay, except buying another windows copy is not an option (Sorry to make life hard, but my money is limited).

You didn't say which Windows you have, but the safest thing to do, to prevent any damage to Windows, is to image it off to an external drive -- so you can restore it if anything happens.

If you don't have an external drive, you can do the same to DVDs, if you have a DVD writer in your PC.

But, before you attempt any kind of dual-boot install (separate Linux partition), open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list off your partitions on your hard drive.

---

### Post by roger_1960 on 2011-10-17
Hi

Often, there is a facility to create a recovery image on an external media (disk or USB stick) included in the windows install.  Have a look in the manual/help and if it exists use it.

Then

Backup all your data.

Uninstall Ubuntu (wubi install) using the windows uninstall facility - as for any windows program

Defragment your windows drive using the windows tool for this. This is important.

Burn a USB stick or live CD of the Ubuntu you wish to install.

Boot to this live version.

Use gparted on the live CD/USB to resize the windows ntfs partition - ie make it smaller to leave room for Ubuntu.  Do not encroach onto the area of partition which is in use by windows.

Use the install icon on the desktop to install ubuntu into the free space you have created alongside the exiting windows installation.  I would suggest it needs to be about 10GB minimum to give a little leeway on space.

This should give you  a dual boot system with the choice given to you at start up.

There are other options for partitioning such as creating a separate home partition, but the above is the basic method. I'm not aware that this messes up windows - has worked for me before.

If you have any questions before doing this, post back before you start.  It may be worth running gparted and looking at your partition  - and posting it back to here - before you start.

---

### Post by Mark Phelps on 2011-10-17
You didn't say which version of Windows you're running -- would have helped with providing more detailed advice.

But, if you're running Windows 7, do NOT, repeat NOT, use GParted or the Ubuntu installer to shrink your Win7 OS partition to make room for Ubuntu.  Instead, use the Win7 Disk Management utility to shrink the partition.  Then, afterward, boot into Win7 a couple of times to allow it to make any filesystem adjustments.

Also, again, if you're running Win7, once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

