---
title: "[SOLVED] Trying to load Kubuntu."
date: 2008-08-23
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-08-23
I am trying to load kubuntu on my second drive, but when I get to the disk partitioner I am not sure what to put down as root and /home.  Since I have a root and /home in ubuntu, How do I add the additional root and /home for kubuntu.  I tried loading it once and listed root and /home for both systems and it failed loading.
What am I doing wrong?

---

### Post by alienexplorers on 2008-08-23
come on people doesn't anyone have a answer to this simple question. BUMP

---

### Post by coffeecat on 2008-08-23
You're trying to install Kubuntu and you already have Ubuntu? Which version of Ubuntu? If it's 8.04 and you want Kubuntu 8.04, then there's an easier way. Just install 'kubuntu-desktop' in Ubuntu (using apt-get or Synaptic - whichever you prefer). Then, when you get to the login screen, just select gnome or kde from options.

I should imagine that no one responded because it's not quite clear what you are trying to do - apart from install Kubuntu. If you really do want a separate Kubuntu installation, post details of the two hard discs, where you want to put the Kubuntu root partition (you could share /home) and the output of

```
sudo fdisk -l
```

---

### Post by alienexplorers on 2008-08-23
I want to load Kubuntu seperate from Ubuntu.  I want it on partition sdb3.
I want to keep them seperate in order to compare one from the other to see which one I like.  The Kubuntu /home partition would be part of the root partition on SDb3 unless I cut down SDB2 and make another partition.
```
terminator@terminator-desktop:~$ sudo fdisk -l
[sudo] password for terminator: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006db91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dfa1df9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1661    13341951   83  Linux
/dev/sdb2            1662        3241    12691350   83  Linux
/dev/sdb3            3242        4821    12691350   83  Linux
/dev/sdb4            4822        4982     1293232+  82  Linux swap / Solaris

terminator@terminator-desktop:~$  df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              13G  3.1G  9.0G  26% /
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   60K  252M   1% /dev
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb3              13G  159M   12G   2% /backup
/dev/sdb2              13G  1.3G   11G  11% /home

```

---

### Post by coffeecat on 2008-08-23
OK, that's clear enough. When you get to the partitioning stage of the installer - I'm going from memory here - you choose the third option. I think it's called custom partitioning. The first one is pre-ticked and is guided. Can't remember what the second is. Anyway - the third one lets you direct the installer to partitions you have already set up. You tell it to use sdb3 as / and it will pick up sdb4=swap automatically. If you don't specify anything else it will put Kubuntu /home in your Kubuntu root partition. And you can also specify mountpoints for other partitions if you want to. You don't have to do anything with your Ubuntu partitions unless you want to specify mountpoints for them in Kubuntu. Just make sure they are not marked for reformatting.

I think that's it. It should be plain sailing after that.

---

### Post by alienexplorers on 2008-08-23
Thanks for the info.  It's been a long time since I ran 2 OS's from one disk and for the life of me could not remember th steps.

---

### Post by youthforlinux on 2008-08-23
Am i missing something here?

You know you could just use aptitude to install kubuntu-desktop and if you don't like it aptitude will basically completely remove kde and all its dependencies....I don't see why another ubuntu installation is needed....

---

### Post by tuxulin on 2008-08-23
@ youthforlinux
a comparison in its entirety was required, hence 2 OS

T

---

### Post by youthforlinux on 2008-08-23
ok...sounds good, sorry to doubt haha

---

