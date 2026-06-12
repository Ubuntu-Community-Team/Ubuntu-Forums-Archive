---
title: "Help me reformat my USB key"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by The Jinx on 2008-05-21
Hi,

I was trying to play around with Live USB Persistent and I loaded a copy of Hardy Heron onto my 2gb Kingston DataTraveler. I followed all the instructions i found on [www.pendrivelinux.com](www.pendrivelinux.com) [[COLOR="Red"][http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/")[/COLOR]] i couldn't really get it up and running so i decided to go back to windows to format the drive. I noticed that after my format i was only left with 715mb.

I know this has to do with the formating of the USB key and partitions but i do not know how to get back my full 2gb worth of space.

Thanks,
Jinx

---

### Post by quelx on 2008-05-21
in Windows, Right click **My Computer**
then **Manage**
Click **Disk Management**
locate your pendrive in the list and delete (right click > **Delete Volume**) the partitions and create a new partition with whatever format you wish

---

### Post by seetho on 2008-05-21
I put an executable script in ~/bin directory and run it to format my usb thumbdrives.  I notice that some of my cheaper ones gets corrupted by WinXP occasionally.  The ones from Kingston are more expensive but so far trouble free.

```
#!/bin/bash

# format usb thumbdrive

sudo umount /dev/sdb1
sudo mkdosfs -F 32 -n seetho /dev/sdb1

```

seetho is the volume name I give to my drives when I format them and /dev/sdb1 is where my thumbdrives are mounted.  You should check yours first.

---

### Post by The Jinx on 2008-05-22
Ahhh I thank thee for thine assistance

---

