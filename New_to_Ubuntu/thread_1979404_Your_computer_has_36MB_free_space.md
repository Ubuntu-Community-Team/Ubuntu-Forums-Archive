---
title: "Your computer has 36MB free space"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by YOHAN55 on 2012-05-13
Hi,

I am new to Linux, just installed it. I am using windows 7, and I installed Ubuntu 10.10 inside windows ( When you insert the cd while you are in windows, there is an option called "Inside Windows"). Anyway, I installed it inside a seperate pertition of 100GB. Now, after installing it, I booted into Ubuntu, upgraded it to version 11.04, and installed Netbeans IDE. However, now ubuntu is giving me the following error message

"Your computer has 36MB free space"

I have 91GB left in the partition where I installed this OS, but why it is giving this error? Please help me to get rid of this issue, and please note I am very new to Ubuntu


Thanks

---

### Post by CatKiller on 2012-05-13
```
 gksudo baobab
``` should let you see where the space is being used.

---

### Post by Old_Grey_Wolf on 2012-05-13
Unless WUBI has changed, it doesn't make a partition larger that 32GB. It also doesn't use a partition that you create outside of the Windows partition.

---

### Post by oldfred on 2012-05-13
As Old_Gray_Wolf says wubi is just a file inside the NTFS Windows partition and has limits. It is intended as a longer test for Windows users than a liveCD and it allows updates. But it is not intended for long term use.

Even the designer of wubi expects you to convert to a full partitioned install if you like Ubuntu.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by jerome1232 on 2012-05-13
Also the output of these can be helpful if your unsure about what your looking at in baobob. Press crtl+alt+t to bring up a terminal, then type these in. When you post their out put, please wrap it in code tags by going into advanced mode and pressing the # symbol on your toolbar.


```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by YOHAN55 on 2012-05-14
Thanks for all of your replies. Here is the output for the above code


```
yohan@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            4.6G  4.2G  144M  97% /
none                  932M  744K  932M   1% /dev
none                  939M  1.4M  938M   1% /dev/shm
none                  939M   88K  939M   1% /var/run
none                  939M     0  939M   0% /var/lock
/dev/sda5              98G  5.7G   93G   6% /host
yohan@ubuntu:~$ sudo du -hx --max-depth=1 /
[sudo] password for yohan: 
249M    /lib
14M    /etc
4.0K    /opt
64K    /tmp
4.0K    /host
4.0K    /selinux

```

I am glad to use the complete partition dedicated for ubuntu. Which means, Now I don't want to keep it as an install/uninstall program, I need to use it as another OS. Going to try the advices posted in [here]("http://ubuntuforums.org/showthread.php?t=1519354") as mentioned by another user. Please help me!

---

### Post by YOHAN55 on 2012-05-14
No, I don't know how to do it correctly, Please help

---

### Post by jerome1232 on 2012-05-14
Okay, you/the installer only gave wubi 4.6 GB's, no wonder it filled up! I would do as others recommended and migrate to a full install.

---

### Post by YOHAN55 on 2012-05-14
I tried the following, but as you can see, it failed



```
yohan@ubuntu://home/yohan/Downloads/wubi-move-2.2$ sudo bash wubi-move-2.2.sh /dev/sda5 
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  Source for migration validated successfully:
wubi-move-2.2.sh:    Wubi host partition: /dev/sda5
wubi-move-2.2.sh:    Size of install: 4397456 K
wubi-move-2.2.sh:    Size of /boot: 42052 K
wubi-move-2.2.sh:    Size of /usr: 2732860 K
wubi-move-2.2.sh:    Size of /home: 107448 K
wubi-move-2.2.sh:  Validating migration target(s)...
wubi-move-2.2.sh:  /dev/sda5 is mounted - please unmount and try again
wubi-move-2.2.sh:  partition /dev/sda5 must be type 83 - Linux.
wubi-move-2.2.sh:  Validation of target(s) failed

wubi-move-2.2.sh:  Migration did not complete successfully.
yohan@ubuntu://home/yohan/Downloads/wubi-move-2.2$ ^C
yohan@ubuntu://home/yohan/Downloads/wubi-move-2.2$ 
```

---

### Post by YOHAN55 on 2012-05-14
I might have misunderstood the partitions! Please help!

---

### Post by mastablasta on 2012-05-14
unless you have any sensitive data in the wubi it is far more easier to uninstall it and do a new side by side install.
with pics...
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
 
plenty in install is then done automaticly (such as swap partition and similar)
 
the important thing here is that you create empty disk space (unformated disk) and then select that part to install the OS to. the easiest way is to delete the partition with windows disk manager (!deleting partition will destroy all data there!)
the install process will then format that part appropriatelly to your file system choice (or you can use default ext4 filetype).
 
there are also osme nice tutorial fo rhtis ofund on youtube if you like video more...

---

### Post by oldfred on 2012-05-14
I am  not familiar with script but I think it needs you to create the Linux / (root) partition and swap in advance with gparted. Linux partitions cannot be NTFS format as that is Windows but ext4  (or actually many others).

errors you posted from script:
 > wubi-move-2.2.sh:  /dev/sda5 is mounted - please unmount and try again
wubi-move-2.2.sh:  partition /dev/sda5 must be type 83 - Linux.

You can only use gparted from liveCD not wubi to create partitions. Do not use Windows to create partitions as it cannot create Linux formated partitions and may try to convert to dynamic which does not work with Linux at all.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by subhadip_sky on 2012-05-14
If you are going to dedicate the whole partition to Ubuntu, then you actually don't need to use Gparted. The live installation CD will give you the option to format the partition as EXT4 form whatever format it is currently in. Even if you want to create two partitions out of the whole 100 gb partition, you can do so without using the Gparted.
By the way, why do you want to use 10.10 as it is not supported for Desktops anymore. Choose a version that is still supported.

---

### Post by bcbc on 2012-05-14
As oldfred pointed out, you need to create the target partitions before migrating. You attempted to migrate to the same partition that you installed Wubi on (/dev/sda5) which isn't possible (part of the migration is to format the target partition prior to copying)

If you've only just installed (not done much on Ubuntu) then it's really easier to just install fresh. Migration is only if you've customized it, installed a bunch of programs and don't want to redo the work.

> yohan@ubuntu://home/yohan/Downloads/wubi-move-2.2$ sudo bash wubi-move-2.2.sh /dev/sda5 
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  Source for migration validated successfully:
wubi-move-2.2.sh:    **[COLOR="Red"]Wubi host partition: /dev/sda5[/COLOR]**
wubi-move-2.2.sh:    Size of install: 4397456 K
wubi-move-2.2.sh:    Size of /boot: 42052 K
wubi-move-2.2.sh:    Size of /usr: 2732860 K
wubi-move-2.2.sh:    Size of /home: 107448 K
wubi-move-2.2.sh:  Validating migration target(s)...
wubi-move-2.2.sh:  [COLOR="red"]**/dev/sda5**[/COLOR] is mounted - please unmount and try again
wubi-move-2.2.sh:  partition **[COLOR="red"]/dev/sda5[/COLOR]** must be type 83 - Linux.
wubi-move-2.2.sh:  Validation of target(s) failed

---

### Post by migs73 on 2012-05-14
Ooops ignore me please

---

### Post by YOHAN55 on 2012-05-15
Thanks for all of your help. I uninstalled it and installed the latest version as a dual boot :)

---

