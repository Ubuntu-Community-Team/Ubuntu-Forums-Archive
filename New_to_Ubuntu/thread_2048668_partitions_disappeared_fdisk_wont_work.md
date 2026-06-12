---
title: "partitions disappeared fdisk wont work"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Splodg3 on 2012-08-27
Im having a problem with gParted because it shows that my whole hardrive is unallocated when in fact I can boot into ubuntu and linux mint i can also mount my linux mint, lubuntu and xp partitions from within Ubuntu. Ive been looking around and i haven't found anything that helps
I've tried 
```
sudo fdisk -l
``` 
and it says 
fdisk: unable to seek on /dev/sda: Invalid argument
I can still see the partitions uuid if i use blkid the blkid results are as follows 
```
/dev/sda2: LABEL="Windows XP" UUID="9CD8FCBED8FC982A" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="38c289c7-c009-4c8b-8885-172f00c984c0" TYPE="ext4" 
/dev/sda6: LABEL="Lubuntu" UUID="ab244b09-997c-4627-9d9f-5f301e910672" TYPE="ext4" 
/dev/sda7: LABEL="Linux Mint" UUID="2eea42c8-a878-44fb-9fe6-dd2c349f6c10" TYPE="ext4" 
```
Any help would be appreciated thanks :p

---

