---
title: "How to create persistence on a USB stick that already has Ubuntu OS?"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by theotaxis on 2015-01-29
I downloaded and "burned" ubuntu-14.10-desktop-i386.iso to a USB thumb drive. It is bootable on my machine and when I clicked "Try Ubuntu" the OS created live sessions that worked. It is amazing.

However I would like to have persistence on the same USB thumb drive so that I can store data on that persistent partition.

How do I create a partition a USB thumb drive that already contains a bootable Ubuntu OS?

I have studied an article ([https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)) but it does not answer my need.

---

### Post by ian-weisser on 2015-01-29
> **theotaxis said:**
> How do I create a partition a USB thumb drive that already contains a bootable Ubuntu OS?

It is usually much easier to use your downloaded .iso file to re-create the LiveMedia with persistence.

Partitioning tools can be risky for beginners - a typo can overwrite your beloved HDD. Not a good starting point.

---

### Post by sudodus on 2015-01-29
> **ian-weisser said:**
> It is usually much easier to use your downloaded .iso file to re-create the LiveMedia with persistence.

Partitioning tools can be risky for beginners - a typo can overwrite your beloved HDD. Not a good starting point.

+1

I suggest that you use ***Unetbootin***. There is an options to create persistence (you can select the size of the 'space used to preserve files across reboots').

---

### Post by yancek on 2015-01-29
You can modify a flash drive with a bootable Ubuntu Live CD on it per the instructions at the link below.  You would probably need an installed Ubuntu system as you will need to shrink the partition on which the Live CD is installed to using GParted.  You could then create another partition using the remainder of the flash drive as long as you use a Linux filesystem type and not FAT32.  If you only have Ubuntu on a flash, I don't think that will work but I have never tried.  You will probably be better off using Unetbootin as already suggested and doing it over.

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by JeQhdMD on 2015-01-29
Can also use "startup disk creator" . . . from an Ubuntu standard system.  A bit more user friendly than some.   Use your current flash-stick to boot into a "try ubuntu" session.   Plug in a second usb-flash stick in another usb port.   Search the live session (use the dash tool) for "startup disk creator' . . . . be sure to have the original ubu 14.10 iso accessible (via a windows folder, or via copy'ing it into one of your two flash-sticks.   Follow the screen instructions on the "startup disk creator" program, and recreate the bootable drive.

---

### Post by Mike_Walsh on 2015-01-29
I tend to agree with some of the others here...especially sudodus, as I've done the same thing many times myself.

You really would do just as well to recreate the stick using Unetbootin.....and set up your persistent file at the same time. It's only a 10 minute job at best, but be warned; IF you decide to create the largest size of persistent partition (just under 10GB, if I remember correctly), it WILL take a while.....since the write speeds of flash drives are a lot slower than those of a hard drive.

Creating the persistence IS the longest part of the procedure.


Regards,

Mike.

---

### Post by C.S.Cameron on 2015-01-29
The following is a step by step for making a dandy little persistent flash drive, you can vary partition size depending on your needs:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens, use the following code for 64bit systems.



```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz.efi
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

---

### Post by yancek on 2015-01-29
> 
How do I create a partition a USB thumb drive that already contains a bootable Ubuntu OS?

I might be reading the question by the OP incorrectly but, it seems to me that he wants to use the flash drive to create a persistent file/partition on the same flash drive.  If the system on the flash is just one partition, I don't see how he can do it because he would have to resize that partition from the running system which can't be done because he needs to unmount before resizing.  If he does have another Ubuntu or Linux system, he should be in good shape with all the advice above.

---

### Post by C.S.Cameron on 2015-01-31
There is info kicking around on how to create a casper-rw file from scratch.
If he drops this file onto the Ubuntu partition and then edits syslinux.cfg as shown in post #7 above he should end up with a persistent drive.
text,cfg or txt.cfg can alternately be modified by adding a space and then the word persistent after --.

The easiest thing to do is format the drive and create a persistent drive using Startup Disk Creator or UNetbootin.

---

