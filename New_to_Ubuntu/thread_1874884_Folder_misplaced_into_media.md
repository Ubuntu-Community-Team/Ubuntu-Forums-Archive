---
title: "Folder misplaced into /media"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by kentfx on 2011-11-03
This is re: Ubuntu 10.04.  I inadvertently destroyed the boot record on the hard drive of a new HP machine (following some advice on a Ubuntu site, actually; evidently I mis-typed a command somewhere along the line).  That's been fixed -- I ended up reinstalling Ubuntu -- but afterwards 533 GB of hard drive space had disappeared.  That's more than half of the drive.

I finally located the missing space, mounted as a huge folder in the /media directory. The folder was named a long string of letters and numbers, and it included the original Ubuntu operating system along with all my documents and applications.  I renamed it AltDrive, moved the documents over to the newly-installed system, and am in the process of re-loading all my applications.  Meanwhile, the machine sees a great big "external drive" attached to /media.  It's empty now, so it can be used for storage, etc.

Does anyone know how I can make the machine recognize those 533 GBs as part of the hard drive proper?  It would be a great deal more convenient.  After my stupid "accident", I'm very wary of experimenting around with the system.  Thanks for any help.

---

### Post by Hedgehog1 on 2011-11-04
Once you have moved the data, and ALSO BACKED IT UP (hint hint), you can remove the partition, then then expand your 'good' partition to take over that space on the hard drive.

These steps are done when booted from a LiveCD/LiveUSB of Ubuntu.

Boot the LiveCD/USB, select 'run Ubuntu', and then use gparted to remove the unwanted partition and extend the 'good' one.

Be aware that if the 'good' partition is in an extended partition, you will have to enlarge the extended partition first.

***The Hedge***

:KS

---

### Post by Paqman on 2011-11-04
Hedgehog1 is right, you need to boot into a Live CD or USB. One trick though: the system will automatically mount any swap partitions it finds (to improve performance), and that will lock any other partitions that are within the same extended partition as that swap.

Simple solution: if you find any partitions are locked once you open Gparted, right click on your swap and "swapoff". You should then be able to make any changes you want.

---

### Post by kentfx on 2011-11-04
Thank you for your quick responses.  

I backup up the entire HP machine to a 2 TB external drive, then booted the computer with LiveCD and ran Gparted.  What it displays doesn't agree with the "Tree" column that displays in the file browser.  That shows these folders/systems:

Home Folder: 7.4 GB used, 71.2 unused
File System: 219.8 GB used, 71.2 unused
AltDrive: 25.0 GB used, 463.4 GB free

(The AltDrive is that mysterious folder under /media.)

_____

With Gparted there's a very different picture.

Device: /dev/sda
Size: 596.17 GB
Partition table: msdos

1. Partition: unallocated, 
   File System: unallocated
   Size: 1.00 MB

2. Partition: /dev/sda1
   File System: ext4
   Label: AltDrive
   Size: 496.19 GB
   Used: 7.98 GB
   Unused: 488.21 GB
   BOOT FLAG: (checked)

3. Partition: /dev/sda2
   File System: extended
   Size: 99.98 GB
 
   -- Partition: /dev/sda6
      File System: ext4
      Label: 97_GB _ext4
      Size: 90.46 GB
      Used: 14.69 GB
      Unused: 75.77 GB

   -- Partition: unallocated
      File System: unallocated
      Label: ext4
      Size: 1.00 MB

   -- Partition: /dev/sda7
      File System: linux-swap
      Size: 2.88 GB

   -- Partition: unallocated
      File System: unallocated
      Size: 4.0 MB

   -- Partition: /dev/sda5
      File System: linux-swap
      Size: 5.64 GB

____

So it seems to be saying that the system is booting up with that AltDrive, which is attached to /media and is practically empty, and which I was just about to delete.  

And there's NO reference (that I can see) to the "File System" that the file browser can see, which has 219.8 GB used and 71.2 GB unused.  

There's no pull-down menu in the upper right of Gparted that might show other partitions.


I wonder if you know what's going on here, and how it can be solved.  Or maybe I shouldn't do anything, just keep using it as it's (sort of) working.

Thanks for any ideas...

Kent

---

