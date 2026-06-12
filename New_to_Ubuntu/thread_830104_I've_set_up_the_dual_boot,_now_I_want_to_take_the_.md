---
title: "I've set up the dual boot, now I want to take the next step....."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by sum janus on 2008-06-15
Hi,
I'd been on Debian for about a month, but other than that I've been a lifelong Windows user.  I had a ton of problems with Debian..... my gtk+- was out of date and I needed to upgrade my gtk+- to do so??..... or something crazy like that.  I also hated how I was using "Iceweasel", not the official "Firefox", which kept me away from updates.

So I picked up a Ubuntu CD, put it in, and it ran slow - but I had heard live CDs to run slow (and I only have 600 mHz processing), and wanted to see how it'd run off an install.  So I set up a dual boot between Ubuntu and Debian, and I am totally loving Ubuntu.  Slick and easy.

:guitar:

The problem is that I have a really small hard drive - and I've been pulling some games off of the Ubuntu repository.

So quite simply, how do I clear the other partition?  I know I want to free the space, but I don't know how.... any help would be great.

Thanks a ton

---

### Post by durand on 2008-06-15
Install gparted:
```
sudo aptitude install gparted
```
Run it: System > Administration > Partition Editor

**[COLOR="Red"]Make sure you know what partition you want to remove!![/COLOR]** And delete the partition you don't want. Gparted is pretty simple to use.

I'm not really sure how you would combine it with your existing ubuntu partition though. I guess you should wait for more replies.

---

### Post by sum janus on 2008-06-15
Alright thanks.  Also, how would I know which partition Ubuntu is on?  I wouldn't want to accidentally delete that :O !

---

### Post by hyper_ch on 2008-06-15
install gparted, delete the debian partition, expand the ubuntu one over the freed space

---

### Post by hyper_ch on 2008-06-15
run

```

df -l

```

it will say what partition is mounted where... if you are in ubuntu then the one that is mounted as "/" shouldn't be deleted...

you can also post the output here and also your fstab.

---

### Post by sum janus on 2008-06-15
Here's df-l
```

Filestyem - 1K Blocks - Used - Available - Use % - Mounted On

/dev/sda6 - 15866612 - 4995760 - 10071220 - 34% - /
varrun - 257812 - 112 - 257700 - 1% - /var/run
varlock - 257812 - 0 - 257812 - 0% - /var/lock
udev - 257812 - 60 - 257752 - 1% - /dev
devshm - 257812 - 44 - 257768 - 1% - /dev/shm
lrm - 557812 - 38176 - 219636 - 15% - /lib/modules/2.6.24-18-generic/volatile
gvfs-fuse-daemon - 15866612 - 4995760 - 10071220 - 34% - /home/eric/.gvfs
/dev/scd1 - 50436 - 50436 - 0 - 100% - /media/cdrom0

```

So I'm guessing sda6 is what I want to keep for sure, which ones do I delete?  If it helps, when Ubuntu was partitioning I set it up 65-35 in favor of Ubuntu.

---

### Post by sum janus on 2008-06-15
Also, here's what GParted says:

```

Partition - Filesystem - Mountpoint - Size - Used - Unused - Flags

/dev/sda1 - ext3 - [Blank] - 8.46 GB - 5.69 GB - 2.75 GB - Boot
/dev/sda2 - extended - [Blank] - 17.06 - [Blank] - [Blank] - [Blank]
# These are all subsections of sda2:
/dev/sda6 - ext3 - / - 15.25 GB - 4.88 GB - 10.37 GB - [Blank]
/dev/sda7 - linux-swap - [Blank] - 729.48 MB - [Blank] - [Blank] - [Blank]
/dev/sda5 - linux-swap - [Blank] - 1.10 GB - [Blank] - [Blank] - [Blank]

```

If someone would be so kind as to guide me through what to do, I'd really appreciate it.

---

### Post by durand on 2008-06-15
Ok, this is kinda a problem because you haven't mounted your other partitions. A screenshot of gparted would be more helpful.
Or you could just go to the Computer and click on all the partitions there, then run df -l again.

EDIT: Whoops!

---

### Post by durand on 2008-06-15
Ok, run these commands:

```

mkdir sda1
sudo mount /dev/sda1 sda1
mkdir sda2
sudo mount /dev/sda2 sda2

```

Then go inside those directories and see which one is your debian partiton.

PS: You have two swap partitions for some reason...

---

### Post by dnns123 on 2008-06-15
I think you have to run Gparted from the Live CD. Delete the debian partition (you probably know its sda[COLOR="Red"]X[/COLOR]. Right click on the Ubuntu partition and resize it to max. Apply and reboot!

P.S. I'm not a pro. In my opinion, get a second opinion. Anyway, this is how I would do it.

---

### Post by durand on 2008-06-15
> **dnns123 said:**
> I think you have to run Gparted from the Live CD. Delete the debian partition (you probably know its sda[COLOR="Red"]X[/COLOR]. Right click on the Ubuntu partition and resize it to max. Apply and reboot!

P.S. I'm not a pro. In my opinion, get a second opinion. Anyway, this is how I would do it.

Actually, you have a point there! You cannot edit a partition that is currently mounted so if you want to resize your ubuntu partition, you will need to use a live cd to do it.

---

### Post by sum janus on 2008-06-15
So, I would need to reinstall Ubuntu?

---

### Post by durand on 2008-06-15
> **sum janus said:**
> So, I would need to reinstall Ubuntu?

No way!

---

### Post by durand on 2008-06-15
Though you might want to backup some stuff first.

EDIT: I should really stop multiposting.

---

### Post by hyper_ch on 2008-06-15
/dev/sda6 seems to be your ubuntu partition....

and

/dev/sda1 seems to be your debian partition

however /dev/sda6 is part of the extended partition /dev/sda2... not sure if you can resize that, you'd have to try....

easiest would be a clean install of ubuntu and make a backup first.

---

### Post by sum janus on 2008-06-15
Alright cool.  I've only had it for a couple of days so I don't really have any important files.  I'll redo it soon.

Thanks for all your help

~~~

Actually do you think I'd be better off just waiting until I need the space?  I still have a few GBs left, and because the Zune software won't work (not even through wine) I won't be needing to put my music on..... and I should be getting a new computer within the year.

---

