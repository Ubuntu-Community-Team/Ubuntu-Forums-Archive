---
title: "Vodacom ON9 Ubuntu 10.04 ARM Help"
date: 2017-05-19
forum: New to Ubuntu
---

### Post by majewski97 on 2017-05-19
Good morning, afternoon or evening Ubuntu Community. I don't know if this issue was posted already.

First let me introduce myself, my name is Ewald ):P, I am from South Africa and I am an IT Technician specializing in Windows and thus never worked on a Linux platform before. I have a Vodafone Webbook ON9 with me that I am struggling to fix, it is running Ubuntu ARM 10.04 if I am not mistaken. 

**_Backstory_**
The Vodafone Webbook ON9 was first booked in for a password removal through intense googling :lolflag:  I got the commands to do it "mount /dev/mmcblk0p3 /mnt" "chroot /mnt" "passwd" I entered the new password in twice, rebooted and viola I was in, I noticed there was a pretty big folder, consisting of music, pictures and documents, on the system around 3GB or something, I am saying it is pretty big because the webbook only has 4GB available space, I informed the customer about this and asked if I may delete it, his answer was yes, when I deleted the folder the webbook froze and rebooted.

**_End of Backstory_**
When the computer rebooted It booted up past the vodacom splash bios logo, (I am unable to get into the bios, not with holding in escape or shift, or repeatedly pressing escape or shift, I don't even know how to get into the bios, to be honest.) I was met with this screen: [ATTACH=CONFIG]275169[/ATTACH]

I then downloaded the Ubuntu 10.04 ARM edition after another search from google burned it on a disc (This webbook doesn't have a built-in optical drive.) Attached a USB Optical Drive hoping it will boot up, like I am used to. But to no avail, it doesn't pick up the optical drive. I tried running fsck and msck commands to maybe repair the drive but I keep getting the " /bin/sh fsck command not found and when I use ls /sbin, fsck nor msck appears to be listed.

Is there something I am missing? 

At this point I gave up already, if you guys can maybe help me with this, it will be very appreciated. Maybe how to delete that big folder, or reloading the OS or repairing it. 

Thank you for your time guys and ladies :)

---

### Post by vasa1 on 2017-05-19
10.04 is no longer supported. You will not receive updates, including security updates.

---

