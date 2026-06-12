---
title: "adding 2nd drive"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by Autodave on 2011-09-24
I have an Asus netbook with 2 SSDs.  One is a 4 gig and the other a 16 gig.  I have Ubuntu 11.4 installed and running on the 4 gig drive.  Now, I want to use the slower 16 gig drive for everything except the operating system.  How do I get it to mount automatically at boot up and get the OS to use it?

---

### Post by TeoBigusGeekus on 2011-09-24
Mount the 16gb disk and post us the output of
```
mount
sudo blkid
nano /etc/fstab
```
Don't forget to tell us which is the partition you want mounted upon startup.

---

### Post by ajgreeny on 2011-09-24
You could easily put your /home on a separate partition on that 16GB disk.

Make a new partition in the appropriate filesystem for an SSD (ext2?;  I'm not sure about that) then mount it and copy across your current /home/*username*.  You may now need to run the **chown** command on those newly copied files and folders ```
sudo chown -R *username*:*username* /path/to/new/home/*username*
```You will need to edit fstab with ```
gksudo gedit /etc/fstab
``` and the line added should be ```
UUID=*e2554df2-7e16-4864-97c9-834d8bebecda* /home           *ext2*    defaults        0       2
``` but of course use your own UUID and filesystem for the partition you have made.  Save the new fstab and run command ```
sudo mount -a
```which should mount everything in fstab, including your new home.

Once you are happy that all is OK you can remove all the files and folders from your old /home/username

---

