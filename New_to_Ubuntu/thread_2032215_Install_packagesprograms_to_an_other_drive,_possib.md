---
title: "Install packages/programs to an other drive, possible?"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Bufeu on 2012-07-23
Hi,
I just wonder if it is possible to install packages/programs on an other drive that Ubuntu is installed on. I'm going to get a new computer soon with a SDD. Windows, this is easy, thanks to the drive letters. I still want to use Synaptic/apt-get/Ubuntu Software Center (with other words, I don't want to use and install.deb-files on my own, i prefer a front-end like Synaptic/Ubuntu Software Center).
Anyone who knows if it's possible? Can I have different programs on different drives, e.g. Firefox and Transmission on my HDD and VLC and GIMP on my SSD? If I can, can I move already installed programs from a drive to on other?

---

### Post by richpri on 2012-07-23
I guess that the answer has to be "it depends".

In all versions of linux, software is not installed on drives; rather it is installed in directories.  There is a standard directory structure and in it most packages are installed in the /usr directory. It contains the majority of user utilities and applications, and partly replicates the root directory structure, containing for instance, among others, /usr/bin/ and /usr/lib. 

Now you could move one of these directories to a different drive and point, for example, /usr to the new /usr/lib on the new directory.  But. before you try anything like this, I suggest that you do enough research to be fairly sure you won't mess anything up.

---

### Post by Bufeu on 2012-07-23
Okey, so I actually can change what directory that I want to install the software on? What happens if the directory change its name? Is a re-installation needed or can I use "environment variables" and just change the variable?

---

### Post by Cheesemill on 2012-07-23
Not really.

Unlike Windows which stores applications in separate directories under  'Program Files', a Linux applications is spread out in several locations  across the disk. For example program binaries live in /usr/bin,  documentation lives in /usr/share/docs, libraries are in /lib etc...

---

### Post by asmoore82 on 2012-07-23
The linuxy thing to do is to mount key directories on different physical drives. You can't easily say install Firefox here and VLC over there, but you can mount the entire /usr directory on a different drive and the /home directory on another. This way, the program files of Firefox/VLC in /usr versus the cache/movie files in /home load *simultaneously* from different physical drives.

Also, in this setup, should anything drastic happen to either the /usr drive or the /home drive, most of your custom system configuration will still be safely in the /etc directory on the root drive. And the root drive can still boot the system to a rudimentary shell to attempt recovery. I say "rudimentary" because there won't be much to work with, most likely just what's contained within your initrd, but it's better than nothing.

Creating this setup after the fact when a new drive arrives could be a little tricky. You'd want to get to a rescue shell, likely from some bootable media. Then rsync /usr to the new drive. Then configure fstab on the old drive to use the new /usr. Then boot it and make sure it works! Then back to bootable media to delete the old /usr and actually recover the free space.

All that having been said, the only thing I ever actually put on a separate partition is /home.

---

### Post by Bufeu on 2012-07-23
> **Cheesemill said:**
> Not really.

Unlike Windows which stores applications in separate directories under  'Program Files', a Linux applications is spread out in several locations  across the disk. For example program binaries live in /usr/bin,  documentation lives in /usr/share/docs, libraries are in /lib etc...
So, because the files "spreads out" on the disk, it's impossible to install a whole program/package under the same location (directory)?

---

### Post by Cheesemill on 2012-07-23
> **Bufeu said:**
> So, because the files "spreads out" on the disk, it's impossible to install a whole program/package under the same location (directory)?
Correct.

---

### Post by Bufeu on 2012-07-24
> **Cheesemill said:**
> Correct.
That means you shouldn't have a SSD if you're running a Linux-based OS?

---

### Post by Mark Phelps on 2012-07-24
> **Bufeu said:**
> That means you shouldn't have a SSD if you're running a Linux-based OS?

No, it just means you need one large enough to include the apps you're installing, not just the OS.

---

### Post by Cheesemill on 2012-07-24
> **Bufeu said:**
> That means you shouldn't have a SSD if you're running a Linux-based OS?
I do use an SSD.
I have my / and /home partitions on the SSD, they currently take up about 20GB between them.
All of my media files and other data are on a mechanical hard drive.
```
rob@precise:~$ df -h -t ext4
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        40G   13G   26G  34% /
/dev/sda3        20G  6.1G   13G  33% /home
/dev/sdb1       882G  356G  483G  43% /data
```
Even if you were to go overboard with installing applications it would be difficult to get / any bigger than around 25GB. Seeing as the smallest SSD's you can get are 64GB (it's what I have) then I really don't see the problem with having all of your applications stored in their default locations.

---

### Post by Bufeu on 2012-07-24
The problem is that I want to have some program on the HDD and some on the SSD.

---

### Post by gordintoronto on 2012-07-24
> **Bufeu said:**
> The problem is that I want to have some program on the HDD and some on the SSD.

The Linux Way is to have your root (/) on the SSD, and /home on the mechanical drive.

I have quite a few programs installed beyond a basic installation, and my root is less than 6 GB. Even a small SSD is much larger than this.

Programs just aren't that big! Media, on the other hand...

---

### Post by Bufeu on 2012-07-24
> **gordintoronto said:**
> The Linux Way is to have your root (/) on the SSD, and /home on the mechanical drive.

I have quite a few programs installed beyond a basic installation, and my root is less than 6 GB. Even a small SSD is much larger than this.

Programs just aren't that big! Media, on the other hand...
But I mean... Temporary files then? A SSD can only handle a certain number of writes...

---

### Post by Cheesemill on 2012-07-24
There are a couple of steps that can be used to tune an SSD system...

1 - Add the discard and noatime options to your /etc/fstab file.

The discard option enables trim support whereas the noatime option disables the write that usually happens every time a file is accessed.


2 - Move /tmp to a RAMdisk.

If you have a large amount of RAM then you can mount /tmp in RAM instead of using a physical drive. This also cuts down on the number of writes to your SSD.


3 - Have swap on a physical drive.

This will also cut down on the number of unnecessary disk writes.


Some research for you:

[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Bufeu on 2012-07-24
2. Of course, I can move /tmp to a partition on my HDD?

3. Do I really need a swap (I have 8 GB RAM)?

---

### Post by Cheesemill on 2012-07-24
> **Bufeu said:**
> 2. Of course, I can move /tmp to a partition on my HDD?
Of course.

> 3. Do I really need a swap (I have 8 GB RAM)?You don't have to. I just have a swap partition the same size as my RAM (12GB) for the few occasions that I hibernate, space on my HD is cheap and plentiful :)

---

### Post by Bufeu on 2012-07-24
So you mean the programs will not be so big so it's necessary to move program by program to the HDD (in other words, can all programs be installed on the SSD without too many writes?)

---

