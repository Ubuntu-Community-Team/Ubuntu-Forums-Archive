---
title: "Just installed Ubuntu on Chromebook Via ChrUbuntu"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by tamcphan94 on 2014-03-13
It asked me to pick amount of space Ubuntu will take up and I picked 10GB of my 16GB SSD. After my installation, the harddrive only showed that I have 800mb of SSD left. Why is that and why do I have such little amount of space left?

Chromebook: Acer C720 16GB SSD

---

### Post by ajgreeny on 2014-03-13
If you let the system install in the default manner without specifying separate partitions for root and swap, it is possible that a fair chunk of that 10GB was made into swap space.

From terminal in Ubuntu let's see the output of **sudo parted -l**

---

### Post by tamcphan94 on 2014-03-13
> **ajgreeny said:**
> If you let the system install in the default  manner without specifying separate partitions for root and swap, it is  possible that a fair chunk of that 10GB was made into swap space.

From terminal in Ubuntu let's see the output of **sudo parted -l**


Model: ATA KINGSTON SNS4151 (scsi)
Disk /dev/sda: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
11      32.8kB  8421kB  8389kB               RWFW
 9      8422kB  8423kB  512B                 reserved
10      8423kB  8423kB  512B                 reserved
 2      10.5MB  27.3MB  16.8MB               KERN-A
 4      27.3MB  44.0MB  16.8MB               KERN-B
 8      44.0MB  60.8MB  16.8MB  ext4         OEM         msftdata
12      128MB   145MB   16.8MB  fat16        EFI-SYSTEM  boot
 5      145MB   2292MB  2147MB  ext2         ROOT-B
 3      2292MB  4440MB  2147MB  ext2         ROOT-A
 1      4440MB  5243MB  803MB   ext4         STATE       msftdata
 6      5243MB  5260MB  16.8MB               KERN-C
 7      5260MB  16.0GB  10.7GB  ext4         ROOT-C

---

### Post by ajgreeny on 2014-03-13
Oh crikey, I had forgotten the complicated way Chrome-OS installs in all those separate partitions, and I'm afraid it is not the sort of output I had expected, which would have been more like shown below, though with extra partitions for the other OS (Chrome-OS) 
```
sudo parted -l
[sudo] password for user: 
Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  211MB   210MB   fat32           EFI System Partition  boot
 2      211MB   21.2GB  21.0GB  ext4
 4      21.2GB  992GB   970GB   ext4
 3      992GB   1000GB  8597MB  linux-swap(v1)

```However, you do not seem to have any swap space at all and I wonder if partition **7      5260MB  16.0GB  10.7GB  ext4         ROOT-C** is your Ubuntu; it is the only large ext4 filesystem which is the default for Ubuntu.

Perhaps you could also run **mount** from your ubuntu install which will give some idea of what is going on here.

---

### Post by tamcphan94 on 2014-03-13
not sure what you mean run mount, new to these terms. but I typed mount in terminal and got this 

/dev/sda7 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=user)
/dev/sda1 on /media/user/74d5b644-fd38-438c-85de-5bd58429240b type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda8 on /media/user/OEM type ext4 (rw,nosuid,nodev,uhelper=udisks2)

---

### Post by ajgreeny on 2014-03-13
Yes, that is what I meant, thank you for guessing correctly, and it does show that sda7 is the root partition of your Ubuntu.

That means that of your 10.7 GB available you have already used almost 10GB with the Ubuntu system, assuming that 800MB of space available is from your ubuntu and not just a general view of available space in the system's whole disk.
Have you installed a lot of large packages for games or similar in Ubuntu?  How many kernels have you now?

Let's now see the output of ```
df -hT in terminal
``` to see just how much of that 10.7GB is already used.

---

### Post by tamcphan94 on 2014-03-13
user@chrubuntu:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4      9.8G  4.3G  5.0G  47% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  929M  8.0K  929M   1% /dev
tmpfs          tmpfs     188M  1.2M  187M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     939M   80K  939M   1% /run/shm
none           tmpfs     100M   56K  100M   1% /run/user
/dev/sda1      ext4      738M   21M  664M   4% /media/user/74d5b644-fd38-438c-85de-5bd58429240b
/dev/sda8      ext4       12M   24K   12M   1% /media/user/OEM
user@chrubuntu:~$

---

### Post by ajgreeny on 2014-03-13
As you will see, you have 5GB available in your root partition, not 800MB.
Where did that figure come from?

---

### Post by tamcphan94 on 2014-03-13
> **ajgreeny said:**
> As you will see, you have 5GB available in your root partition, not 800MB.
Where did that figure come from?
In system setting details it shows disk = 0 bytes
In Files it shows 5 Devices
OEM
ROOT-A
ROOT-A
803 MB Volume
Computer

I'm unable to view the Root devices though
There is no device that shows 5GB left that's why I was surprised.

---

### Post by thenh813 on 2014-03-13
Maybe that is the amount of free space shown in Chrome OS.
I do not know anything about Chrome besides what I know about Linux.
then again I dislike Chrome in general though and testing it was enough for me.

---

### Post by thenh813 on 2014-03-13
You posted a second before I did, LOL.
Go to the / folder on Ubuntu, what does Nautilus say about free space in the bottom?

---

### Post by tamcphan94 on 2014-03-13
Alright thanks for you help, very appreciated!

---

### Post by thenh813 on 2014-03-13
Glad I could help you, please mark the thread solved via the Thread Tools at the top if you are finished.

---

