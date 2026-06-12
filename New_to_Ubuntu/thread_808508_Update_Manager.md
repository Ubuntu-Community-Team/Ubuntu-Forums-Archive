---
title: "Update Manager"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by AMZ on 2008-05-26
Hi,
I am looking for some help with get my update manager to work.I just upgraded for 7.10 to 8.04 via the update manger.I can see that there are updates to get but when I try to install them I get an error that tells me to 'dpkg --configure -a ' when I do this using sudo dpkg --configure -a it fails.

---

### Post by forestpixie on 2008-05-26
You're going to need to give the actual error message you get

---

### Post by AMZ on 2008-05-26
Sorry about that kinda new to forums but the error I get is.

E:dpkg was interupted, you must run dpkg --configure -a to correct this problem 

E:_cache->open()failed

Thanks for a quick response forestpixie hope you can help me.

---

### Post by ibutho on 2008-05-26
Try running Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by AMZ on 2008-05-27
Ibutho I ran dpkg --configure -a this is what I get.

 sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Any ideas?

---

### Post by hyper_ch on 2008-05-27
> 
gzip: stdout: No space left on device


What's your guess?

---

### Post by AMZ on 2008-05-27
how do I fix it I have plenty of room on my hard drive.I am only using 7% of a 160GB drive.

---

### Post by Monicker on 2008-05-27
> **AMZ said:**
> how do I fix it I have plenty of room on my hard drive.I am only using 7% of a 160GB drive.

show the output of these commands

```
df -h
sudo fdisk -l
```

---

### Post by AMZ on 2008-05-27
Thanks to everyone who helped me with this question but I think I am going to try a fresh install from a disk and see if that solves the problem.Thanks again for your input.:)

---

### Post by AMZ on 2008-05-28
I think I'm gonna scratch a new install.I was just a little frustrated.
here is the info you wanted to see.

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             144G   11G  129G   8% /
varrun                252M  220K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   48K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  215M  15% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1              46M   39M  4.4M  90% /boot
df: `/home/ad/.gvfs': Transport endpoint is not connected

sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076c2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  83  Linux
/dev/sda2               7       19033   152834377+  83  Linux
/dev/sda3           19094       19457     2923830   82  Linux swap / Solaris
/dev/sda4   *       19034       19093      481950   83  Linux

Partition table entries are not in disk order

This problem is a bit of a pain because it is on computer that I gave to a friend with 7.10.I am trying to convert him away from WINBLOWS.

---

### Post by hyper_ch on 2008-05-28
I guess this
```

/dev/sda1 46M 39M 4.4M 90% /boot

```
is the problem. Your boot partition just has 4.4 MB free disk space and I assume it's a kernel upgrade, so more than 4.4 MB are needed for that.

You still have plenty of diskspace left, so I'd suggest to enlarge the boot partition to maybe 100 MB

---

### Post by AMZ on 2008-06-06
thanks
 problem solved

---

