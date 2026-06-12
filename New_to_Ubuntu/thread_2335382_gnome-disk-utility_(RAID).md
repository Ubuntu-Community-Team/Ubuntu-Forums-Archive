---
title: "gnome-disk-utility (RAID)"
date: 2016-08-28
forum: New to Ubuntu
---

### Post by gerd88 on 2016-08-28
Hi there,

I just upgraded LTS to 16.04 and noticed that the disk utility does no longer display RAID information. 

It appears it has been discontinued on purpose. 

So I'd like to ask if somebody knows an alternative GUI with some basic RAID support. For serious things I use the command line anyway. However, it was nice to have a GUI.

Thanks in advance for your replies!

---

### Post by slimx3m on 2016-08-28
You could probably consider mdadm with webmin.  As long as you don't mind having a web interface running.

---

### Post by comi-guido on 2016-12-12
> **slimx3m said:**
> You could probably consider mdadm with webmin.  As long as you don't mind having a web interface running.

this is a solution for environments like servers;
personally I am actually using mdadm raid on my primary destkop machine, and this lack on gnome-disks made me finally learn to use mdadm via cli wich is the best way.
But a part this personal thoughts, i think that a valid gui tool, like was gnome-disks on ubuntu 14.04 fo example, should exist, on desktop machine i think that should be a must, I really hope that someone would invest in this.

---

### Post by mastablasta on 2016-12-13
RAID is mostly used on servers where you need high uptime. desktops are often turned off or suspended.

for servers there is CLi and also a couple of web guis available.

---

### Post by lwmeehan on 2017-07-21
> **mastablasta said:**
> RAID is mostly used on servers where you need high uptime. desktops are often turned off or suspended.

for servers there is CLi and also a couple of web guis available.

I expect high uptime for my desktop too!  It runs continuously.  It can receive mail and updates during the night and I can schedule other operation to occur while I'm sleeping.  Not everyone (especially linux users) are turning their desktops on and off all the time (laptops are a little different).  Even if I shut it down sometimes, why would I *not* want to have RAID?  It may start up a little more slowly, but it's not as if I have to rebuild the RAID each time I boot the system.

And why do you assume desktop users don't want to have RAID for their  valuable data?  I certainly do.  It's a lot simpler than messing with a backup device and rebuilding a failed drive from backup.  It's much simpler to just replace a drive.  Of course a RAID can be backed up for real disasters.

While learning mdadm, I once had the unfortunate experience once of trashing 2 TB of data.  Mdadm is not simple to learn and getting something wrong can be disastrous.  One has to learn way more than necessary in order to use mdadm safely.  There are options I'll never use, but to understand mdadm you have to understand them all.  You shouldn't have to know how everything works "under the hood" in order to do basic management.

So why not a simple GUI RAID manager for the normal operations?  It might encourage more people to use RAID and lose less data.  This omission in inexcusable.

I've managed unix and linux systems for decades.  It's time to make it easy to manage a system without being a systems manager.  *There is still way too much command line elitism in the linux community*.  The lack of easy-to-use GUIs is the main reason linux has not gained the wide acceptance it hoped for as a personal computer operating system.  If it's all about servers, why has so much development been put into fancy desktops?  The desktops don't give you real management tools yet they don't make them unnecessary either.  The right tools should should exist and they should be in the distribution.  Users shouldn't have to go hunting all over the internet to find things that should be there by default.

Webmin is pretty good, but the reason it exists is because linux doesn't have simpler ways to do a lot of things.  Not all users want to run a webserver on their desktop systems.

---

### Post by oldos2er on 2017-07-22
Back to sleep, old thread.

If you have further questions or problems, please start a new thread.

---

