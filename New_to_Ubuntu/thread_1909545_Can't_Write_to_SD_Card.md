---
title: "Can't Write to SD Card"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by DGINSD on 2012-01-15
In my Dell X300 laptop there's a built in Richo SD Card reader which Ubuntu recognizes it can see and mount when a car is put in and unmount (eject) it as well. If I try to copy a file there the options to do any type of file creation (new file, new folder, copy) are all greyed out. I've tried changing permissions using gksudo nautilus but I get an error message. 

```
Sorry, could not change the permissions of "9029-62AD": Error setting permissions: Read-only file system
```

What am I doing wrong? I seriously doubt they would put a card reader in a laptop that couldn't write to it as well but I've seen more stupid things than that.

My other question is related and dependent on the first, I have an extra 2Gig SD card, is it possible to use this card as an swap space insted of the HD, this computer has low RAM so it seems to be swapping a lot so I'm hoping I can use the SD card as swap to speed it up a bit.

On a side note there use to be a program in Ubuntu to see what programs and services ran at start up and allowed you to get rid of the ones you didn't need, was great for people like me with older machines  to free up as much RAM as possible for the thing I actually use. I thought it was called Startup Applications but the only application listed is the gnome login sound. I know I should just buy more RAM but I'm actually saving to get some new computers so I'm really in need of a temporary options

---

### Post by BC59 on 2012-01-15
Is the card formatted to ext4 or to NTFS-FAT?
If is formatted to NTFS you cannot change permissions.

---

### Post by BC59 on 2012-01-15
For the other question, the external card will be always be slower to the internal HDD, so it's not recommended for swap. You are going to have a slow system.

---

### Post by Carterclan on 2012-01-15
Not sure if this will work for you, but in answer to your first question I recently had the same thing with my sons usb dongle.
He could do anything with it on his mums Windows based PC but not with either mine or his Ubuntu one.
The solution turned out to be simple. When he was disconnecting from Windows he was not using the 'safely remove' option, as soon as he done this in Windows he could write to it in Ubuntu.
As I say, might not be applicable to you but worth a try.

---

### Post by bluexrider on 2012-01-15
[IMG]http://www.psychocats.net/ubuntu/index[/IMG]
[IMG]http://www.psychocats.net/ubuntu/images/ubuntucat.jpg[/IMG]
[Unmount the partition]("http://www.psychocats.net/ubuntu/mountwindowsfstab#unmounting")
[Examine the partition table]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fdiskl")
[Create a mount point]("http://www.psychocats.net/ubuntu/mountwindowsfstab#mountpoint")
[Edit the /etc/fstab file]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fstab")
[For FAT32 (instead of NTFS)]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32")
[Save changes]("http://www.psychocats.net/ubuntu/mountwindowsfstab#finish")
[Enable read/write for NTFS]("http://www.psychocats.net/ubuntu/mountwindowsfstab#ntfs3g") <<<<<<  This may provide the solution the the problem
  

REF: [HERE]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

---

### Post by DGINSD on 2012-01-16
> **BC59 said:**
> Is the card formatted to ext4 or to NTFS-FAT?
If is formatted to NTFS you cannot change permissions.

It is formatted as FAT, also I do have read write enabled for NTFS (I can copy and paste files in a mounted windows partition).

The Tutorial on mounting windows partitions seems a bit out of date mu fstab looks nothing like any of the examples everything is listed as UUID and the hda1 type data is commented out #, no mention of any windows partitions. Is fstab even used in any capacity any more?

I actually reformatted the sd card so it should be a fresh plate to copy stuff to but no luck, much of this is over my head but I'd love to learn something here.

---

### Post by mcduck on 2012-01-16
If you get error about read-only filesystem even when running as root (or usign gksudo nautlus) then it's not a permission question, the filesystem contains errors and to protect it from further damage Linux has mounted it as read-only.

Run some kind of check for the partition on your SD card. Fixing whatever errors it has should automatically make Linux mount it normally again.


(and yes, fstab is still used. Gnome and other desktop environments have theur own mechanisms for mounting removable drives and any drive that isn't configured in fstab, but any system partition, and any one that you want to be able to configure in any detail, needs to be in fstab.)

---

### Post by DGINSD on 2012-01-16
> **bluexrider said:**
> [IMG]http://www.psychocats.net/ubuntu/index[/IMG]
[IMG]http://www.psychocats.net/ubuntu/images/ubuntucat.jpg[/IMG]
[Unmount the partition]("http://www.psychocats.net/ubuntu/mountwindowsfstab#unmounting")
[Examine the partition table]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fdiskl")
[Create a mount point]("http://www.psychocats.net/ubuntu/mountwindowsfstab#mountpoint")
[Edit the /etc/fstab file]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fstab")
[For FAT32 (instead of NTFS)]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32")
[Save changes]("http://www.psychocats.net/ubuntu/mountwindowsfstab#finish")
[Enable read/write for NTFS]("http://www.psychocats.net/ubuntu/mountwindowsfstab#ntfs3g") <<<<<<  This may provide the solution the the problem
  

REF: [HERE]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

Then is this tutorial still valid or is there a more up to date one? Do I just add lines accordingly or do I need to format them with UUID numbers and if so how do I find those.

With regaurds to the SD card having bad sectors, I have reformatted it with a windows machine but it really didn't change anything.

---

### Post by cortman on 2012-01-16
Real basic question: Almost all SD cards that I'm familiar with have a little "lock" switch on the side- did that get slid to "locked" accidentally?

---

### Post by DGINSD on 2012-01-17
> **cortman said:**
> Real basic question: Almost all SD cards that I'm familiar with have a little "lock" switch on the side- did that get slid to "locked" accidentally?

No the lock is and was off.

---

