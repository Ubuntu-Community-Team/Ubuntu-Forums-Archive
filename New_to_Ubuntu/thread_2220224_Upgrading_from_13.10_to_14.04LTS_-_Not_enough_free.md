---
title: "Upgrading from 13.10 to 14.04LTS - Not enough free disk space (PLS HELP A NEWBIE)"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by Russ_J on 2014-04-25
Recently moved on from XP to Ubuntu 13.10 and loving it - however a complete newbie!

Trying to upgrade from 13.10 to 14.04 LTS but get the following error message

[ATTACH=CONFIG]252507[/ATTACH]

Ubuntu is installed on partitioned 160GB on Samsung NC10 with 2GB ram (partitions are ~72GB each, D:/ is the partition with Ubuntu on and has a good deal of space).

[ATTACH=CONFIG]252505[/ATTACH]

Looking in disk usage it appears the Ubuntu disk appears to only be 7GB 


[ATTACH=CONFIG]252506[/ATTACH]

Is this the issue???

Please help me but you'll need to walk me through this as I'm learning (as I leave MS behind for ever hopefully)!!

Thanks 

russ

---

### Post by Ubi_one_2014 on 2014-04-25
as it says

empty your trash and remove old packages

---

### Post by Russ_J on 2014-04-25
I have!!

---

### Post by Ubi_one_2014 on 2014-04-25
pls open a terminal and type:
df [enter]

and copy the output here

---

### Post by Russ_J on 2014-04-25
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/loop0       6666380  5648976    655728  90% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1018012        8   1018004   1% /dev
tmpfs             205356     1096    204260   1% /run
none                5120        0      5120   0% /run/lock
none             1026780      500   1026280   1% /run/shm
none              102400       56    102344   1% /run/user
/dev/sda3       75496444 14443280  61053164  20% /host
/dev/sdb1       30741824       32  30741792   1% /media/russjeffers/SD 32GB
/dev/sdc        15633404    67036  15566368   1% /media/russjeffers/USB 16GB

---

### Post by Ubi_one_2014 on 2014-04-25
what shows:
dpkg -l | grep linux-image

---

### Post by Russ_J on 2014-04-25
ii  linux-image-3.11.0-12-generic             3.11.0-12.19                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-19-generic             3.11.0-19.33                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-20-generic             3.11.0-20.34                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-12-generic       3.11.0-12.19                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic       3.11.0-19.33                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-20-generic       3.11.0-20.34                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-generic                       3.11.0.20.21                            i386         Generic Linux kernel image

---

### Post by Ubi_one_2014 on 2014-04-25
i think that you are correct, and that the total amount of spce, dedicated to ubuntu, is 7Gb

when i press df , for myself, i get:
```
/dev/sda2              954750764  17296916   888932224   2% /
none                           4         0           4   0% /sys/fs/cgroup
udev                     2974760         4     2974756   1% /dev
tmpfs                     597812      1412      596400   1% /run
none                        5120         0        5120   0% /run/lock
none                     2989044       340     2988704   1% /run/shm
none                      102400        20      102380   1% /run/user
/dev/sda1                 497696      3428      494268   1% /boot/efi



```

in other words, the 1TB hd is totally used for ubuntu

are u able to recall the installation process of ubuntu 13.10?

---

### Post by Russ_J on 2014-04-25
I was advised to use to do it through Windows installation, the 160GB HD was always partitioned into 2 equal slices of ~72GB so I thought I'd installed onto the free 72GB D: partition

---

### Post by Ubi_one_2014 on 2014-04-25
i see

normaly, one has to boot from dvd, and follow up the recommended instructions from the installer

---

### Post by Russ_J on 2014-04-25
Samsung is Netbook with no CD/DVD drive, so was downloaded onto a USB stick and booted from there.

---

### Post by Russ_J on 2014-04-25
Sorry I mean installed from the USB onto the D partition

---

### Post by Russ_J on 2014-04-27
Hi,
 
I'd posted in the Installation & Upgrades forum and got some advice - [http://ubuntuforums.org/member.php?u=1919754](http://ubuntuforums.org/member.php?u=1919754)

I think I need to increase the size of my virtual disk but I'm completely lost.

Please can somebody advise.

Ta

Russ

---

### Post by bapoumba on 2014-04-27
Threads merged and moved to ABT.
Please do not start multiple threads on the same subject, it dilutes community efforts, thanks.

---

### Post by Ubi_one_2014 on 2014-04-27
> **Russ_J said:**
> Hi,
 
I'd posted in the Installation & Upgrades forum and got some advice - [http://ubuntuforums.org/member.php?u=1919754](http://ubuntuforums.org/member.php?u=1919754)

I think I need to increase the size of my virtual disk but I'm completely lost.

Please can somebody advise.

Ta

Russ

gparted can do that, but i am uncertain if all data will be lost or not

actually, i recommend to install ubuntu again, booting up from whatever medium .
delete all partitions, and let ubuntu decide what's recommended

pls note, if there are better answers , follow tjhm up first

---

### Post by Russ_J on 2014-04-27
Thanks for merging the posts bapoumba, I wasn't sure what I was to do Ubi_one_2014 so posted again thinking that was the end and maybe I should have put thus in the beginners section - sorry if I've broken the rules!!

Having already let Ubuntu decide during the last installation I'm slightly worried the same will happen again.

How is this done in gparted - again tried but to no success?

Ta
RJ

---

### Post by westie457 on 2014-04-27
Looking at your screen shots you have a WUBI installation: The /host is the tell.

You could give this a try. [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

If that fails then you will have to do a clean installation of ubuntu.

Before trying the suggestion though, move your personal files from ubuntu to somewhere safe. Just in case something goes wrong.

---

### Post by Russ_J on 2014-04-27
westie457
this my current set up - have looked a MigrateWubi

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/loop0       6666380  5270608   1034096  84% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1018012       12   1018000   1% /dev
tmpfs             205356     1092    204264   1% /run
none                5120        0      5120   0% /run/lock
none             1026780      540   1026240   1% /run/shm
none              102400       52    102348   1% /run/user
/dev/sda3       75496444 14443280  61053164  20% /host
/dev/sda2       74495092 66889232   7605860  90% /media/russjeffers/WIN XP 71GB



Can't quite work out what to insert
sudo bash wubi-move.sh [OPTION] target_partition [swap_partition]

---

### Post by Russ_J on 2014-04-27
Still stuck - have dowloaded MigrateWubi and have got the following

russjeffers@ubuntu:~$ sudo bash wubi-move.sh
[sudo] password for russjeffers: 
bash: wubi-move.sh: No such file or directory

---

