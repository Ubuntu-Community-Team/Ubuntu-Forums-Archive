---
title: "Ubuntu Main Drive Read-only"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by bockee on 2012-04-12
i installed ubuntu a few days back, but one of the  partition  is like read only. I cant create anything in the drive nor can i move files into it. Help please?

---

### Post by jerrrys on 2012-04-12
so you can boot to desktop?

open a terminal and enter:

sudo apt-get update && sudo apt-get upgrade

any errors?

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by bockee on 2012-04-12
> **jerrrys said:**
> so you can boot to desktop?

open a terminal and enter:

sudo apt-get update && sudo apt-get upgrade

any errors?

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)


It's downloading an update? 
It didn't show any error.
What exactly my problem is , is that while installing I created two partitions. The logical one is the one which isnt accessible right now. The mount point of the drive is /swap and its ext3.

---

### Post by jerrrys on 2012-04-12
in terminal enter:

df

what you get?

---

### Post by bockee on 2012-04-12
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             13682440   2556844  10430556  20% /
none                    504392       272    504120   1% /dev
none                    508612       428    508184   1% /dev/shm
none                    508612        92    508520   1% /var/run
none                    508612         0    508612   0% /var/lock
none                    508612         0    508612   0% /lib/init/rw
/dev/sda6             23810200    176196  22424508   1% /swap

---

### Post by jerrrys on 2012-04-12
also looks good.  Is there another partition?

---

### Post by bockee on 2012-04-12
Nope. Only 999mb of Swap space

---

### Post by jerrrys on 2012-04-12
which partition do you see as read only?

---

### Post by oldfred on 2012-04-12
Swap is not a formated partition that you use, but space for RAM overflow. It looks like you created a partition called /swap, formated it and mounted it. That may confuse system.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Usually best for new users just to have a separate /home, but you can have a data partition. You do not have to call it data, but do not call it swap to avoid confusion. It can be music, video, shared, photo or any name you like. 

umount /swap
sudo mkdir /mnt/data
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda6 /mnt/data
#where sda6 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

You would have to manully mount everytime you rebooted, but you can add an entry to fstab to auto mount every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jerrrys on 2012-04-12
hi oldfred, thanks :)

---

### Post by bockee on 2012-04-12
> **oldfred said:**
> Swap is not a formated partition that you use, but space for RAM overflow. It looks like you created a partition called /swap, formated it and mounted it. That may confuse system.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Usually best for new users just to have a separate /home, but you can have a data partition. You do not have to call it data, but do not call it swap to avoid confusion. It can be music, video, shared, photo or any name you like. 

umount /swap
sudo mkdir /mnt/data
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda6 /mnt/data
#where sda6 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

You would have to manully mount everytime you rebooted, but you can add an entry to fstab to auto mount every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
Okay, So I need to use the code above in the terminal? And thats it? 
Sorry about the question cause I'm new to Ubuntu and trying to learn the commands :)

---

### Post by bockee on 2012-04-12
> **oldfred said:**
> Swap is not a formated partition that you use, but space for RAM overflow. It looks like you created a partition called /swap, formated it and mounted it. That may confuse system.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Usually best for new users just to have a separate /home, but you can have a data partition. You do not have to call it data, but do not call it swap to avoid confusion. It can be music, video, shared, photo or any name you like. 

umount /swap
sudo mkdir /mnt/data
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda6 /mnt/data
#where sda6 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

You would have to manully mount everytime you rebooted, but you can add an entry to fstab to auto mount every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)



Okay, So I need to use the code above in the terminal? And thats it? 
Sorry about the question cause I'm new to Ubuntu and trying to learn the  commands :smile:

---

### Post by jerrrys on 2012-04-12
oldfred is telling you if your trying to mount a swap partition and use it; this will not work.  If you want a partition to store data, you got to make one.

---

### Post by bockee on 2012-04-12
> **jerrrys said:**
> oldfred is telling you if your trying to mount a swap partition and use it; this will not work.  If you want a partition to store data, you got to make one.

Okay, While creating the partitions during Installation, there was an error which said "No root file defined" .
So a quick google search landed me with the mount labels.They said for the primary drive, use "/"
and for the logical drive use /swap .
So , If I were to reinstall again, what would I have to use?

---

### Post by jerrrys on 2012-04-12
if you install again, just follow the on screen instructions.  No need to complicate things until you understand linux better.

---

### Post by bockee on 2012-04-12
I did try doing that, but it still said No root file defined. It needed some mount point, What can i use just for it to get normal?

---

### Post by jerrrys on 2012-04-12
If you want to start over, use gparted to delete ALL ubuntu partitions. Gparted is on the live CD.  If you have windows installed, you must reinstall ubuntu before windows will boot.

---

### Post by bockee on 2012-04-12
Okay. Thanks a lot! :)

---

### Post by jerrrys on 2012-04-12
let us know what happens :)

---

### Post by oldfred on 2012-04-12
Subtle difference swap and /swap. The swap partition is for RAM overflow. Any other partition you create is formated and has a mount point like off / (root) or /media etc.

I normally partition in advance, so I do not use installer to partition, but it only used to let you create the standard system partitions, but now must let you create others.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by SeijiSensei on 2012-04-12
Isn't the problem here simply that / is mounted read-only as happens when it has filesystem errors?

bockee, run the command "mount" from the command line and see if the entry for /dev/sda1 says it's read-only.  If so, you should see an entry like this:

```
/dev/sda1 on / type ext4 (ro)
```

If it says (ro) and not (rw), then the root filesystem has been marked read-only by the OS.  To fix the problem reboot and choose the "recovery mode" kernel from the list offered at bootup, then choose the "root shell" option when it is offered.  At the "#" prompt enter these commands:

```

mount -o remount,rw -n /
touch /forcefsck
shutdown -r now

```

Note there's no space in "remount,rw".  Don't do anything else to the system until it reboots.  It will run a filesystem check at startup and fix any problems it finds.

If you don't see a list of alternate kernels at boot, hold down the shift key while booting.

---

### Post by bockee on 2012-04-13
Thank you! Did what you told and Voila! Works awesome! :)

---

