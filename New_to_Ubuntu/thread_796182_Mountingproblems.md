---
title: "Mountingproblems"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Helged on 2008-05-16
I've installed windows and unbunt on my computer.

When i try to mount my drive i get an error
"Cannot mount volume.
unable to mount the volume 'Ting'
Details:
mount_point cannot contain the following characters: newline, G_DIR SEPARATOR (usually /)"

How can i fix this, and how can i make them automount when i log in?

---

### Post by hermes0710 on 2008-05-16
can you post your /etc/fstab file and also which command do you use to mount the windows partition?

---

### Post by Helged on 2008-05-16
I rightclick the drive and selects mount volume..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ba88341d-050a-4ab2-b679-42b2530c955f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=9c9fa116-df72-4325-8caa-f41e932c02b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by hermes0710 on 2008-05-16
Open a terminal (Applications>Accessories>Terminal) and create a folder in /media in order to have windows mounted there
```
sudo mkdir /media/windows
```

Then try to mount the device:
```
sudo mount /dev/sda1 /media/windows
```

What error do you get and what is the filesystem (ntfs or fat) of the windows partition?

---

### Post by Helged on 2008-05-16
It seemd to work, but it was the wrong of my two windows partitions which was mounted.

How do i unmount it again, and how do i mount the second ntfs-partition?

Both partitions are NTFS

---

### Post by hermes0710 on 2008-05-16
To unmount use ```
sudo umount /dev/sda1
```

For each partition there is an entry in the /dev folder.
From your fstab file i see that /dev/sda2 and /dev/sda3 are you linux root and swap partitions accordingly. What other sda? entries are in that folder: [code]ls /dev/sd*[code]

---

### Post by Helged on 2008-05-16
Ok! Thanks. It was sda4.

But how can i make them automount at boot?

---

### Post by hermes0710 on 2008-05-16
You will need a new package (if you don't have it already) in order to gain write access on ntfs
```
sudo apt-get install ntfs-config
```

Then add in you /etc/fstab two entries for your partitions following the below template:
```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,user,uid=1000,locale=en_US.utf8   0    0
```

Before restarting you can test it by opening a terminal and executing ```
mount -a
```

---

### Post by Helged on 2008-05-16
Gedit gives me an error
I dont have the permissions necessary to save the file

---

### Post by hermes0710 on 2008-05-16
You must edit this file with root privileges which means:
   execute
```
sudo gedit /etc/fstab
``` 
from inside a terminal

---

### Post by Helged on 2008-05-16
It works!

Thanks a lot! :D

---

### Post by hermes0710 on 2008-05-16
Great :)

---

