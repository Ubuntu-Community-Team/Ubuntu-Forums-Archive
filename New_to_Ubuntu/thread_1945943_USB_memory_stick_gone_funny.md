---
title: "USB memory stick gone funny"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by Homeground on 2012-03-23
Ubuntu 10.04. I may have made a mistake preparing the flash drive. Initially it was set to FAT32, as it was a new drive. In Gparted I immediately formatted it to ext4. Then I chose Create Partition table. That resulted in the drive turning into "unallocated". At that point I realized I should have chosen "New". So I crossed my fingers and did that. I reformatted as ext4 without partitioning and gave it the label "USB8". Then I looked at the contents in the File Browser. It contained a file, marked with a big white "X", titled Lost+Found. I right-clicked on it and chose "Properties". It said,

Name: Lost+Found
Type: folder (inode/directory)
Location: /media/USB8 
Volume: USB
Free Space: Unknown

Rather than make things worse, I thought it was time to get some advice. Is this fixable?

---

### Post by wildmanne39 on 2012-03-23
Hi, what are you wanting to use it for media or a bootable usb for ubuntu?
Thanks

---

### Post by Homeground on 2012-03-23
^I wanted a bootable USB with Ubuntu installed, just as a backup.

---

### Post by wildmanne39 on 2012-03-24
Hi, use staartup disk creator in ubuntu to make one, just click to erase what is on the drive then to install ubuntu on to it and it will do the rest for you.
Thanks

---

### Post by Homeground on 2012-03-24
I just tried that. I clicked on Erase. I got a pop-up message "org.freedesktop.Udisks.Error.Inhibited:  Daemon is inhibited."

---

### Post by wildmanne39 on 2012-03-24
Hi, it looks like it is because the drive is not mounted if that is the case open disk utility then mount it and close disk utility and try again.
Thanks

---

### Post by Homeground on 2012-03-24
..

---

### Post by stubbs4 on 2012-03-31
If you want a bootable USB stick with UBUNTU installed, do not use Startup Disk Creator. All it does is copy the iso to the stick. If you want a truly bootable stick that you can plug in and boot "your" system on any machine try this:
[http://azcrumpty.weebly.com/1/post/2011/10/full-usb-flash-drive-install-with-ubuntu-1110-oneiric-ocelot.html](http://azcrumpty.weebly.com/1/post/2011/10/full-usb-flash-drive-install-with-ubuntu-1110-oneiric-ocelot.html)

Glenn

---

