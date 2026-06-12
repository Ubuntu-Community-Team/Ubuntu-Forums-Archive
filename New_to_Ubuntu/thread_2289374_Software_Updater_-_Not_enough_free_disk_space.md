---
title: "Software Updater - Not enough free disk space"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by UltimatePredator on 2015-08-03
Hi there,

I get this same error message whenever I try to update my system (lubuntu 15.04); Not enough free disk space.

 I have done some googling and installed bleachbit, ran it in root mode and normally. Initially it sorted the problem out, but I'm still getting the error message now even after running bleachbit. 

I'm aware that I can delete some stuff manually through the terminal, but would like some help on the matter please as I'm a bit of a newb with the terminal.

Many thanks in advance!

---

### Post by Vladlenin5000 on 2015-08-03
Do you have a separated /boot partition. You do if you used LVM/encryption. The default size the installer assigns to that partition is really small, so small that just a few kernel versions are enough to fill it up.
I don't use Bleachbit but it should give you an option to remove old kernels. And that's all you need. The updater is complaining about lack of space in that partition, nowhere else.

---

### Post by UltimatePredator on 2015-08-03
> **Vladlenin5000 said:**
> Do you have a separated /boot partition. You do if you used LVM/encryption. The default size the installer assigns to that partition is really small, so small that just a few kernel versions are enough to fill it up.
I don't use Bleachbit but it should give you an option to remove old kernels. And that's all you need. The updater is complaining about lack of space in that partition, nowhere else.

Hello there. I believe I do have a separated /boot partition, I opened the Disks program and there is a filesystem partition called Master Boot Record. It is indeed a small size; 255MB. 

I don't know if I use LVM/encryption though, how could I check?

Alas, bleachbit doesn't remove old kernels as far as I can see; [http://bleachbit.sourceforge.net/forum/old-kernels](http://bleachbit.sourceforge.net/forum/old-kernels)

Also, I've tried sudo apt-get autoclean and it didn't do the job :(

---

### Post by Vladlenin5000 on 2015-08-03
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

Says Lubuntu but the method is the same.

---

### Post by monkeybrain20122 on 2015-08-03
> **Ian_James_Yarnell said:**
> 
I don't know if I use LVM/encryption though, how could I check?


If you don't know then you are not. But why did you create a /boot partition?? Does the installer now create it by default? (I don't know as I always choose "something else" and do the partition  manually)

---

### Post by v3.xx on 2015-08-03
Please post the output of
```
df -h
```

---

### Post by UltimatePredator on 2015-08-04
> **Vladlenin5000 said:**
> [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

Says Lubuntu but the method is the same.

Thank you, off to work at the mo but bookmarked that for later (I am using lubuntu actually so thats grand!),

> **monkeybrain20122 said:**
> If you don't know then you are not. But  why did you create a /boot partition?? Does the installer now create it  by default? (I don't know as I always choose "something else" and do  the partition  manually)

I can't remember! I'm pretty sure it was automatic. I double checked Disks again and it does say Partition 1, Contents Ext2 (version 1.0) - Mounted at /boot.

> **v3.xx said:**
> Please post the output of
```
df -h
```

Ok, here it is;

Filesystem                    Size  Used Avail Use% Mounted on
udev                          740M     0  740M   0% /dev
tmpfs                         150M  5.0M  145M   4% /run
/dev/mapper/lubuntu--vg-root   35G  8.1G   26G  25% /
tmpfs                         750M   76K  750M   1% /dev/shm
tmpfs                         5.0M  4.0K  5.0M   1% /run/lock
tmpfs                         750M     0  750M   0% /sys/fs/cgroup
/dev/sda1                     236M  162M   62M  73% /boot
tmpfs                         150M   36K  150M   1% /run/user/1000

---

### Post by howefield on 2015-08-04
Does running... 

```
sudo apt-get autoremove
```

.. offer to remove any old kernels ?

---

### Post by UltimatePredator on 2015-08-04
> **howefield said:**
> Does running... 

```
sudo apt-get autoremove
```

.. offer to remove any old kernels ?

Alas, no:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.

---

### Post by UltimatePredator on 2015-08-04
I've been trying to delete soe of the older images as advised here; [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

But not having any luck, here is my readout for example;

uname -r
3.19.0-22-generic
ian:~$ dpkg -l | grep linux-image-
rc  linux-image-3.16.0-23-generic              3.16.0-23.31                               i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-3.16.0-31-generic              3.16.0-31.43                               i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-36-generic              3.16.0-36.48                               i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-15-generic              3.19.0-15.15                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-16-generic              3.19.0-16.16                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-18-generic              3.19.0-18.18                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-20-generic              3.19.0-20.20                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-21-generic              3.19.0-21.21                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-22-generic              3.19.0-22.22                               i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic        3.16.0-23.31                               i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-extra-3.16.0-31-generic        3.16.0-31.43                               i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-36-generic        3.16.0-36.48                               i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic        3.19.0-15.15                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-16-generic        3.19.0-16.16                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-18-generic        3.19.0-18.18                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic        3.19.0-20.20                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic        3.19.0-21.21                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic        3.19.0-22.22                               i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-generic                        3.19.0.22.21                               i386         Generic Linux kernel image
ian:~$ sudo apt-get autoremove linux-image-3.16.0-23-generic linux-image-extra-3.16.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-extra-3.16.0-23-generic' is not installed, so not removed
Package 'linux-image-3.16.0-23-generic' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.
ian:~$ sudo apt-get autoremove linux-image-3.16.0-31-gener
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.16.0-31-generic' for regex 'linux-image-3.16.0-31-gener'
Package 'linux-image-3.16.0-31-generic' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.

---

### Post by UltimatePredator on 2015-08-04
Fixed it, the advice on this thread is gold; [http://ubuntuforums.org/showthread.php?t=2240697](http://ubuntuforums.org/showthread.php?t=2240697)

I took the advice from the removeoldkernels page that was recommended ([https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)) and kept the most recent version as well as the most recent previous version.

sudo apt-get autoremove just doesn't work on my system at all. sudo apt-get -y purge does work!

---

### Post by ajgreeny on 2015-08-04
Great!

Please mark as solved from.the Thread Tools menu at the top.

---

### Post by UltimatePredator on 2015-08-05
> **ajgreeny said:**
> Great!

Please mark as solved from.the Thread Tools menu at the top.

Done! Thanks for the help people :)

---

