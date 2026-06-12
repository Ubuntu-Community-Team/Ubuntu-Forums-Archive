---
title: "Writting into hard disk"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by dhirajsuvarna on 2008-11-03
Hi everyone,

I have mounted my hard drives (E: and D:) using fstab file.
But now i am facing a problem,
I cannot write into the file, i do not have permission to do it.

I have tried chmod for changing the permission but it also shows "permission denied"

Please help.

---

### Post by taurus on 2008-11-03
How do you mount them from /etc/fstab and what type of filesystem are those drives/partitions?

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by dhirajsuvarna on 2008-11-03
I do not have net connection in my PC.
but i will surely post the output.

Actually i have added some line in fstab file, so that the hard drives get mounted as a when my ubuntu boots.

is there any othere way to do the same?
Also plese help in the above mentioned problem of permissions to write in the hard disk.

---

### Post by taurus on 2008-11-03
What filesystems are those drives/partitions?

---

### Post by dhirajsuvarna on 2008-11-04
What difference does it make ?

Anyways 
C dirve is NTFS
D drive is FAT32
E drive is FAT32

ext and swap are partitioned in the D drive

---

### Post by cariboo on 2008-11-04
Drive letters mean nothing in Linux, to help you better we need the device numbers Linux gives hard drives and partitons:

```
/dev/sda1
```

in the above case the device number is the first partiton of the first hard drive. 

Could you paste a copy of your /etc/fstab in your next post. If you are dual booting use the following command:

```
sudo cp /etc/fstab /dev/sda1/dirname
```

where /dev/sda1/dirname is a directory on your C drive.

Jim

---

### Post by taurus on 2008-11-04
> **dhirajsuvarna said:**
> What difference does it make ?

Anyways 
C dirve is NTFS
D drive is FAT32
E drive is FAT32

ext and swap are partitioned in the D drive

Big difference since chmod/chown won't work for ntfs or fat32.  For others to help you better, you should post the outputs of those commands unless you want to figure everything out yourself.

---

