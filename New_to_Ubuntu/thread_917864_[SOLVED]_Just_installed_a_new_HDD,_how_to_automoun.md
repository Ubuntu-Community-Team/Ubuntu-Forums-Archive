---
title: "[SOLVED] Just installed a new HDD, how to automount?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by neurostu on 2008-09-12
I just installed two new SATA HDDs into my desktop computer. What do I need to do to get them to mount automatically to:  /home/username/data?

---

### Post by wolfen69 on 2008-09-12
what format are they?

---

### Post by neurostu on 2008-09-12
I just formatted them EXT3

---

### Post by wolfen69 on 2008-09-12
first you will need to find out if they are sda1, sdb2, etc...

do ```
sudo fdisk -l
``` to find out. then:
```
sudo mkdir /media/whatever_you_want_to_call_it
```do this for both drives.then: ```
gksudo gedit /etc/fstab
``` an example of the 2 lines to add to it would be: ```
/dev/sdxx   /media/name_you_called_the_drive  ext3   defaults  0 0
```replacing xx with whatever you got with fdisk -l. you will need to create an empty line at the end of fstab. click at the end of the last line and hit enter. save file and reboot. you may have permissions problems. post back if you do.

---

### Post by neurostu on 2008-09-12
What if I want the drives to be mounted under my home dir? could I change /media/name_of_drive to /home/username/driveMountDir?

---

### Post by wolfen69 on 2008-09-12
why you want them mounted in home i have no idea, but if so, you would need to: ```
sudo mkdir /home/your_name/name_you_want_for_drive
```

---

### Post by neurostu on 2008-09-16
I want to mount them under home b/c its easier for what I'm doing... it really doesn't matter were its mounted does it?

Also when I tried to write I got a permissions error so I used:
```

sudo chown username directory

```

---

### Post by neurostu on 2008-09-16
In the end I ended up mounting the drive under /media/data, then I ran:
```

ln -s /media/data data

```
from my home directory...

---

