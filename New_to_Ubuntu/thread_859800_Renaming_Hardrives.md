---
title: "Renaming Hardrives"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-14
How do I rename my hard drives to a more user friendly tag? When I right click the drive and select rename, I get an error saying that the function is not supported by the backend.

---

### Post by iaculallad on 2008-07-14
> **Unotforme said:**
> How do I rename my hard drives to a more user friendly tag? When I right click the drive and select rename, I get an error saying that the function is not supported by the backend.

That would be the job of e2label terminal command.

i.e: 

```
sudo e2label /dev/sdb1 Music
```

---

### Post by kaibob on 2008-07-14
See the following document:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Despite the title, the procedures work with all drives.

---

### Post by Unotforme on 2008-07-15
Ok I ran e2label and checked my labels in terminal and they show the names I gave them:
larry@Home:/$ sudo umount /dev/sdb1
larry@Home:/$ sudo e2label /dev/sdb1
General
larry@Home:/$ sudo e2label /dev/sda1
Main

However, when I go to Places>Computer it shows the two drives as Filesystem and 40GB Media. I've tried rebooting, but the labels remain the old names (in Places>Computer).

---

### Post by iaculallad on 2008-07-15
> **Unotforme said:**
> Ok I ran e2label and checked my labels in terminal and they show the names I gave them:
larry@Home:/$ sudo umount /dev/sdb1
larry@Home:/$ sudo e2label /dev/sdb1
General
larry@Home:/$ sudo e2label /dev/sda1
Main

However, when I go to Places>Computer it shows the two drives as Filesystem and 40GB Media. I've tried rebooting, but the labels remain the old names (in Places>Computer).

Could you post whatever display when you issue the command below:

```
 sudo blkid
```

---

### Post by Unotforme on 2008-07-15
sudo blkid
/dev/sda1: UUID="c2db2906-8a57-434d-8896-7b23855ea825" TYPE="ext3" LABEL="Main" 
/dev/sda5: TYPE="swap" UUID="2828a4d5-7e34-4029-80a8-191a14b8dd77" 
/dev/sdb1: LABEL="General" UUID="20f084e8-599e-4e43-be7a-f070f8a0d231" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by iaculallad on 2008-07-15
It worked as shown by the blkid command, but not in your Places? Ooowwwss.. that would automatically work even without restarting :confused:

---

