---
title: "Can't backup file from 12.10 installation from Live CD."
date: 2013-06-13
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-06-13
Hello all,
After running into some issues lastnight/this morning, I've got about everything squared away except for this last problem.

I have one specific folder that is located within the home folder of my 12.10 installation that I need to backup. I cannot access my 12.10 installation directly, so I have been using a 12.04 Live CD t mount the SDA and backup the files.

I originally mounted the SDA and backed up the files with:
```
cd  
mkdir mnt  
sudo mount /dev/sda1 mnt
```

Everything was going good until I ran into a folder called "My Stuffs" that has a few important documents in it. It's located in the same location as every other file I backed up, however, I cannot view the conents of this folder or modify/backup in any way. 

I tried running:
```
gksudo nautilus
```

But when I ran the above, it only showed the content of the Live CD, and nothing from my hard-drive.

I'm just looking to be able to back this one folder up. I cannot see it within Nautilus, and within the default file browser it says I do not have permissions to access or move it. Any help is greatly appreciated.

---

### Post by grahammechanical on 2013-06-13
Does the standard Nautilus in the live session see the hard disk and the partitions on it? If so open that partition and then launch Nautilus using gksudo. You might then find that the hard disk and the partition show up in the left panel.

I get that situation when I use gksudo nautilus in Ubuntu. It is only when I use standard Nautilus to open the partitions on the hard disk that they show up in gksudo nautilus and I can access them.

Another point that you might keep in mind. When you come to access those files again you might find that root has become the owner. So, you might need to use gksudo nautilus to give ownership/permission to other users. I have this problem when using gksudo nautilus to move files (for putting them in a safe place)  to other partitions.

Regards.

---

