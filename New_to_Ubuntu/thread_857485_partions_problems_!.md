---
title: "partions problems !"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by JinkX on 2008-07-12
hey guys, 
i have a problem that has been there for ages and i had enough.
the problem is that when even i load my ubuntu it takes a really long time then sometimes it see my partions and some times dont, and i have to log in and out couple of times for it to work, and now i have a new problem that i cant run my partions and it says its unmounted for some reason .. 
what can i do now ? it has all my work, and i dont want to switch back to windows..

---

### Post by Bachstelze on 2008-07-12
Please paste the output of :

```
sudo fdisk -l
ls -l /dev/disk/by-uuid
cat /etc/fstab
```

---

### Post by JinkX on 2008-07-12
then ? some stuff came up and nothing seems wrong "zero errors" ..

---

### Post by Bachstelze on 2008-07-12
We need that "stuff" to help you. Please run those comands in a terminal and paste what they output.

---

### Post by miwaypet on 2008-07-12
What kind of partitions are you referring too. Are you speaking of a data partition such as /<data>, or the /home partition. I ask because it may be that the partition is not listed correctly in the uuid table.

---

### Post by JinkX on 2008-07-12
saad@saad-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda11
UUID=e8a818dd-e837-409a-b4ad-0a84949ff3c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda12
UUID=bd0c265c-9c50-4bcc-8c7e-8871ccfe2258 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by miwaypet on 2008-07-13
I have found a possible answer to you problem in the archives here: [http://ubuntuforums.org/archive/index.php/t-199587.html]("http://ubuntuforums.org/archive/index.php/t-199587.html").

Pay particular attention to the last entry.

Using live CD run fsck /dev/hda11.

---

