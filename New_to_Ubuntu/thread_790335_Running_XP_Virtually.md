---
title: "Running XP Virtually"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-05-11
I am using xubuntu 32 bit hardy heron.  I have read that some people run windows virtually rather than dual boot.  How do I do so?  I have a win XP disc.

---

### Post by SunnyRabbiera on 2008-05-11
well you can use a virtual machine software.
Me I use virtualbox to do what I need.

---

### Post by hikujk123 on 2008-05-11
I knew that, but where do I get it/how do I use it?

---

### Post by SIXAXIS on 2008-05-11
I've heard about QEMU (or something like that), but I haven't tried it and I don't know if it's any good. But I saw a video a while ago of them running Windows XP on a PS3 (that's the PPC version of Linux).

---

### Post by SunnyRabbiera on 2008-05-11
well you can get virtualbox here:
[the virtualbox site]("http://www.virtualbox.org/")

It should be easy to install and run, but it may need some extra configuring too...
I am unsure how it will react in xubuntu, as i use regular ubuntu

---

### Post by hyper_ch on 2008-05-11
just install virtualbox, add your user to the vbox group, create a new virtual machine, and then have the virtual amchine boot from cd-drive.

---

### Post by hikujk123 on 2008-05-11
look below

---

### Post by hikujk123 on 2008-05-11
How much space should I allow for xp? I mean in terms of hard drive. Will I be able to save to my ubuntu partition?
Would 7.5 G be enough?  If I can save to my linux partition, then I would like to keep it at the bare minimum xp needs.

---

### Post by hikujk123 on 2008-05-11
I getting this error:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

How do I fix this?

---

### Post by niteshifter on 2008-05-11
Hi,

There are two versions of VirtualBox, the open source (ose, available in the repositories) and the closed source. The difference between the two as it relates to most folks usage is USB capablility: None in ose, does support USB in the closed source. You can get the closed source via virtualbox.org, it will take you to Sun's site (Sun bought Innotek recently). The closed source is also a different license, it's not GPL, is for personal or evaluation use only. Commercial use is not allowed under the PUEL.

As to how much space you need: Vbox will ask for 10GB minimum for XP. However less can be used. I just redid my XP install for the retail version of XP SP2, it's disk usage was slightly more than 2GB. After "upgrading" (IE7 and SP3)* it was just below 5GB. So one could get by with as little as 4GB, but really, it's your call - it depends upon what you're going to do with XP.

Just so you'll know, just having an XP disk - like came with a computer (called an OEM disk) may not cut it. Technically it will work, but there's a EULA issue here, it has to be used on the machine it came with. That's between you and your conscience. Also, OEM versions are going to require activation, over the phone. This may or may not work.

You need to do this to get any version to work:
Go to Users and Groups
Go to the Groups list
Find vboxusers and your user to the group.

Or using the command line:
```
sudo adduser <user> vboxusers
```
Replace <user> with your user id.


There are two things you have to do to get the PUEL version to work:
**Make backup copies of these files first!**
Edit /etc/init.d/mountdevsubfs.sh
Edit /etc/fstab

See this [page]("https://help.ubuntu.com/community/VirtualBox") for what to do with mountdevsubfs.sh

Add this line at the end of your fstab:
```
#usbfs
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0

```
Change the number after devgid= to your vboxusers group id.
Reboot. USB devices will then work.


*Note: avoid SP3 upgrade if you can. If you want IE7 get it first, then get SP3. Depending upon the version of XP you have Automatic Update may be present and turned on, this caused me some grief. The basic install took 35 minutes, the next 3.5 hours was spent dealing with SP3 issues.

---

### Post by hikujk123 on 2008-05-11
I decided I'll dual boot instead.  I already created a virtual hard disk for xp by installing the virtual box .deb from the virtual box website.  How do I uninstall this package and delete the virtual hard disk?  I am new to linux and want to do things the easiest way possible.

---

### Post by dRock1286 on 2008-05-11
Go to File>Virtual Disk Manager...>Then release and remove the virtual disk. that frees up your space again...  :)

---

### Post by dRock1286 on 2008-05-11
I wish you would give virtualization a shot.  I think it is much easier than rebooting everytime I needed to do something else...

---

### Post by hikujk123 on 2008-05-11
Thanks.  I freed up the space but how do I uninstall virtual box?I decided I'll dual boot instead.  I already created a virtual hard disk for xp by installing the virtual box .deb from the virtual box website.  How do I uninstall this package and delete the virtual hard disk?  I am new to linux and want to do things the easiest way possible.

---

### Post by dRock1286 on 2008-05-11
Just go to sypnatic and search for virtualbox.  then click on the green box and choose complete removal.  that should rid your system of it.

---

### Post by hikujk123 on 2008-05-11
I didn't know debs showed up in synaptic.  Thanks.

---

