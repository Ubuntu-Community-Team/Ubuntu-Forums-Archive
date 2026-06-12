---
title: "How to access a USB drive from Ubuntu Server Terminal?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-08-13
I have to load network drivers in order to get my motherboard’s onboard LAN to work. I have the drivers on a USB drive, and can see them if I boot from the Live CD. From the terminal, though, I can’t figure out how to access the flash drive. I’ve tried lots of the available tutorials and how-tos, but to no avail. At some point the screen doesn’t display or do what the tutorial says it should. For example, in [this](http://tldp.org/HOWTO/html_single/Flash-Memory-HOWTO/#physical) How To, everything works until I get to “The path  /proc/scsi/usb-storage-0/ should now exist.” It doesn’t exist, and the rest of the tutorial doesn’t apply. 

All I really want to do is access the drive, not necessarily mount it—but in all the tutorials I’ve seen it appears that I need to mount it before I can read/transfer files from it. If there is an easier way to do this (e.g., DOS cd: F, then go from there), by all means let me know. Or if there’s a way to boot from the Ubuntu desktop Live CD and move files from the flash drive to my HDDs, that would be great too. Heck, if I can get apt-get install ubuntu-desktop to read from the CD drive, even that would work. But in the meantime, is there a tried and true USB-reading, Ubuntu Server Terminal-specific, How To that I can follow? And if it doesn’t work, can I ask follow-up questions here?

Thanks, 

Rhythm

---

### Post by viciouslime on 2008-08-13
You will need to mount it in order to access data on it, however ubuntu server should do this for you. By default it will mount it in /media

It will probably be /media/disk, but if you change to /meda (cd /media) then run "ls" you will be able to see everything that's been mounted there and can go through them by trial and error (there'll be very few).

Hope that helps :)

---

### Post by Rhythmdvl on 2008-08-13
Thanks~

I’d gotten a bit frustrated in the meantime, and pulled a NIC (it’s got to be circa 1996-7!) from an older “parts” machine and dropped it in – it linked up right away. So after a bit of reinstall shenanigans, I made it to the Server prompt and the first thing I did was apt-get install ubuntu-desktop. 

I’m still grateful for your reply — while the GUI does make getting up and running easier for the newbie, I think learning the command shell is imperative.

---

