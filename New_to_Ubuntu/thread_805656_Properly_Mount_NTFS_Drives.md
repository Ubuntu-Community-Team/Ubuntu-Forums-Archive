---
title: "Properly Mount NTFS Drives?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-05-24
Hello, whenever I go to access one of my other drives, it seems to (I think) auto-mount and create an icon on the desktop. 
This is a problem for example when trying to select my music folder in my "storage" drive, it only sees my file system drive. Currently to fix this problem I made a link on the desktop, but its getting really annoying.

So how would I go about permanently mounting my NTFS drives.

Thanks!

---

### Post by ajmorris on 2008-05-24
hi there,
you can add the relevant options in /etc/fstab
Just mimic the entries already in there, but for your ntfs partition.
so you can add a new line that will have:

/dev/sda# (where # is the ntfs partition number) /media/ntfs (where ntfs is your ntfs mount point) ntfs-3g defaults 0 0

just dont add the stuff that i put in brackets. This will auto mount your ntfs partition whenever you log into ubuntu. However, for it to work, you must have ntfs-3g install, so just go ahead and sudo apt-get install ntfs3g
NOTE: The package for apt-get might be ntfs-3g, i cant remember, so if ntfs3g is not found, do sudo apt-get install ntfs-3g


AJ

---

### Post by Thee_Baron_ on 2008-05-24
How do I found out the number of the drive, I dont see it in drive properties.

Thanks

---

### Post by cdtech on 2008-05-24
You can use:
sudo fdisk -l

---

### Post by geo909 on 2008-05-24
A very nice tool if you don't want to mess up with fstab and configuration files is PYSDM (PYthon Storage Device Manager).
It's a graphical tool that you can install from synaptic and it lets you choose how you want to handle your other disks by just ticking boxes.
It's very easy to use.

After the installation I think you will find it somewhere under "system" menu, but I'm not sure, do search a little.

---

### Post by Thee_Baron_ on 2008-05-25
Thanks! geo909 it worked perfectly :)

---

