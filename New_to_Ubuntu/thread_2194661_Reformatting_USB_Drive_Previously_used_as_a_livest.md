---
title: "Reformatting USB Drive Previously used as a livestick"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by Mattaus on 2013-12-19
Hi all,

I'm going insane here so I have to ask. I have previously been running Openelec on my HTPC off a 16GB UB Flash Drive. I know want to use that flash drive for something else so I am trying to reformat it. When I insert the flash drive into my desktop (which is running Windows 7 for the time being, so I only have access to Ubuntu via a live CD) GParted scans endlessly. If I run fdisk -l, that thinks forever as well once it gets to the USB drive. If I try mkfs it says the device is busy. Windows can see the flash drive inserted into my system, but I cannot interact with it in any way. Ubuntu mounts the drive and I can even browse the drive.

As eluded to however, I cannot for the life of me get anything to actually 'wipe' this flash drive so I can use it for something else!

What can I do?

- Matt

---

### Post by tfrue on 2013-12-20
Well, you have several options. First being, use Window's to format it. Make sure not to do a quick format and then go from there. If you do use Window's, try and go back into your live cd and run the same fdisk options you tried before and see if that works.

In Ubuntu, does it try and mount the drive when you plug it in? If it does, try and use the Disk utility to unmount the drive and format it from there, or leave it mounted if it needs to be.

Now this part is going to be intense, so bare with me. But before I get to the intense part, are you getting into the usb through fdisk? If so, are you deleting the partitions then saving the changes and using mkfs to make the proper fs?

---

### Post by Mattaus on 2013-12-20
That's the thing - windows can see the drive in the Device Manager, but it won't mount for me to actually browse it. As I can't view it in Windows Explorer, I am unable to format it.

In Ubuntu it auto mounts it straight away. When I start the disk utility is spends eternity (literally - it never finalizes) loading the available drives. If I use the disk utility without the USB drive inserted, it finishes almost immediately. 

I am UNABLE to get to the disk through fdisk. 

In any OS I am unable to format the drive. I have NFI what is going on - I've never seen this before.

---

### Post by tfrue on 2013-12-20
The thing is, we don't want it to mount as I believe its not possible to format a drive if it's mounted. So if you know a way for it not to auto mount, or unmount it from the desktop, then read this and set both to false, and then when we are finished don't forget to set them back to true. You may need to restart your computer.:

To enable or disable automount open a terminal and type **dconf-editor** followed by the **[Enter]** key. 
Browse to **org.gnome.desktop.media-handling**. 
The **automount**  key controls whether to automatically mount media. If set to true, then  Nautilus will automatically mount media such as user-visible hard disks  and removable media on start-up and media insertion. 
There is another key **org.gnome.desktop.media-handling.automount-open**. This controls whether to automatically open a folder for automounted media. 
If  set to true, then Nautilus will automatically open a folder when media  is automounted. This only applies to media where no known x-content/*  type was detected; for media where a known x-content type is detected,  the user configurable action will be taken instead. This can be  configured as shown below.

Now try using fdisk -l and see if that works and I will wait for your response before we continue.

---

### Post by tfrue on 2013-12-20
You might could try and use Precise Puppy, install to a CD or USB and try and mount and wipe the drive through that OS. I haven't ever had any problems with Puppy Linux

---

### Post by tfrue on 2013-12-20
It might also help if you post the output of
```
dmesg | tail
```

---

### Post by Mattaus on 2013-12-20
Thanks for your help so far :) I'll have to give this a try in the morning as I do not have any more time tonight.

---

### Post by tfrue on 2013-12-20
> **Mattaus said:**
> Thanks for your help so far :) I'll have to give this a try in the morning as I do not have any more time tonight.

No problem! Well, see you then!:D

---

### Post by The Cog on 2013-12-20
I would probably just wipe the partition table and then reformat from windows. To wipe the partition table, use the command ```
sudo blkid
```before and after inserting the stick to see which new device appears. Assuming the stick turns out to be /dev/sdf, this command will wipe the partition table by copying 1M of zeros to it:
```
sudo dd if=/dev/zero of=/dev/sdf bs=1M count=1
```

---

### Post by Mattaus on 2013-12-21
Well that was all a waste of time! The problem I was trying to fix (OpenELEC not working on my network...among other things) was corrected through a total fluke, so my need to wipe and start fresh (with regular XBMCbuntu) is not needed anymore.

Nonetheless I've saved this thread to my favorites so I know what to try next time I invariably have this problem.

---

### Post by tfrue on 2013-12-22
Don't forget to mark this as solved, and glad you found a fix!

Chris

---

