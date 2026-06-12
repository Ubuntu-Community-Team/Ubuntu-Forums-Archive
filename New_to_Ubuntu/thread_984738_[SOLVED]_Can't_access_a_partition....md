---
title: "[SOLVED] Can't access a partition..."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by dj620129 on 2008-11-16
Hi all,

I am new to Ubuntu. In fact, I am new to Linux in general.

Before installing Ubuntu, my PC's 100GB HD was partitioned as follows under Windows:
Drive C: (about 20GB)
Drive D: (about 40GB)
Drive E: (about 40GB)
Unused area: (about 3GB)
No need to say, Drive D, E and unused area are were in extended partitions under Windows or DOS, whichever is correct.

Then, I wanted to try Ubuntu so I moved whatever was in Drive E: to Drive D: and to my external USB HDD to empty the Drive E.
Then using Ubuntu Live USB, I installed Ubuntu 8.10 on Drive E.
So Ubuntu is on /dev/sda5.
After using it for a few days, I found it very very good, and started to copy my files from work to relevant directories under my home directory. Since I was getting short on free space, I moved all the files in Drive D to my external USB HDD and created an ext3 type partition. Linux recognizes it as /dev/sda7 since /dev/sda6 is my swap partition.

Now the problem!!!
I can mount sda7. It mounts automatically booting and I can also umount and mount sda7 without any problem. However, I cannot access it. I cannot create a folder, move or copy a file into it.
I mount it as follows:
    sudo mount -t ext3 /dev/sda7 /media/work
Of course the directory /media/work is created. I created it under /media because Ubuntu seems to mount all drives and stuff in /media.

Can anyone help me to be able to use my /dev/sda7 partition? Otherwise I won't have enough space and I will have to start deleting files from my /dev/sda5 partition.

Thanks in advance.

---

### Post by handydan918 on 2008-11-16
Most likely an ownership issue. To change ownership of (for example) /dev/sda5 you could ```
sudo chown -R <username> /dev/sda5
```

You can also edit /etc/fstab to automatically mount the partition at boot. I feel certain that you can find how to do that on your own.

---

### Post by dj620129 on 2008-11-17
> **handydan918 said:**
> Most likely an ownership issue. To change ownership of (for example) /dev/sda5 you could ```
sudo chown -R <username> /dev/sda5
```

You can also edit /etc/fstab to automatically mount the partition at boot. I feel certain that you can find how to do that on your own.

I ran ls -l /dev/sda* and got the following:
brw-rw---- 1 root disk 8, 0 2008-11-17 17:30 sda
brw-rw---- 1 root disk 8, 1 2008-11-17 17:30 sda1
brw-rw---- 1 root disk 8, 2 2008-11-17 17:30 sda2
brw-rw---- 1 root disk 8, 5 2008-11-17 17:30 sda5
brw-rw---- 1 root disk 8, 6 2008-11-17 17:30 sda6
brw-rw---- 1 root disk 8, 7 2008-11-17 09:30 sda7

Maybe I am wrong but it does not seem to an ownership issue since sda7 and sda5 both have same permission and ownership.

---

### Post by handydan918 on 2008-11-17
> I mount it as follows:
sudo mount -t ext3 /dev/sda7 /media/work

Right. Notice the "sudo", indicating that YOU can't mount it because YOU don't own it. Much like the output you posted, indicating some guy named "root" as owner. He probably doesn't even have a password.
Old Unix maxim says, "If you can't open it, you don't own it."

chown allows you to own it.

---

### Post by dj620129 on 2008-11-17
OK, I changed ownership.

brw-rw---- 1 root  disk 8, 0 2008-11-17 17:30 sda
brw-rw---- 1 root  disk 8, 1 2008-11-17 17:30 sda1
brw-rw---- 1 root  disk 8, 2 2008-11-17 17:30 sda2
brw-rw---- 1 root  disk 8, 5 2008-11-17 17:30 sda5
brw-rw---- 1 root  disk 8, 6 2008-11-17 17:30 sda6
brw-rw---- 1 david disk 8, 7 2008-11-17 09:30 sda7

