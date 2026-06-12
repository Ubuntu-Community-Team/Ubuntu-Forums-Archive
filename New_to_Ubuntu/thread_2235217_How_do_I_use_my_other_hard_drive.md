---
title: "How do I use my other hard drive?"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by shahin on 2014-07-19
Greetings-
This is the status of my partitions:
:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           931.5G
&#9500;&#9472;sda1 ext4   845.8G
&#9500;&#9472;sda2            1K
&#9492;&#9472;sda5 ntfs    85.7G
sdb           111.8G
&#9500;&#9472;sdb1 ntfs      40G
&#9500;&#9472;sdb3            1K
&#9500;&#9472;sdb5 ext3    21.6G
&#9500;&#9472;sdb6 swap     2.2G [SWAP]
&#9500;&#9472;sdb7 ext4    31.2G
&#9492;&#9472;sdb8 ext4    16.9G /
sr0            1024M

I am out of room. How can I take advantage of the sda1? As you can see this is a dual boot machine. Do I need to move root? How do I do this please? I am familiar with GParted and the live CD. I can re size my drive. Is that the best way to do this? Should I just use a live CD? How should I proceed?

---

### Post by grahammechanical on 2014-07-19
Which hard drive is full up? What drives are the two operating systems on? What operating systems are they? What are you using the partitions for? If it was me I would use the smaller drive for both operating systems and then use the larger driver for data. But that is just me. You would most likely have to re-install at least one, if not both of the operating systems.

---

### Post by shahin on 2014-07-19
root seems to be full:

```

sansari@shahin-desktop:~$ df -h --total
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        17G   15G  771M  96% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            745M   12K  745M   1% /dev
tmpfs           151M  1.2M  150M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            754M  152K  754M   1% /run/shm
none            100M   48K  100M   1% /run/user
total            19G   15G  2.5G  86% -

```
What drives are tow operating systems one? For windows, I used some of both drives. I move MyDocuments folder to the larger drive. For Ubuntu, I think I partitioned most of the 2nd drive, but I did not use it. So that is why you see ext4 but all the Ubuntu partitions are on the smaller drive. This machine crashed when I tried to resize the smaller drive. I was able to recover windows, and then I added the larger drive.Then I found a great tool to recover grub, and then I saw my old Ubuntu install and life was good for a while. Now I am facing the same size issue. How do I fix the size issue with the Ubuntu root, and use the larger drive for a /data partition? I don't think I have created a data partition. Can I use Gparted to create a data partition on the 2nd drive for my Ubuntu? I think Windows is already configured to use the 2nd drive as data. I may have to resize it at some point. But that is ok. It is XP, and I am just keeping it because this machine does not have the hardware profile to be upgraded to Win7 or later. 
Is

---

### Post by shahin on 2014-07-19
Although I see the larger drive when I log into Ubuntu, I can not copy any of the directories from / to the larger drive. When I drag the directory over, it bounces right back. Am I missing something?

---

### Post by shahin on 2014-07-19
Here is what the larger drive looks like:
[IMG]https://drive.google.com/?urp=https://www.google.com/url?sa%3Dt%26rct%3Dj%26q%3D%26esrc%3Ds%26so&authuser=0&ddrp=1#my-drive[/IMG]

---

### Post by shahin on 2014-07-19
I am trying to post images of my harddrvies in Gparted, but seems like we can not include images in the forum? Is that right?

---

### Post by Iowan on 2014-07-19
Images are allowed... 
Large images should be attached as thumbnails.

---

