---
title: "Ubuntu 12.04 crashing all of the time"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by NRF19 on 2013-06-21
Hi,

My Ubuntu 12.04 crashes to the point I have to hard reboot all of the time, no matter what I am doing it will crash, whether it be mounting a drive, trying to access a certain folder or just configuring a program.

My spec shouldn't be an issue as I am running:

Gigabyte GA-G41M-Combo
2 x 2Gb DDR2 RAM
Intel Core 2 Quad Q8200

I found a guide earlier which told me to update the kernel and so I did that up to 3.9.0 but still am suffering from the crashes.

I have installed a few programs listed including:

Sabnzbd
Sickbeard
Couchpotato
TVheadend
samba
xrdp
Psensor 
mhddfs

and am not sure whether it is one of these causing a problem?

Is there some upgrade I can do or failing that some log I can navigate to and post which would highlight whether it is one thing that is causing this?

Thanks

Edit: In the last 15 minutes it has crashed twice whilst I have been trying to access and move a certain folder in /media/root/Movies, reckon it could be a drive problem?

---

### Post by 2F4U on 2013-06-22
The log files are written to /var/log and you should take a look into them. They should contain a hint on whats going on. Is this a fresh installation and do you experience these problems from the beginning? Did you verify temperatures on the machine, since overheating may be the problem? Did you check the RAM in the machine (memtest from a liveCD may do that)?

---

### Post by NRF19 on 2013-06-22
Hey, thanks for the response, I'll take a look at the log. Temps and RAM are both fine and it is a fresh installation, I think it may be down to a specific harddrive but I'll check the log also

Thanks!

---

### Post by 2F4U on 2013-06-22
If it is a specific hard drive, boot into a liveCD/USB and run fsck on the drive. The reason for booting into a liveCD is that the drive should not be mounted while running fsck on it.

---

