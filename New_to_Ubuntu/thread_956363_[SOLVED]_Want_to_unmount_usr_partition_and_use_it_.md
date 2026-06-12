---
title: "[SOLVED] Want to unmount /usr partition and use it somewhere else"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by danimaltron on 2008-10-23
I decided to go all out and install ubuntu today and kill off Vista completely. I only did this because I got a new MacBook Pro and wanted to use my desktop as a file/media/web server :)

So as I was installing, I had no idea how to setup my partitions and mount points. I did what I thought was best and now I realize what I did was not very good. Here is df -h results:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              38G  979M   35G   3% /
varrun               1008M  220K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   56K 1008M   1% /dev
devshm               1008M   12K 1008M   1% /dev/shm
lrm                  1008M   44M  964M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb3              71G   26G   42G  39% /home
/dev/sda1             278G  2.1G  262G   1% /usr
gvfs-fuse-daemon       38G  979M   35G   3% /home/danny/.gvfs

```

As you can see I put an entire large hard-drive dedicated to /usr. Not only is this not ideal for performance, I cant even use the space because I can't create new folders in this directory (is this for some security reason?).

This is my first day working with any Linux distro, so I really had no idea what the /usr directory was when I installed.

I want to know: Is it possible to rearrange my partitions & mount points and come out with something usable so that I can use my space to share files, etc? I think the home directory should get all of it.

I have 2 hard drives. The first has two partitions, 1 mounted to /, the other to /home. The second hard drive has 1 partition and is mounted to /usr.

Will I need to reinstall to fix this? If I do... that sucks, but it's okay. But I need to know how I should setup my partitions and mount points to best utilize my space and set myself up to have lots of room for sharing files.

In the future I will be adding another hard drive, or replacing one of them as well. So I need that flexibility.

Thanks!

---

### Post by Hexagoon on 2008-10-23
Oh, you've gotta reinstall this, use the standard setup that the guide gives you, then there should be no problem...

You dont have to make a partition for each mountpoint :)

Edit: I just saw that you had 2 drives, then you probably want to create a volume group, to get one big partition instead of 2 small.

Then you format both, create a small(500 mb) partition for mountpoint /boot , then you create a volume group of the remaining space on both disks, then  split that in 2, one formatted as swap, and one formatted as ext3 mounted on /

Hmm, that might have been the worst explanations since... yeah, who knows... but i hope you got it :)

---

### Post by 3rdalbum on 2008-10-23
It's probably a better idea to use two partitions: / and /home. /home will contain your home directory, or if you have multiple users, home directories.

20-30 gigabytes is ample for the /, and just chuck the rest into /home. If you really wanted to you could copy the data from sdb3 to sdb1 and vice versa, and then change the /etc/fstab file to point in the opposite directions; that would give you a big home, but also an unreasonably big usr. But it's probably better to reinstall and reallocate all that space more wisely.

As for your kinda second question, your ordinary user account can't access the internals of the system; this includes /usr. It is a security feature that stops ordinary users from being able to mess up a computer for everybody in a shared environment, and it's also useful for stopping malware from installing itself system-wide. However, the first user account created can "sudo" into the administrator account, which is called "root".

You know when you start up Synaptic Package Manager and it asks you for a password? Synaptic must run as root, so it asks you the password in order to elevate itself to root. You can run any program as root; for instance, press Alt-F2 and type "gksudo nautilus" and you can modify and delete files at will. But BE CAREFUL what you do as root, and don't run as root for longer than necessary.

---

### Post by Liviu-Theodor on 2008-10-23
Don't need to reinstall anything. Just resize the /usr partition to about 8 GB (just to be safe, you can use any convenient value). With the freed up space you can do whatever you want - create as many partition as you want, mount them wherever you want.

To do that, you must first run [FONT="Courier New"]System-Administration->Partition Editor[/FONT].

After creating partitions, you must read a bit about the [/etc/fstab]("https://help.ubuntu.com/community/Fstab") file. Take a look at it.

Now, follow these commands in a terminal:
```
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