### Post by shahin on 2014-07-19
I found these procedures [http://askubuntu.com/questions/3402/how-to-move-boot-and-root-partitions-to-another-drive]("http://askubuntu.com/questions/3402/how-to-move-boot-and-root-partitions-to-another-drive") and I am trying to follow them. There is a section where it instructs updating the new /etc/fstab on the new root. I only find one fstab file. Is there more than one fstab? How do I switch to the new /, root, fstab file and update it with the UUID and the rest of the information?

---

### Post by yancek on 2014-07-19
> Although I see the larger drive when I log into Ubuntu, I can not copy  any of the directories from / to the larger drive. When I drag the  directory over, it bounces right back. Am I missing something?                 

A normal user has write permissions to the /home/user directory.  Pretty much any other directory or partition will need root/administrator rights.  That can be changed.  Since sda1 is your largest partition, you can boot Ubuntu and create a directory as a mount point for that partition:  sudo mkdir /mnt/sda1
You don't need to use sda1, you can rename it to whatever you want, just using that as a simple example.  After you have created this directory you need to mount it from Ubuntu which should work with:  sudo mount -t ext4 /dev/sda1 /mnt/sda1.  You should then be able to see any files and you should be able to copy files there if you are logged in with root privileges.

You can open a terminal in your /home/user directory and test copy a file from therr to sda1:  sudo cp filename /mnt/sda1, obviously change filename to the test file you want to copy.  Once you get that working, you can change permissions so that a user has more than read access.

It's a bit odd that the drive you have your operating systems on is seen as the second drive?

---

### Post by shahin on 2014-07-19
I think I need help with updating /etc/fstab. I updated it when I was using the livecd and ofcourse all the updates are gone. It is back to default:
```

ubuntu@ubuntu:~$ locate /etc/fstab
/etc/fstab
/etc/fstab.d
ubuntu@ubuntu:~$ more /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb6 swap swap defaults 0 0
ubuntu@ubuntu:~$ 
```

I do not know how to change to the new partition's /etc/fstab. My new partition is /dev/sda3. I copied all of my / directory in there.

---

### Post by 3rdalbum on 2014-07-19
I have no idea why your hard disks contain all those Ext3 and Ext4 partitions. It looks like only the smallest one is being used.

Rather than move your / to the first hard disk, I suggest you copy your /home folder to sda1. Then update /etc/fstab to mount /dev/sda1 as /home.

17 gigabytes is plenty for a / partition, and your personal files (/home) will be on sda1.

---

### Post by shahin on 2014-07-20
> **yancek said:**
> A normal user has write permissions to the /home/user directory.  Pretty much any other directory or partition will need root/administrator rights.  That can be changed.  Since sda1 is your largest partition, you can boot Ubuntu and create a directory as a mount point for that partition:  sudo mkdir /mnt/sda1
You don't need to use sda1, you can rename it to whatever you want, just using that as a simple example.  After you have created this directory you need to mount it from Ubuntu which should work with:  sudo mount -t ext4 /dev/sda1 /mnt/sda1.  You should then be able to see any files and you should be able to copy files there if you are logged in with root privileges.

You can open a terminal in your /home/user directory and test copy a file from therr to sda1:  sudo cp filename /mnt/sda1, obviously change filename to the test file you want to copy.  Once you get that working, you can change permissions so that a user has more than read access.

It's a bit odd that the drive you have your operating systems on is seen as the second drive?

Thanks; this helped me see the larger space. Do I need to mount it everytime I boot into Ubuntu? I guess I have to update fstab file if I want it to automatically mount?
Aftewards, I tried to move some directories from / to make space, but there deos not seem to be anything there that I can move. I su'd ( i.e. logged in as root ) and ls does not have anything. ls -a shows a bunch fo . files: 
```

root@shahin-desktop:~# ls
root@shahin-desktop:~# ls -al
total 56
drwx------ 10 root root 4096 Jul  7 16:22 .
drwxr-xr-x 22 root root 4096 Jul 20 05:02 ..
-rw-------  1 root root  415 Jul 19 17:33 .bash_history
-rw-r--r--  1 root root 3106 Feb 19 21:43 .bashrc
drwx------  3 root root 4096 Jun 18 23:14 .cache
drwxr-xr-x  6 root root 4096 Jul  7 16:22 .config
drwx------  3 root root 4096 Jun 18 23:14 .dbus
drwx------  3 root root 4096 Jul 10 21:51 .gconf
drwx------  2 root root 4096 Jun 18 23:15 .gvfs
drwxr-----  2 root root 4096 Jul 20 04:58 .hplip
drwxr-xr-x  3 root root 4096 Jun 18 23:14 .local
-rw-r--r--  1 root root  140 Feb 19 21:43 .profile
drwxr-xr-x  2 root root 4096 Jul  7 16:22 .vnc
-rw-------  1 root root  108 Jul  7 16:22 .Xauthority

```
I am still struggling with the issue of low space in my root directory.

My other issue is that DiskUsageAnalyzer does not seem to have access to root. When I run it, it says it could not scan / or some folder in it due to a permission issue. I have attached a screenshot of the image. [ATTACH=CONFIG]254852[/ATTACH]

---

### Post by Impavidus on 2014-07-20
Don't move random root-owned files to your larger partition. Your system won't be able to find them there and your system will stop working. Instead move your /home directory there. See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The fstab you have to modify is the one on your installed system. A live system has its own fstab, but you don't need to touch that. In fact, there is no need to run a live session to move your /home directory to its own partition.

Once you moved your /home directory to its own partition, the /home partition will no longer be shown in the file manager, but every file and directory in the /home directory will be located on that partition on your other drive.

Edit: I see you have only a small amount of data in your /home (which is atypical, but not so strange on relatively fresh installs), but the contents of your /var are huge. Check the contents of your /var/log. There may be overflowing log files.

---

### Post by shahin on 2014-07-20
Thanks:-) I'll review the link.

