---
title: "Problem with disk space when downloading iso file"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by wjweder on 2008-06-03
I tried to download ubuntu 8.04 but it complains that I have insufficient space.   Don't know what to do, there is a 100 gig total space on disk but only using about 20 gig.  The download is automatically to the desk top. So how do I redirect the download or get more space for the desktop?  Obviously I don't know the file system well enough.

---

### Post by spiderbatdad on 2008-06-03
what platform are you using? Windows? MacOSX? Typically you can select a destination via browser settings.

---

### Post by wjweder on 2008-06-03
I am using Ubuntu to download the iso

---

### Post by Maestro23 on 2008-06-03
In terminal, run:

> df -h

Copy/Paste output here.

---

### Post by spiderbatdad on 2008-06-03
Well. that is odd. As you should have all free space available. Try this command to see what is taking all the space:```
sudo du -sh /*
```

---

### Post by wjweder on 2008-06-03
wjweder@wjweder-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             3.7G  3.5G   11M 100% /
varrun                722M  100K  722M   1% /var/run
varlock               722M     0  722M   0% /var/lock
procbususb            722M  112K  722M   1% /proc/bus/usb
udev                  722M  112K  722M   1% /dev
devshm                722M     0  722M   0% /dev/shm
lrm                   722M   39M  684M   6% /lib/modules/2.6.20-16-generic/volatile
/dev/hda3             5.4G  3.5G  1.7G  68% /media/disk
/dev/hda1              99G  6.8G   90G

---

### Post by spiderbatdad on 2008-06-03
looks like only a 3.7G partition...

---

### Post by wjweder on 2008-06-03
so what do i do about it.  Can  I icrease it?

---

### Post by wjweder on 2008-06-03
How do I increase the space?

---

### Post by hyper_ch on 2008-06-03
temporary filles will be stored in /tmp and that resides (normally) on the root partition. So when you make a home folder and you want to download some stuff or process some, you have to take that into consideration. Hence I recommend to make root at least 10 GB or more... I actually don't use a seperate home anymore. I see no need for it really.

It's also interesting that I don't see a hda2... there's hda1, hda3 and hda4....

You can try to resize it. Get the Desktop CD and boot it Ubuntu from it. Then you might need to install gparted (although I think it's on the desktop cd already) and then you can try to resize the drives. However before you attempt to do so, make a backup of the data.

---