Your new partition(s) must be in the [FONT="Courier New"]/etc/fstab[/FONT] file. Read also the [Where to put mount for startup]("http://ubuntuforums.org/showthread.php?t=953317") and the [[SOLVED] Swap partition not mounted automatically]("http://ubuntuforums.org/showthread.php?t=955414") threads.

---

### Post by Hexagoon on 2008-10-23
> **Liviu-Theodor said:**
> With the freed up space you can do whatever you want - create as many partition as you want, mount them wherever you want.

I can't agree with that on a desktop system, on a server, ok. But on a desktop i want as much space as possible, i would hate to run out of space on the /usr/ partition and have a lot of space on /share for example :P

Just my humble opinion :p

---

### Post by Liviu-Theodor on 2008-10-23
> **Hexagoon said:**
> I can't agree with that on a desktop system, on a server, ok. But on a desktop i want as much space as possible, i would hate to run out of space on the /usr/ partition and have a lot of space on /share for example :P

Just my humble opinion :p

That is one of the charms of GNU/Linux. One can transform a desktop into a server and a server into a desktop with ease. Or use it as both desktop and server. If you run into the problem described, you can also resize partitions, or move them across hard-drives. And of course I want also on servers as much space as possible, because there I store files needed in common for workstations...

My humble opinion is not the same as yours. :p

---

### Post by danimaltron on 2008-10-23
> **Liviu-Theodor said:**
> Don't need to reinstall anything. Just resize the /usr partition to about 8 GB (just to be safe, you can use any convenient value). With the freed up space you can do whatever you want - create as many partition as you want, mount them wherever you want.

To do that, you must first run [FONT="Courier New"]System-Administration->Partition Editor[/FONT].

After creating partitions, you must read a bit about the [/etc/fstab]("https://help.ubuntu.com/community/Fstab") file. Take a look at it.

