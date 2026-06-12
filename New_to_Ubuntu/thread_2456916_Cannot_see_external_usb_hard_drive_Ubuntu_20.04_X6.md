---
title: "Cannot see external usb hard drive Ubuntu 20.04 X64"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by vafred69 on 2021-01-21
Hello all I'm a second time newbie. I have an external usb hard drive and cannot find it anywhere in Ubuntu 20.04 I'm running a dual boot windows 8 and Ubuntu 20.04 the drive is fine in windows but it is not listed anywhere in Ubuntu. I have tried to disconnect it and then reconnect it but no luck. If I plug a usb thumb drive in I get a popup that it is recognized. Any ideas or a starting point? The drive is set up as MBR and formatted as FAT32 Thanks in advance, Fred Watson

---

### Post by simon-webb on 2021-01-21
Hi Fred. Ubuntu has no trouble with FAT32, and the fact that you can see other (thumb) drives shows it's having no trouble with USB storage in general...so it's a strange issue. Are you sure the drive works on Windows, on the particular port into which you're plugging it? On some laptops, there can be a bunch of low-power USB ports to save power, which work fine for thumb drives but don't have enough power to drive spinning disks...so, if you're not always plugging the drives into the same port, it's possible that something like this is happening at a hardware level, rather than it being an OS-related issue. On the other hand if the drive definitely works in that specific port on Windows, yet doesn't work on Ubuntu, it would be useful to see what the kernel has to say about it. If you type (in the shell) sudo dmesg you can see the latest kernel messages. Immediately after doing that, plug in your problem drive, give it a few seconds, and then type sudo dmesg again. You might learn something useful from that output. Perhaps try it with the working drive first (the thumb drive) and then try it with the problem drive to compare the output and spot the differences.

---

### Post by vafred69 on 2021-01-21
Thanks I'll try that in a bit thank you

---

### Post by vafred69 on 2021-01-21
Simon
OK those are some long files:D I pasted the output to a text file for before and after plugging it in and will look for anything I can find. Thanks

---

### Post by vafred69 on 2021-01-21
Simon
OK it only looks different in the last 15 lines or so and it's about a USB Device but I don't understand what it means at all. Hmmmmm
is there a way to paste it here? Just the lines that are different about 15 lines.

---

### Post by vafred69 on 2021-01-21
Does anybody have any ideas where to start?

---

### Post by simon-webb on 2021-01-22
Yes, it's only the last few lines that matter: dmesg dumps *all* the kernel messages, so you're seeing a running commentary on everything hardware-related that's been happening since you booted...the last few lines should tell you what the kernel saw/did when you plugged in a new USB device. You can just copy and paste them here like any other text. To send shell output to a file you can use the > symbol after the command, like this:```
dmesg > dmesg.txt
``` Then if you can edit that text file in a friendly GUI editor like gedit if you like (gedit dmesg.txt)...just copy and paste the relevant text from there into your forum post.

OK, I've had a look at my own messages to see what you should be seeing when a FAT32 USB drive gets plugged in. I'm seeing "New USB device found", then a bunch of identifying info (stuff like "idVendor" and "idProduct" that can be used to look up exactly what the device is), then a bit further down "usb-storage" which tells us that the kernel's recognised the USB device as a storage device and has loaded up the part of itself that deals with such devices. If you type dmesg too quickly after inserting the drive, that will be quite near the bottom of the messages (again, I'm describing what *should* be happening, not necessary what you'll be seeing if something's broken) with only a couple more lines after "usb-storage"...but if you give it enough time for the drive to be mounted (typically a few seconds), you should see about half a dozen lines starting with the actual drive letter it's been assigned (so on my system it's sdc, though it might be sdb on yours if you have a single internal hard disk).

I'm guessing you *won't* see those last few messages about the drive's having been assigned a name in the filesystem. If you do see that, it's great news...it means things are basically working...but then I'd expect you also to see the volume mounted automatically in Files. Anyway, let's have a look at what you actually do see when you plug in the drive, as that may tell us what's happening.

---

### Post by yancek on 2021-01-22
What type filesystem do you have on the partitions on the external drive?  If it is ntfs and you see and use it on windows, you should check to see if windows is hibernated since no Linux OS will mount a hibernated partition.  Good place to start.

---

### Post by simon-webb on 2021-01-23
Yancek, does hibernating Windows really affect external drives? My understanding was that it would warn another OS not to boot the root partition (the one from which Windows boots), but external drives should not be affected by that. Also, the OP said it's a FAT32 drive...so not NTFS.

---

### Post by QIII on 2021-01-23
If it is NTFS and it is mounted when Windows is hibernated, then whether it is internal or external, it will be in a hibernated state and it Linux will not touch it.  If it is unmounted/ejected prior to hibernation, Linux will use it.

---

### Post by simon-webb on 2021-01-24
Wow, that's really useful to know. It won't be the issue in this case (as this is a FAT32 drive) but it's a potentially serious problem I'd never heard of. I'm surprised Windows doesn't just unmount external drives prior to hibernation: I wonder if it warns users that they need to plug all such drives back in before powering back on...otherwise (if the external drive is simply unplugged and packed away when the computer comes out of hibernation) presumably the data corruption (that the locking of the external drive aims to avoid) could still happen. Seems like a good reason to stick to vfat on USB drives.

---

### Post by ajgreeny on 2021-01-24
You can check the end lines of dmesg by piping the output to tail with command ```
dmesg | tail
``` which by default shows the final 10 lines, I think.

That is  big help in situations like yours, saves a long search of huge text files.

---

### Post by simon-webb on 2021-01-24
Yep, 10 lines by default...or if you want to see a few more, you can e.g.```
dmesg | tail -n 20
```to view the last 20 (same as for "head", which defaults to the first 10 lines but can dump as many or as few lines as you want with the -n switch).

Are you sure the drive is physically OK...do you have another machine with which you can confirm that it's still a working drive?

---

### Post by TheFu on 2021-01-24
**dmesg -w** maybe easier.  It is basically [B]dmesg|tail -f
[/B]
Also, sudo is not needed with dmesg ... er ... yet. There have been some discussions about properly locking log files, so sometime in the next few releases, sudo may become necessary.

As for the OP using fat32 or some other file system like exfat, it is possible to make a little mistake. On some linux distros, exfat  support is not standard. Extra packages need to be installed.

---

### Post by vafred69 on 2021-01-29
OK Sorry it's been so long but I found the problem. It was a bad USB Port. I plugged another portable hard drive into the same port and it was found fine. Then I plugged the one I was having the problem with into another port and it is found fine.

Thank you all for all your help It was my fault as I should have checked that before.
Fred Watson

---

### Post by TheFu on 2021-01-29
vafred69 - not uncommon. We've all done it.  There's something about having to explain stuff to someone else that gets our troubleshooting hats working.
In general, best to try and isolate what you think is the issue as much as possible.

Hardware, software, cables.  Think logically.  Simplify and test.  Do that over and over. until the only thing left is too small to split apart for testing, then replace that part/software/cable.

---

### Post by vafred69 on 2021-01-29
TheFu, Thanks I guess it was just a panic moment but thanks for the help from everyone here anyway.

Fred Watson

---