Then I remounted sda7. 

By the way, this is my fstab

# /etc/fstab: static file system information.
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=13700fe0-8d32-473c-866d-7025fda557df         /      ext2    defaults,auto       1

# /dev/sda7
UUID=4c758425-176c-4258-84eb-c958ff9f3434   /media/data     ext3   defaults,auto 0     1

# /dev/sda6
UUID=e3b69b32-455c-49b1-abc2-6cca5d4cb48b       none    swap    sw              0       0


I still cannot create any file in /media/data.

---

### Post by handydan918 on 2008-11-17
Hmmm.

I wonder what ls -l would have to say about /media/data....

---

### Post by dj620129 on 2008-11-17
> **handydan918 said:**
> Hmmm.

I wonder what ls -l would have to say about /media/data....

I have chmod /media/data. Then out of curiosity I put /dev/sda7 back to its original owner (root:disk).

See the ls -l of /dev/sda* and /media/data below.

david@david-laptop:~$ ls -l /dev/sda*
brw-rw---- 1 root disk 8, 0 2008-11-17 22:37 /dev/sda
brw-rw---- 1 root disk 8, 1 2008-11-17 22:37 /dev/sda1
brw-rw---- 1 root disk 8, 2 2008-11-17 22:37 /dev/sda2
brw-rw---- 1 root disk 8, 5 2008-11-17 22:37 /dev/sda5
brw-rw---- 1 root disk 8, 6 2008-11-17 22:37 /dev/sda6
brw-rw---- 1 root disk 8, 7 2008-11-17 14:37 /dev/sda7
david@david-laptop:~$ ls -l /media
&#54633;&#44228; 24
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB1
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB2
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB3
lrwxrwxrwx 1 root root     6 2008-11-13 18:57 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-11-13 18:57 cdrom0
drwxrwxr-x 3 root david 4096 2008-11-17 14:29 data
drwxrwxrwx 1 root root  4096 2008-11-16 15:52 disk
david@david-laptop:~$ 


Now it works fine. 
I have to add that I had to reboot because even unmounting and running sudo mount -a did not work.

Anyway I rebooted and now it works fine.

Thanks.

---

### Post by dj620129 on 2008-11-17
> **handydan918 said:**
> Hmmm.

I wonder what ls -l would have to say about /media/data....

I have chmod and chown  /media/data. Then out of curiosity I put /dev/sda7 back to its original owner (root:disk).

See the ls -l of /dev/sda* and /media/data below.

david@david-laptop:~$ ls -l /dev/sda*
brw-rw---- 1 root disk 8, 0 2008-11-17 22:37 /dev/sda
brw-rw---- 1 root disk 8, 1 2008-11-17 22:37 /dev/sda1
brw-rw---- 1 root disk 8, 2 2008-11-17 22:37 /dev/sda2
brw-rw---- 1 root disk 8, 5 2008-11-17 22:37 /dev/sda5
brw-rw---- 1 root disk 8, 6 2008-11-17 22:37 /dev/sda6
brw-rw---- 1 root disk 8, 7 2008-11-17 14:37 /dev/sda7
david@david-laptop:~$ ls -l /media
&#54633;&#44228; 24
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB1
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB2
drwxr-xr-x 2 root root  4096 2008-11-15 18:04 USB3
lrwxrwxrwx 1 root root     6 2008-11-13 18:57 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-11-13 18:57 cdrom0
drwxrwxr-x 3 root david 4096 2008-11-17 14:29 data
drwxrwxrwx 1 root root  4096 2008-11-16 15:52 disk
david@david-laptop:~$ 


Now it works fine. 
I have to add that I had to reboot because even unmounting and running sudo mount -a did not work.

Anyway I rebooted and now it works fine.

Thanks.

---