---

### Post by shahin on 2014-07-20
This helped; thanks. Here is the result:
```

sansari@shahin-desktop:/$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        17G   15G  946M  95% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            745M  8.0K  745M   1% /dev
tmpfs           151M  1.2M  150M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            754M  156K  754M   1% /run/shm
none            100M   48K  100M   1% /run/user
/dev/sda1       833G  215M  790G   1% /home
/dev/sda5        86G   28G   59G  32% /media/sansari/*******************
/dev/sdb1        41G   35G  5.5G  87% /media/sansari/********************
/dev/sdb7        31G  466M   29G   2% /media/sansari/******************************
/dev/sda6      1003K   17K  915K   2% /media/sansari/*********************

```
As you can see I am still using 15G of available 17G for /. Is that ok? Is 2G enough from here on out? My delima is that I can not move the start of / with Gparted; I have plenty of space in that same harddrive. I think if I move the start of /, it would mess up where Grub looks to boot my Ubuntu. Am I mistaken? I'll post an image in a few minutes to clearify what I mean.

---

### Post by shahin on 2014-07-20
Here is another pic of DiskUsage; I see all of my Winodes directories under /. [ATTACH=CONFIG]254853[/ATTACH]

---

### Post by shahin on 2014-07-20
I think there was an earlier post about why I have a number of ext3 and ext4 partitions. I think I tried to install Ubuntu a couple of times; that created some extra partitions. For instance I mounted /dev/sdb7, which is a 31G partition, and it does not seem to be actively used. I changed to var directory and it is empty. I think I should delete it; perhaps using the Gparted? 

```

sansari@shahin-desktop:~$ cd /mnt/
sansari@shahin-desktop:/mnt$ ls
sda1  sda3  sdb7
sansari@shahin-desktop:/mnt$ cd sdb7/
sansari@shahin-desktop:/mnt/sdb7$ ls
boot   home        media  opt   run  tmp                 usr
cdrom  lost+found  mnt    root  srv  ubiquity-apt-clone  var
sansari@shahin-desktop:/mnt/sdb7$ cd var/
sansari@shahin-desktop:/mnt/sdb7/var$ ls
lib  local
sansari@shahin-desktop:/mnt/sdb7/var$
```

---

### Post by coffeecat on 2014-07-20
@shahin, I have added code tags to the terminal output in a number of your posts. Please use BBCode code tags for terminal output and the contents of configuration files to preserve formatting. You can either type out the tags by hand thus:

[noparse]```
Your terminal output
```[/noparse]

Becomes:

```
Your terminal output
```

