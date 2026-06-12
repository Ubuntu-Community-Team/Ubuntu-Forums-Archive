---
title: "How To Change USB Memory Device Back to Removable"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-04
In May of 2012, I got help at this forum, changing an external usb memory stick (thumb, jump, pen, Flash drive) from being seen by the OS as a removable to a non-removable device. I wanted it to be 3 things: 1 - removable, 2 - able to run LinuxOS executables and 3 - to run Microsoft Windows executables. I started using Lastpass password manager software and an add-on to Lastpass called: Sesame. Those two create a 2-step password verification. Very secure.

Time went by and during some problems with my root directory getting overfilled with out-of-date kernels and images and the like, the splash screen started to say that the thumb drive was not mounted and did I want to

(S)kip, (C)ancel or (M)ount Manually. 

For I while I chose skip. Then one morning the OS [would not boot]("http://ubuntuforums.org/showthread.php?t=2109070"). I spent the weekend with help from around the globe (this forum) and got my operating system back. But the usb device (called Lexar) still would not mount and as it has Cryptkeeper encrypted files on it, I could not obtain access to them.

I spent the [next few days]("http://ubuntuforums.org/showthread.php?t=2111329") figuring out how to either work-around, by-pass or fix the /Lexar not mounting. Whether my solution is temporary or permanent, I don't know for certain. But that doesn't much matter. What I want to do is UNDO the way the removable USB device is seen by the OS and revert it back to being a (typical) removable device. 

The reason I want to do this is I am deleting the partitions that the Microsfot Windows used. I will no longer have to run their executables. I want to copy the data/files/folders from the thumb drive to my desktop, run GParted against the thumb drive and change the file system to ext3. Then copy the documents back. No more Mr. Nice Guy.

I spent yesterday and today searching for a way to change the USB device back to "normal", but cannot find a way to do that. What's more, the: [Introduction to Fstab Community page]("https://help.ubuntu.com/community/Fstab") even goes so far to say:

[COLOR="Red"]"Removable devices such as flash drives *can* be added to fstab, but are typically mounted by gnome-volume-manager and are beyond the scope of this document."[/COLOR]

So, someone who knows, point me to the document that has within in it's arcane knowledge, how to aright my wrong(ly) mounted device.

---

### Post by Mark_in_Hollywood on 2013-02-05
After coming to the understanding that the sensitive data on the Lexar usb drive could be copied to somewhere else, I booted into LiveUSB mode. There the Lexar drive partition was removed and re-installed as ext3. It was also given a new Label.

Upon re-booting into (what should be the correct word here?) ordinary OS (Main, Real, non-LiveUSB?), and using nano, I commented out the uuid of the Lexar device, in /etc/fstab. Saved and exited. Then using a terminal I entered superuser mode (sudo su). Changed directory to root ( / ) and removed the entry LEXAR.

I re-booted as a safety measure to insure that the changes didn't affect the OS or / or the removable devices otherwise and find that the OS isn't issuing a splash screen error or warning.

I plugged the Lexar back into a usb port. Opened a terminal and looked around the file system. At /media there is an entry LEXAR. I believe the devices' firmware is controlling that. But as there was no entry for LEXAR in root ( / ), I believe things are back to normal.

Running both fsck and dpgk from the GRUB Recovery does hang at /sda5, which is my /home partition. I'll post about that when I get it fixed. 

UBUNTU? YES, safety in numbers. 

Thank you, Linux Community for your help.

---

