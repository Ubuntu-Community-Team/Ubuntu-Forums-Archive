---
title: "Insufficient Hard drive Space?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by Andorudesu on 2012-11-24
I'm currently trying to install World of Warcraft on Ubuntu 12.10, and I finally got my computer to go to the install screen, but when I click install, it says > There is insufficient space on your hard drive. Please clear some space or select a different drive and try again. 22.0GB required. I don't have a clue as to why this is showing.  I'm almost positive that I have more than a few hundred gigs in my Ubuntu partition.  Any help would be great, Thanks in advance.:P

---

### Post by ibjsb4 on 2012-11-24
Wow, thats one big game.  Anyhow; take a look at your HDD space.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

df -h

---

### Post by Andorudesu on 2012-11-24
It says I have 408G of space left.
> leedle-cx@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       24G   20G  4.2G  83% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           781M  904K  780M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  2.3M  2.0G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda3       456G   49G  408G  11% /host

---

### Post by Andorudesu on 2012-11-25
I've tried everything I know to do, so if anyone has ANY suggestions, PLEASE let me know.  Do you think I could have to do a fresh install of Ubuntu again?  I also can't copy things withing my system.  I tried copying a file from a CD and it says "There is not enough space on the destination. Try to remove files to make space." Gosh, what can I do?:confused:

---

### Post by ibjsb4 on 2012-11-25
Should of said more than that; 408G of space left where?

Also, have you been here?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=World+of+Warcraft&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=World+of+Warcraft&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Andorudesu on 2012-11-25
I was assuming that /dev/sda3 was my Ubuntu partition, but I was most likely wrong... 
No, but I'll check on it.

---

### Post by ibjsb4 on 2012-11-25
What you appear to have is a wubi install (ubuntu inside windows).  If this is what you have, a wubi install is limited to 30G max and you have only 4.2G left open.

---

### Post by Andorudesu on 2012-11-25
Oh. So what do you suggest that I do?

---

### Post by krustenBrot on 2012-11-25
You could run WoW on Windows and install it there.
Or split up the Partition and install Ubuntu natively if you want to use it as a OS in future. The option to "take" space from your Windows Partition is given during the Ubuntu setup.

---

### Post by ibjsb4 on 2012-11-25
> **krustenBrot said:**
> You could run WoW on Windows and install it there.
Or split up the Partition and install Ubuntu natively if you want to use it as a OS in future. The option to "take" space from your Windows Partition is given during the Ubuntu setup.

Yep, time to upgrade you ubuntu install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=World+of+Warcraft&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=World+of+Warcraft&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Mark Phelps on 2012-11-25
IF you're running Win7, do NOT use the Ubuntu installer to shrink the Win7 filesystem.  Doing so risks corrupting the Win7 install and rendering it unbootable.  Use only the Win7 Disk Management utility to shrink Win7.

Also, while you're in Win7, running the Disk Management utility, count the number of "drives" (actually, they are partitions).  IF you already have the maximum of 4, forcing the creation of a fifth with automatically convert your partitions to Dynamic Disks -- something you do NOT want to do.

---

### Post by Andorudesu on 2012-11-25
Okay.  Thanks for your help.:P  I decided to install Ubuntu in it's own partition with a thumb drive.  Fingers crossed that it works!

---

### Post by bilkay on 2012-11-25
There's another possible solution to your problem.

Your root filesystem (/dev/loop0) is actually a 24GB file on your ntfs drive. You can create another such filesystem and mount it, perhaps at /home. Here's how:

```
~$ dd if=/dev/zero of=/host/MyNewHome bs=1K count=24M
~$ mkfs -t ext3 /host/MyNewHome
```
Note:  mkfs will tell you that it's not a block device and ask if you want to proceed. Answer "y".

You have now created a new 24GB (or whatever size you like) filesystem that can be mounted wherever you like. If it's going to be your new /home, you'll need to mount it somewhere and then copy your current /home to it:

```
~$ sudo mnt /host/MyNewHome /mnt
~$ cd mnt
~$ sudo cp -pr /home/* .
```To mount it at /home, add this entry to /etc/fstab. Make sure it's after the /host entry:

/host/MyNewHome /home ext3 loop,errors=remount-ro 0    1

After restart, df /home should tell you that it is a 24B filesystem mounted at /dev/loop1. If so, that's half your problem solved. The other half is clearing out the old /home directory to free up space on your root directory. For this you'll need a rescue disk or thumb drive. After a normal restart, your new home will be mounted over the old home, so you won't have access to it. That's why you need to use the rescue mode.

Your /etc/fstab should tell you where on your C: drive the ubuntu file is. In rescue mode, mount that file somewhere. If somewhere is /mnt, then:

```
~$ cd /mnt/home
~$ rm -Rf *
```

---

### Post by bilkay on 2012-11-26
On second thought, it's not necessary to use rescue mode. Just mount your root directory at some other mount point (e.g. /mnt). If you're using WUBI, you'll have to use the loop option to mount it.

---