(It's better to switch from WYSIWYG mode to one of the source modes in the message editor if you do this.)

Or you can use the toolbar icon that looks like # in the advanced message editor.

---

### Post by shahin on 2014-07-20
Thanks. Sure, I'll do that.

---

### Post by Impavidus on 2014-07-20
I see you moved your /home directory to a separate partition. That's good.

Right now you have:
/dev/sda1: /home partition
/dev/sda2: extended partition
/dev/sda5: Windows data partition. This one is OK to mount read-write in Linux, if you later wish so, enabling you to share files between Windows and Linux.

/dev/sdb1: Windows C partition. Better not to touch this while in Linux
/dev/sdb3: extended partition
/dev/sdb5: Linux partition, probably containing a failed Ubuntu install
/dev/sdb6: swap partition
/dev/sdb7: Linux partition, probably containing another failed Ubuntu install
/dev/sdb8: Your currently installed system's root partition, which is nearly full.

Disk usage analyser can be a useful tool, but it doesn't care about partitions and available disk space. That it shows your Windows system is to be expected if it has been mounted, but it doesn't give us any useful information. The only useful information we do get from the analyser is the fact that your /var (in your working system on /dev/sdb8) is rather large. On my system it's 868MB, on your's it is 11GB (according to your screenshot in post #12). There could be a good reason for that, in which case you'd better expand your / partition or move /var somewhere else, but often it indicates a problem. There could be overflowing log files, so that's why I asked about them.

The /var directory on /dev/sdb7 is not very interesting.

---

### Post by shahin on 2014-07-20
@Impavidus Thanks. I did two major things that may contirbute to var increasing. I setup vnc remote desktop, and configured iptables. I don't suspect iptables would be the issue since the logs just role over. And I don't know engouh about vnc remote desktop to know why it would put so much stuff in var. Can I follow the same procedure I used to move /home and move /var to the larger partition? I tried to see what is the largest file in /var by issueing ```
hf -h
```, but it gives me the same information as issueing it from other working paths. I need a different command to see which file is creaping up in size quickly. Perhaps a combination of watch command with some other one that would print the file sizes would help get to the bottom of the issue.
The other item I wanted to share is that ever since I set up remote vnc, I can log into the user account I set up for vnc and not the account that I installed Ubuntu initially. It is really strange. When I try to use the initial username, the passsword is accepted but the screen refreshes with yet another password prompt window. And this keeps repeating until I change to the username that I setup vnc with, and then I can log in. Once I am in, I can use su to log in as the original username.

---

### Post by shahin on 2014-07-20
I have been trying to share a pic of what Gparted shows, and here it is:
[ATTACH=CONFIG]254858[/ATTACH][ATTACH=CONFIG]254859[/ATTACH] As you can see, my problem with / in sdb is that all the available space is below or before / starts. And I have to move that partition. Which I think it would mess up where Grab is configured to look for the start of Ubuntu image. I appreciate it if you could share a fix for this also. I'll also clean up the partitions remaining from failed Linux install attempts. Thanks.

---

### Post by shahin on 2014-07-20
I get the following message:
[ATTACH=CONFIG]254860[/ATTACH] So I cancel the request.

---

### Post by Impavidus on 2014-07-20
> **shahin said:**
> Can I follow the same procedure I used to move /home and move /var to the larger partition?Only move /var if you know why it has to be large. We don't know yet, so it's better to find that out first > I tried to see what is the largest file in /var by issueing ```
hf -h
```, but it gives me the same information as issueing it from other working paths. I need a different command to see which file is creaping up in size quickly. Perhaps a combination of watch command with some other one that would print the file sizes would help get to the bottom of the issue.Have a look here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
This tutorial explains how to find large files and other disk space problems. Best to use **du** to dig into your /var directory. In principle all log files are rotated, but if they are rotated once a week they can still grow very large if the error is printed every few seconds.
> The other item I wanted to share is that ever since I set up remote vnc, I can log into the user account I set up for vnc and not the account that I installed Ubuntu initially. It is really strange. When I try to use the initial username, the passsword is accepted but the screen refreshes with yet another password prompt window. And this keeps repeating until I change to the username that I setup vnc with, and then I can log in. Once I am in, I can use su to log in as the original username.That's an althogether different issue. It means that your graphical login crashes as soon as it starts. Use the text console (or a terminal and su) to get in and check ownership and permissions of /home/username/.Xauthority and /home/username/.ICEauthority. The should be owned by you and have permissions 600 (rw-------). If that doesn't fix it, start a separate thread for that.

> **shahin said:**
> I have been trying to share a pic of what Gparted shows, and here it is: As you can see, my problem with / in sdb is that all the available space is below or before / starts. And I have to move that partition. Which I think it would mess up where Grab is configured to look for the start of Ubuntu image. I appreciate it if you could share a fix for this also. I'll also clean up the partitions remaining from failed Linux install attempts. Thanks.
Try to fix your problem without resizing /. 17GB should be enough. If you do resize the root partition your system may become unbootable, although Boot-Repair should be capable of fixing that.

---

### Post by shahin on 2014-07-20
Thank you so much. The culprit was a large audacity file in /var/tmp:-) I remove it, and configure audacity to save project files in the Music folder in my home directory. I think life will be good now:
```

root@shahin-desktop:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb7        17G  4.9G   11G  31% /
udev            745M  4.0K  745M   1% /dev
tmpfs           151M  1.1M  150M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            754M  152K  754M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda1       833G  219M  790G   1% /home

```

---

### Post by Impavidus on 2014-07-20
That sounds like a solution. Could you mark the thread as solved (click thread tools (top of page) -> mark as solved)? If you have other issues it's best to open a new thread.

---

