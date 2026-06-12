---
title: "Need Permission on my partition"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Zipolite on 2008-06-19
hello I'm Bran New To this but I'm a fast learner.
I am trying to gain permission to my own Partition but It won't let me I've looked everywhere but all the commands I try fail. it tells me invalid user please can anyone help? This is what I've been trying
zip@HAL:~$ sudo su
[sudo] password for zip: 
root@HAL:/home/zip# chown -R zip.zip/dev/sda1/media/disk *
chown: invalid user: `zip.zip/dev/sda1/media/disk'
root@HAL:/home/zip# chown -R zip.zip
chown: missing operand after `zip.zip'
Try `chown --help' for more information.
root@HAL:/home/zip# chown -R zip.zip /dev/sda1/media/disk *
chown: cannot access `/dev/sda1/media/disk': Not a directory
root@HAL:/home/zip# chown -R zip.zip /media/disk
chown: cannot access `/media/disk': No such file or directory
root@HAL:/home/zip#

---

### Post by alexandremrj on 2008-06-19
You don't have permission to your partiton or only for your filesystem?

Is your home only read only?


About the commands:

In the first command: chown -R zip.zip/dev/sda1/media/disk *

you have to place your username so the system will know wich user to atribute the partion - although if you are new to this i recommend going with care

---

### Post by Dedoimedo on 2008-06-19
Hello,

It should be zip:zip and not zip.zip.

Try sudo (or su) chown -R zip:zip <location>

Cheers,
Dedoimedo

---

### Post by sisco311 on 2008-06-19
fat, ntfs, or ext3?

---

### Post by Zipolite on 2008-06-19
Now it says not a directory
root@HAL:/home/zip# chown  -R zip:zip /dev/sda1/media/disk
chown: cannot access `/dev/sda1/media/disk': Not a directory
root@HAL:/home/zip# 

heres my fdisk info
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5774    46379623+  83  Linux
/dev/sda2           11581       12161     4666882+   5  Extended
/dev/sda3   *        5775       11580    46636695   83  Linux
/dev/sda5           11835       12161     2626596   82  Linux swap / Solaris
/dev/sda6           11581       11834     2040192   82  Linux swap / Solaris

Partition table entries are not in disk order
root@HAL:/home/zip#

---

### Post by sisco311 on 2008-06-19
> **Zipolite said:**
> Now it says not a directory
root@HAL:/home/zip# chown  -R zip:zip /dev/sda1/media/disk
chown: cannot access `/dev/sda1/media/disk': Not a directory
root@HAL:/home/zip# 

heres my fdisk info
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5774    46379623+  83  Linux
/dev/sda2           11581       12161     4666882+   5  Extended
/dev/sda3   *        5775       11580    46636695   83  Linux
/dev/sda5           11835       12161     2626596   82  Linux swap / Solaris
/dev/sda6           11581       11834     2040192   82  Linux swap / Solaris

Partition table entries are not in disk order
root@HAL:/home/zip#

assuming the partition is mounted in /media/disk and your username is zip:
```
sudo chown -R zip. /media/disk
```
or
```
sudo chown -R zip:zip /media/disk
```
or
```
sudo chown -R $USERNAME. /media/disk
```

---

### Post by cariboo on 2008-06-19
your not going to be able to change ownership of /media/disk but you can change permissions.

What is the output of /etc/mtab?

Here is a link to everything you want to know about fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Jim

---

### Post by ezramorris on 2008-06-19
[COLOR="Red"]Edit: [/COLOR]Deleted. Same as above.

---

### Post by Zipolite on 2008-06-19
Thank you very much sisco It was right infront of me the whole time
I own the partition now

---

