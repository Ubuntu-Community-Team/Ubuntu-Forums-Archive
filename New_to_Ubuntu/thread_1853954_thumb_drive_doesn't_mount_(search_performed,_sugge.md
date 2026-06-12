---
title: "thumb drive doesn't mount (search performed, suggested action didn't work)"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by tbrenholts on 2011-10-03
Here are the details:

Ubuntu 11.04, installed on a 5 year old HP laptop (typical Best Buy AMD product) as the sole OS. Installation was smooth from a USB thumb drive, everything works, email is set up, wireless, etc., all are fine. 

After the install, the thumb drive showed up on the desktop with the USB symbol. I powered it down and ejected it, ran the system updates, and then tried using the drive to transfer some photos and music to the computer, but I can't get the drive to mount. 

The thumb drive shows up in the Disk Utility; I ran the read and write tests, to make sure that there was no problem with the USB port. I opened a terminal and did the gconf-editor, and app>nautilus>preferences, and auto mount and auto start upon mount are both checked. 

I'm just not at all familiar with any form of Linux to even know where to start looking for this solution. Any help would be appreciated, thanks.

---

### Post by cavh on 2011-10-03
See if this helps

[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by tbrenholts on 2011-10-03
Yes, thanks cavh, that is what I tried. I don't understand why it doesn't work. 

If it continues, I'm going to give up on solving the problem; the laptop is set up for my wife to use, she's totally point-and-click and doesn't care about thumb drives. I want her to have something that I don't have to worry about trojans and rootkits etc. Ubuntu is pretty slick, I think; I like the integrated email and social networking. It's a pretty simple interface and seems to work seamlessly.

Tom

---

### Post by cavh on 2011-10-04
If you no longer need any of the data on the drive, try formatting it on another machine (if you can mount it, that is!). If you have a Windows box, you can format the drive as FAT32 and Ubuntu will be able to read it.

---

