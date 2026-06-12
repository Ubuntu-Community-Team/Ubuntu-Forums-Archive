---
title: "[SOLVED] Cant update..."
date: 2008-08-23
forum: New to Ubuntu
---

### Post by diplomat.x on 2008-08-23
I am unable to update my hardy heron 
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by Ryadt on 2008-08-23
> **diplomat.x said:**
> I am unable to update my hardy heron

Do```
sudo dpkg --configure -a
```

---

### Post by diplomat.x on 2008-08-23
> ABC@XYZ:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

now what?

---

### Post by eightmillion on 2008-08-23
Looks like your root drive is full. Could you post the output of **df -h** ?

---

### Post by livestockPimp on 2008-08-23
do you have any space left on the device?
what is the output of "df -h"

---

### Post by Ryadt on 2008-08-23
> **diplomat.x said:**
> now what?

What is the output of:```
df
```

---

### Post by diplomat.x on 2008-08-23
Here it is..

```
ABC@XYZ:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G  3.0G   16G  17% /
varrun               1009M  100K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M  204K 1009M   1% /dev/shm
lrm                  1009M   39M  970M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5              46M   41M  2.8M  94% /boot
/dev/sda8              31G   16G   14G  54% /home
gvfs-fuse-daemon       19G  3.0G   16G  17% /home/ABC/.gvfs
/dev/sda3              40G   33G  6.7G  84% /media/Planet M
/dev/sda4              30G   22G  6.8G  77% /media/disk
ABC@XYZ:~$ 

```

Thanks all for coming and helping me so quick...

---

### Post by Ryadt on 2008-08-23
The problem is that your /boot partition is way too small. The kernel is running out of space trying to install. You probably will have to repartition.

---

### Post by robert shearer on 2008-08-23
> **Ryadt said:**
> The problem is that your /boot partition is way too small. The kernel is running out of space trying to install. You probably will have to repartition.

Forgive me for asking but could there be more than one kernel image in boot from previous updates? and if the older kernel images were removed perhaps updates would then occour?

Agreed that the long term solution is a bigger boot partition.

---

### Post by diplomat.x on 2008-08-23
BTW, I might install ubuntu all over again tomorrow but whats the ideal size of /boot?

---

### Post by diplomat.x on 2008-08-24
> **diplomat.x said:**
> BTW, I might install ubuntu all over again tomorrow but whats the ideal size of /boot?

Anyone?? :confused:

---

### Post by mysticmatrix on 2008-08-24
I use 300 MB, as I have to use multiple OS.
One Ubuntu release takes up almost 100MB I guess, and if you reinstall every new release, 100MB would be enough.

BTW, you may also try to have only separate / and /home partition, if you reinstall anyway.( You have only used 3GB on your 16 GB / )

---