Now, follow these commands in a terminal:
```
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

Your new partition(s) must be in the [FONT="Courier New"]/etc/fstab[/FONT] file. Read also the [Where to put mount for startup]("http://ubuntuforums.org/showthread.php?t=953317") and the [[SOLVED] Swap partition not mounted automatically]("http://ubuntuforums.org/showthread.php?t=955414") threads.

Problem is, when I open Gparted I cannot edit the partition of /usr. I suspect because it's in use? Would it work via command line?

---

### Post by Duck2006 on 2008-10-23
You will have it to be unmounted, so it may be best to use the live CD to do it.

---

### Post by danimaltron on 2008-10-23
> **Hexagoon said:**
> Oh, you've gotta reinstall this, use the standard setup that the guide gives you, then there should be no problem...

You dont have to make a partition for each mountpoint :)

Edit: I just saw that you had 2 drives, then you probably want to create a volume group, to get one big partition instead of 2 small.

Then you format both, create a small(500 mb) partition for mountpoint /boot , then you create a volume group of the remaining space on both disks, then  split that in 2, one formatted as swap, and one formatted as ext3 mounted on /

Hmm, that might have been the worst explanations since... yeah, who knows... but i hope you got it :)

Thanks! I don't recall seeing an option to create a volume group during install using manual partition settings. Where do I go do to this? Should I look again? 

> **3rdalbum said:**
> It's probably a better idea to use two partitions: / and /home. /home will contain your home directory, or if you have multiple users, home directories.

20-30 gigabytes is ample for the /, and just chuck the rest into /home. If you really wanted to you could copy the data from sdb3 to sdb1 and vice versa, and then change the /etc/fstab file to point in the opposite directions; that would give you a big home, but also an unreasonably big usr. But it's probably better to reinstall and reallocate all that space more wisely.


Thanks as well. So I will partition my first hard drive with 20-30GB and use that for /. Then I will create partition with remaining space on that disk.
For second hard drive, I will create 1 large partition and 1 small for swap. Now I understand that I should create a volume group with the remaining space on disk 1 and the large space that was on disk 2 and mount it to /home. I'm just not sure how to do that last part (grouping two partitions so I can mount them both to /home)

Thanks for answering my other question as well

---

### Post by danimaltron on 2008-10-23
> **Duck2006 said:**
> You will have it to be unmounted, so it may be best to use the live CD to do it.

Thanks. Now I know. But I think I'm just going to reinstall anyways to fix this mess. Might be better in the long run it would seem.

---

### Post by Duck2006 on 2008-10-23
> **danimaltron said:**
> Thanks. Now I know. But I think I'm just going to reinstall anyways to fix this mess. Might be better in the long run it would seem.

That should make it easyer for you, good luck.

---

### Post by danimaltron on 2008-10-23
Couldn't I just put the first hard drive to /, and then the second hard drive to /home? Wouldn't that give me the same affect as creating a volume group and mounting it to /home?

If I mount one hard drive to /, can I use all of that space by whatever is in /home? I don't quite have my head wrapped around how linux partitions/mount points work.

---

### Post by danimaltron on 2008-10-23
Okay I am installer now and trying to figure out how to partition this thing up.

I currently have 30Gb for / and 3GB to swap area. Then about 86GB on one hard drive, and 300GB on the other hard drive that I want to use for /home.

It won't let me mount both partitions to /home, so how can I use all of that space for sharing my files? I tried doing logical partitions as well to see if that would enable me to mount them both, but the same thing there.

Not sure what to do from here.

Thanks

---

### Post by Hexagoon on 2008-10-23
I'm pretty sure there is a LVM something button at the manual partitioning screen. If it's still an option, i think you could figure out how to do using my previous post. With a little luck :) That way you can use all space from both disk wherever you want in the filesystem, i think it's great, others might not agree :)

---

### Post by Hexagoon on 2008-10-23
> **danimaltron said:**
> 
It won't let me mount both partitions to /home, so how can I use all of that space for sharing my files? I tried doing logical partitions as well to see if that would enable me to mount them both, but the same thing there.


Sorry for double posting.

If i were forced to have separate partitions, i would mount all avaliable space on hdd1 for root, then all available on disk 2 for home.

---

### Post by danimaltron on 2008-10-23
There is no LVM option from the manual screen. I see others talking about it when I google this, but I don't have it. I'm using 8.0.04.1 amd64 bit.

I don't quite understand Linux partitioning, so I have one question about your last post:

If I mount all of HD1 to root, and then all of HD2 to /home, will that limit the /home directory to only what's available on HD2? or will it allow me to use all of what's available on HD2 + whatever is free on HD1?

I'm assuming I would be limited to HD2. Which isn't very good for me.

So if I can't get the LVM through the manual partitioning screen on install, how can I setup a volume group? Can I make some sort of partitions now and then set them up after its all installed using Gparted or something?

I'm still sitting at install screen :) Thanks

---

### Post by Hexagoon on 2008-10-23
Hmmm, wierd that it doesn't show up, can it have something to do with the 64 bit part? :/

Anyway, yes, you will be limited to hd2 on home, a lot of space will go lost if you dont install huge amounts of software :P One solution to this is to create one extra partition on hd1 that you mount in a subfolder to your home (post-install), seems like quite a workaround though :P

---

### Post by danimaltron on 2008-10-23
Can I prepare the partitions I want to use in LVM now, and then set them up once I am installed? If so, where should I mount them to so I can easily unmount later?

And yes... very wierd that there is no LVM from manual partitioning.

---

### Post by Hexagoon on 2008-10-23
I'm not sure that it would be a breeze setting up LVM after install, it would be nice to get some replies from a more experienced user. I'm out of ideas :/

Fringe on tv now, good luck!

---

### Post by danimaltron on 2008-10-23
Thanks for your help :)

After tonnes of googling it seems that the LVM is only available using the alternate desktop version of Ubuntu? Is this true? I cant find any definite answer from my searches.

---

### Post by Hexagoon on 2008-10-24
Aaah, you're right, you have to download the alternate cd. I didn't know because i always go for the alternate cd :)

---

