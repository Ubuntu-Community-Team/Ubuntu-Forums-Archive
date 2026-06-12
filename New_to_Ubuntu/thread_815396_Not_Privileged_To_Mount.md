---
title: "Not Privileged To Mount"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by primky on 2008-06-01
Everything worked fine two days ago. Today I started PC, and wanted to go to one of my Windows drives, but it says 

> 
Cannot mount volume.
You are not privileged to mount this volume.

I also can't write to USB key and stuff.

What should I do?

---

### Post by sayakb on 2008-06-01
```
sudo fdisk -l
```
Note down the /dev/sdax link of the NTFS/HPFS drive. Lets assume that it is sda1
Now do:
```
sudo mkdir /media/sda1
sudo mount -t /dev/sda1 /media/sda1
```

---

### Post by JoshuaRL on 2008-06-01
Try restarting the computer and see if that helps.  Have you done anything lately that seems connected, or any errors and problems that you can remember?

---

### Post by primky on 2008-06-01
JoshuaRL, everything worked fine before.
I also added disks to fstab
> /dev/sda1       /media/ntfs ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/sda5       /media/ntfs2 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

So it should automount at startup, like it did before.

I'll try now, what Mr. LinuxIsInnovation said.

---

### Post by primky on 2008-06-01
What LinuxIsInnovation said, didn't worked.

I tried instead this:
> sudo mount /dev/sda1 /media/ntfs -o force


And it worked. Great, the only concern now is, i have to do this everytime i reboot. Or could i add something new to /etc/fstab, to mount automatically?

---

