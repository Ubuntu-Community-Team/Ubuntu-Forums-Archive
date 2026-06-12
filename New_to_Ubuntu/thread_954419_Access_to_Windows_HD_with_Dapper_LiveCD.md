---
title: "Access to Windows HD with Dapper LiveCD?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by kuitems on 2008-10-21
I'm trying to help someone save a couple files from a failed Windows XP install using an Ubuntu LiveCD.  This version of Ubuntu is two years old (dapper) and I'm not quite sure how I would go about accessing the drive.

Searching the forums, I see the command 'gksu nautilus' might allow me to access the drive.  Will this work under Dapper?  I'm asking ahead because I won't have Internet access when I leave work.  

Does anyone have any advice on how to proceed?

---

### Post by louieb on 2008-10-21
The Dapper live CD doesn't  auto mount partitions on the hard drive.  

open a terminal window Applications>Accessories>terminal
Create a mount point
```
sudo mkdir /media/windows
```

find what the Linux name for his windows partitions is. also the file system type (ntfs or fat)  (lowercase L at the end)
```
sudo fdisk -l
```

mount the windows partition (example what you would enter may vary)
```
sudo mount -t ntfs /dev/hda1 /media/windows
```

now you can **gksudo nautilus **and navigate to /media/windows - the windows files should be there. 

Or just use [Puppy Linux]("http://www.puppylinux.com/") it about a 50-75MB dowload. Burn it to CD then boot and click on the drive icon. It will list the partitions on the drive. when you click on one the file manage will open showing whats in the partition.

---

