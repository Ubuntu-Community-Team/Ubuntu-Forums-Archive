---
title: "/data How to Change directory permissions?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Soriano on 2008-11-14
Hi all!  I'm new to linux and ubuntu and am so far enjoying it alot.  I decided to reinstall ubuntu the other day to seperate /home partition and create /boot etc.

My laptop has two Hard Drives. One 120 GB and one 80GB.  I put everything like /boot, /, swap and /home etc on teh 80GB drive.  Now the 120 GB drive I made a partition called /data.  I figured that is where I would put all my pics and files (Looking back i should have made it /home).  But anyhow my issue is that i can't seem to put anything on /data since its permissions are for root.  

I was trying to figure out how I can change the directory permissions so that any 'user' on my system can put files onto this drive.  So the directory needs these permissions and I want those permissions to apply to every file in that directory (not sure if that is possible).

The other option would be to delete that partition and extend my /home into that drive.  I would almost rather this but again am unsure how to do this.

Any Help much appreciated!

Thanks!

---

### Post by MasterSander on 2008-11-14
please post the ouput of
```
 cat /etc/fstab 
```

---

### Post by Soriano on 2008-11-14
```
matthew@hpdv9000:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6bde31e4-24c4-47e2-9371-2c788dad126e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=173c4d91-3427-4180-9c1a-2eefcce88111 /boot           ext3    relatime        0       2
# /dev/sda1
UUID=a0b95ccb-f459-4b11-b05e-936de3bad5bf /data           ext3    relatime        0       2
# /dev/sdb7
UUID=506ed75f-f3f9-4c57-ae11-157063297efe /home           ext3    relatime        0       2
# /dev/sdb5
UUID=0d0d353e-bf87-4cfd-b8c9-84c9b6f56673 /tmp            ext3    relatime        0       2
# /dev/sdb6
UUID=82810809-9a80-4420-ade8-24bdeeb1f000 /usr            ext3    relatime        0       2
# /dev/sdb3
UUID=ec705aa5-2e50-4bef-ac3a-3494dc3550f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
matthew@hpdv9000:~$ 

```

---

### Post by Soriano on 2008-11-14
I have been trying to use chmod but am not having luck so I am guessing that I don't know something about directory permissions.  I think that if I could somehow extend my home partition onto this drive and remove the /data partition that would be best.

---

### Post by philinux on 2008-11-14
To be honest since this is clean install I would do this.

Reinstall ubuntu to disk 1 the smallest and with only 
/ 10 gig
/home whatever
/swap (mines 4 gig , 2 x mem) less is fine

At the same time
disk 2  /data

This will take about 30 mins

---

### Post by MasterSander on 2008-11-14
change UUID=a0b95ccb-f459-4b11-b05e-936de3bad5bf /data           ext3    relatime        0       2

to this

UUID=a0b95ccb-f459-4b11-b05e-936de3bad5bf /data           ext3    defaults        0       2

make sure the directory /data exists, sudo mkdir /data

---

### Post by bodhi.zazen on 2008-11-14
> **Soriano said:**
> Hi all!  I'm new to linux and ubuntu and am so far enjoying it alot.  I decided to reinstall ubuntu the other day to seperate /home partition and create /boot etc.

My laptop has two Hard Drives. One 120 GB and one 80GB.  I put everything like /boot, /, swap and /home etc on teh 80GB drive.  Now the 120 GB drive I made a partition called /data.  I figured that is where I would put all my pics and files (Looking back i should have made it /home).  But anyhow my issue is that i can't seem to put anything on /data since its permissions are for root.  

I was trying to figure out how I can change the directory permissions so that any 'user' on my system can put files onto this drive.  So the directory needs these permissions and I want those permissions to apply to every file in that directory (not sure if that is possible).

The other option would be to delete that partition and extend my /home into that drive.  I would almost rather this but again am unsure how to do this.

Any Help much appreciated!

Thanks!

```
sudo chown root.users /data
sudo chmod 770 /data
```

---

### Post by Soriano on 2008-11-16
Thank you all for your reply's.  This worked perfectly!

```
sudo chown root.matthew /data
sudo chmod 770 /data
```

Thanks!

---

