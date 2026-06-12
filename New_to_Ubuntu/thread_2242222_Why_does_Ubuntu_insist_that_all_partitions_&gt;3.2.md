---
title: "Why does Ubuntu insist that all partitions &gt;3.2gb?"
date: 2014-08-31
forum: New to Ubuntu
---

### Post by stevef48-0 on 2014-08-31
I have 2 hard disks and an SSD in my Windows 7 PC and would like to install Ubuntu on the SSD. Each time I tried the installation failed, because one of the partitions is less than 3.2gb (Windows 7 loader 100mb).
Please can you explain why Ubuntu needs all partitions to be >3.2gb, when I don't even want it to use the smaller one? Is there anything, apart from messing with the Windows 7 loader partition, that I can do to install Ubuntu?

---

### Post by sandyd on 2014-08-31
Hi, can you take a screenshot of your current partitioning (I assume you clicked 'custom installation' (or similar) at the partitioning window)

Also, go to the Unity Dash (Button on the top left corner of the screen), and type in Terminal.
Click on the first option.

In the terminal window that appears, type in
```

sudo parted -l
```
and post back the output.

The output should look similar to
```

root@SerenityShine:~# parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: QEMU QEMU DVD-ROM (scsi)
Disk /dev/sr0: 380MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End    Size    Type     File system  Flags
 2      294MB  320MB  25.8MB  primary


Model: Virtio Block Device (virtblk)
Disk /dev/vda: 10.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  10.2GB  10.2GB  primary  ext4         boot
 2      10.2GB  10.7GB  537MB   primary  ext3
```

Thanks!

---

### Post by yancek on 2014-08-31
> Please can you explain why Ubuntu needs all partitions to be >3.2gb

It doesn 't.  We can only guess what is happening without more information.  Indicating what warning/error messages you get would be helpful.

---

### Post by uRock on 2014-08-31
The following links may be helpful,

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

### Post by stevef48-0 on 2014-09-04
I didn't do a custom install, I just asked for Ubuntu to install alongside the existing Windows 7.
How do I 'take a screenshot of your current partitioning'?
I'll add the output from the sudo, when I've booted the PC.
Bye for now,
Steve

---

### Post by uRock on 2014-09-04
If need to be, use your phone to take a picture of the screen where you are seeing the problem.

---

### Post by yancek on 2014-09-04
You might have 'Screenshot' which can be used.  I don't know if it is on the installation medium but you can easily find out by clicking the dash (Ubuntu logo in the upper left of the Desktop) and typing 'screenshot' in the Search box.  If it comes up use it, if it doesn't use the phone will work or a digital camera.

---

### Post by ajgreeny on 2014-09-05
Usually just pressing the print-screen button gives you a screenshot of the whole monitor and Alt+print-screen gives one of the active window. It may, however, depend on your system DE.

---

### Post by stevef48-0 on 2014-09-06
The problem went away, I created a USB drive using the latest version of Ubuntu and it won't run, so I've given up. I clicked on Try Ubuntu, the screen went blue and the mouse froze. I left it for 20-30 minutes, no change. Tried a different distro, same result, so I give up. That PC will have to stay on Windows 7.
Thanks for your help,
Steve

---

### Post by JeQhdMD on 2014-09-06
Maybe the original issue is that ubuntu needs at least 3.2 gb to install . . . so is it possible that you were trying to install to a partition under that size?  (versus just having "a" partition on the ssd <3.2 gb?)    Also, creating a bootable usb flash-stick isn't sufficient to boot from IF the bios hasn't been modified to a new boot sequence (usb 1, Optical Disk 2, ssd 3, hdd 4, etc.).   And did you have a good image for the Ubuntu download . . . checksum right?    By the way, a custom install is always a good way to actually see what's going on during the install.   So, maybe a little more patience and effort will result in success versus failure.

---

### Post by stevef48-0 on 2014-09-15
The installation failed despite me trying to use two different partitions each over 100gb.
If I had not specified the correct boot order Ubuntu wouldn't have started at all.
I didn't notice a 'custom install' option, but as I asked for Ubuntu to be installed alongside Windows, I probably used it.
I don't believe Ubuntu and the other distro would both have downloaded with errors, but I will try again and validate the checksum.

---

### Post by oldfred on 2014-09-15
Ubuntu often fails if Windows is hibernated, or needs chkdsk. And it needs chkdsk after any resize. Existing 100MB boot and main Windows installs do not make any difference to Windows installer as those are standard.

It can also fail if you used Windows and converted partitioning to dynamic from basic by creating more than 4 primary partitions or have used all 4 primary partitions, so there is no space for Ubuntu even if drive has unallocated space.
That is why we need to see your current partition scheme to know what the issue may be.

---

### Post by uRock on 2014-09-15
We've offered requests for specs, output from commands, and screenshots. We can't help you without more information.

---

### Post by stevef48-0 on 2014-09-15
Sorry, with all the issues installing Ubuntu I ignored your requests.
When I ran Windows Disk management I discovered 2 hitherto unknown partitions on the 2nd hard disk, both under 3 gb, which I've now deleted.
I'll try reinstalling, if the Live DVD will work - it hasn't so far, and let you know what happens.
Thank you for your patience,
Steve

---

### Post by stevef48-0 on 2014-09-15
OK latest update:
Ubuntu installed after I deleted the two small partitions, so the original question is still not answered.
All I did was delete two small partitions, nothing else. It isn't as if I told the Ubuntu installer to use one of the small partitons. They weren't on the primary HDD either.
I'm still mystified.

---

### Post by uRock on 2014-09-15
This almost sounds like the actual problem was that you already had 4 primary partitions. Once you deleted them, the installer was able to create what it needed when using the "install alongside Windows" option. I've always used the "Something else" option.

---

### Post by JeQhdMD on 2014-09-15
By the way, installing "alongside" is not the same as a custom install.   The actual wording on the ubuntu installer screen is "something else" referring to another method/option for the install.   That is the entry that takes you into the custom install screens, and by doing so, allows you to see and modify your partition tables, sizes, order, where to put bootloader, etc.   I wish the installer screen was clearer, but, that's the way it's been for at least 3-4 years.   

Good luck with running Ubuntu now that it's installed.   Here's a good link general info about Linux & Windows distinctions:  . . [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by stevef48-0 on 2014-09-16
Ubuntu ran once, then stopped working. There's obviously something wrong with my PC, but I don't know what yet.
Maybe, as you said, too many primary partitions. Ubuntu is not a priority, I'll try again when I'm not so busy.
Thanks you everyone for your help and suggestions
Steve

---

