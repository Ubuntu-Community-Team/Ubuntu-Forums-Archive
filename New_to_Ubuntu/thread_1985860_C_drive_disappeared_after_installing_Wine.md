---
title: "C drive disappeared after installing Wine"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by spudarthur on 2012-05-23
I have a dual boot of windows 7 and Ubuntu 12.04. I'm incredibly ignorant over Ubuntu issues. I hope someone whisper into my ears these words "Help is on the way". Thank you !!!

---

### Post by Enigmapond on 2012-05-23
Welcome to the forum. Can you be a bit more specific regarding the problem? You mean your virtual C drive???

---

### Post by anewguy on 2012-05-23
If, by chance, you thought that after installing Wine the drive it sees would be your Windows "C" drive, that would be in error.  Wine creates its own virtual drive "C" -> it's in a hidden folder in your home folder.

So, if you started Wine and thought "wow, everything's gone!", don't worry.   

If not, please do explain in much more detail just what you mean.

Dave ;)

---

### Post by spudarthur on 2012-05-24
Yeah, exactly. When I started wine and I thought everything's gone and I quickly uninstalled wine. Now I can't find c drive and also can't install anymore softwares. It says I don't have enough space.

---

### Post by Mark Phelps on 2012-05-24
You didn't tell us how you're looking for C:.

If you installed from inside Windows, you won't see C: at all.  That is because drive letters are conventions that MS Windows uses, not Linux.  To see your files in this case, you need to look under /host in your Linux filesystem.  Wubi installed Ubuntu versions automatically mount your Windows partition at that location.

If you installed from outside Windows, it's a similar situation -- you still won't see a C: drive.  Instead, you click the "home" icon on the top left area of the navigation bar on the left and you will see a list of partitions.  One of them will be your C: partition.

---

### Post by anewguy on 2012-05-24
Like Mark said, your regular "C" drive won't show as "C" in Linux.  And as I mentioned, the "C" drive you see in Wine is a virtual drive - it's just a file in a hidden folder in your home folder.

If you are not looking for your "C" drive either directly in Linux or via Wine, then you need to post back telling us exactly how you are looking for it and where.

---

### Post by spudarthur on 2012-05-24
I'm looking for c drive in my home folder under devices. I saw c drive before I installed wine but then I uninstalled wine now. I can't look from there. My primary problem is not focused on finding c drive, I just want to install some software from the software center. I still got 12 GB left on my C drive but still I get a message When I install new software I don't have enough space again.

---

### Post by anewguy on 2012-05-24
Well, if by "C" drive you mean (a) your only disk drive or (b) the drive you installed Windows and Ubuntu to, then we need to look at a few things.

Your opening post said you dual-boot.  Is this a true dual-boot, or did you do a wubi (ubuntu inside of Windows) install?

The 12 gig you have free - is that from Windows?  If you installed a true dual-boot - ubuntu in it's own partition(s), then you need to look at the free space that ubuntu thinks it has, not Windows.  You need to check in ubuntu (and remember, there is no such thing as "drive C" in ubuntu) to see how much free space it thinks it has left.

EDIT:  forgot to tell you HOW to check free space in ubuntu:  open a terminal window and type df -h and press enter.  You'll see a total percentage used.

When you installed ubuntu, how much disk space did you give it?

Dave ;)

---

### Post by spudarthur on 2012-05-25
Here's my free space, I guess. 

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      4.5G  4.5G  2.6M 100% /
udev            988M  4.0K  988M   1% /dev
tmpfs           399M  808K  398M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            996M  284K  996M   1% /run/shm
/dev/sda1        38G   25G   13G  67% /host

I meant C drive by B)the drive you installed Windows and Ubuntu to and I used wubi for the dual boot. Thanks for being kind

---

### Post by spudarthur on 2012-05-25
When I install something via software center, this is what I get all the time.

Failed to load the package list
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.
Details
E:Unable to synchronize mmap - msync (28: No space left on device), E:The package lists or status file could not be parsed or opened.

---

### Post by anewguy on 2012-05-25
I'm not sure how to interpret the output when it's a virtual drive since you used a wubi install.  I'll see if I can find a wubi expert to help you out further.  At first glance it looks full (only 2.5mb free of 4.5gb).

Sorry I can't help you further, but I'll get a wubi expert over here as soon as I can.

Dave ;)

---

### Post by roelforg on 2012-05-25
> **anewguy said:**
> I'm not sure how to interpret the output when it's a virtual drive since you used a wubi install. I'll see if I can find a wubi expert to help you out further. At first glance it looks full (only 2.5mb free of 4.5gb).
 
Sorry I can't help you further, but I'll get a wubi expert over here as soon as I can.
 
Dave ;)
 
I run a wubi install and i know a lot about disk images (and that's what wubi uses to store the filesystems) and mounting/running from them as root (build my own ubuntu livecd initrd from scratch and wrote the mounting and rest of the boot myself, e.g i did not create a standard one but one that doesn't use the normal systems), would i qualify?
 
Anyways,
try running this command, it may take a while (mine takes about 10 minutes, i've got a copy of the linux kernel source in my home folder (about 40000+ files) so it takes a while for me; please ignore any permission errors it gives you as they're normal and don't matter):
```

du -chs /home

```
I'd like to know the output.

---

### Post by bcbc on 2012-05-25
> **spudarthur said:**
> Here's my free space, I guess. 

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      4.5G  4.5G  2.6M 100% /
udev            988M  4.0K  988M   1% /dev
tmpfs           399M  808K  398M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            996M  284K  996M   1% /run/shm
/dev/sda1        38G   25G   13G  67% /host
```

I meant C drive by B)the drive you installed Windows and Ubuntu to and I used wubi for the dual boot. Thanks for being kind

You have a minimum install (your virtual disk is 4.5G). It's full. I'm surprised it can even boot with only 2.6M available. Maybe next time you try it will fail. 

And you only have 13G free on the host partition.

1. Move personal data from /home to /host (not likely to be much but even a couple hundred MB will help
2. Free up unneeded packages and cache
```
sudo apt-get autoremove
sudo apt-get autoclean
```

3. Clear your browser cache (this can be up to 500MB easily depending on how long you've used it)

4. Keep only the last two kernels (each one can save ~140MB)
There's some code here for that: 
```
OLD=$(ls -tr /boot/vmlinuz-* | head -n -2 | cut -d- -f2- | awk '{print "linux-image-" $0}')
if [ -n "$OLD" ]; then sudo apt-get remove --purge $OLD; fi

```

5. Resizing
You don't have much option since your root.disk is 5GB and you don't want to eat too much of the 13G for Windows. And your Windows partition is already very small.
You can create a separate virtual disk for /home as I believe *roelforg* is suggesting. 

You could do an [inplace resize]("https://help.ubuntu.com/community/ResizeWubiDisk") from a live CD and bump it a couple of GBs. 

But personally I don't see a lot of wiggle room for running two operating systems on a 38G partition long term.

---

### Post by anewguy on 2012-05-25
Thanks, bcbc.  I suspected it was full from the output I requested, but I don't know wubi so I didn't know if the disk was dynamic or not.

Dave ;)

---

### Post by bcbc on 2012-05-25
> **anewguy said:**
> Thanks, bcbc.  I suspected it was full from the output I requested, but I don't know wubi so I didn't know if the disk was dynamic or not.

Dave ;)

No prob :)  It would be nice if they were (a little) dynamic... like a virtual machine. But I don't believe a loop device that's mounted can be resized. Maybe *roelforg* can answer that one.

I guess it wouldn't take long to find out...
> The resize2fs program will resize ext2, ext3, or ext4 file systems. It can be used to enlarge or shrink an unmounted file system located on device. If the filesystem is mounted, it can be used to expand the size of the mounted filesystem, assuming the kernel supports on-line resizing. (As of this writing, the Linux 2.6 kernel supports on-line resize for filesystems mounted using ext3 only.).

---

### Post by anewguy on 2012-05-25
Then again, as you said, the entire hard disk is way too small to try to run both OS's on anyway.  That 4.5gb for wubi - I don't think that's even the minimum they recommend for a normal ubuntu install.

So, to the OP:  as I suspected, and as bcbc has shown, your virtual disk for wubi is full.  There really isn't enough free space for ubuntu to really boot, so you're lucky it even does that.

Also, as bcbc has pointed out, your entire hard disk that has both Windows and Ubuntu on it does not have much free, and really is barely big enough to run just Windows in comfortably (considering what most people do with Windows, and if you install extra programs).

While I'm a fan of Ubuntu, right now your best choices are:
[LIST]
[*]either completely remove Windows or Ubuntu from your system
[*]buy a larger hard disk (preferably not less than 100gb)
[/LIST]

We're sorry to be the bearers of bad news, but there isn't much way around it.

Dave ;)

Much thanks to bcbc!

---

### Post by zurgo1 on 2013-04-13
I'd like to know where the virtual c:/ drive from the application wine is??? Any chance of you knowing this??:popcorn:

---

### Post by deadflowr on 2013-04-13
> **zurgo1 said:**
> I'd like to know where the virtual c:/ drive from the application wine is??? Any chance of you knowing this??:popcorn:

Did you happen to read through this by chance?
[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)
Anyway, the c drive in wine is located in the users home folder.
It's in the .wine folder, which is a hidden folder.
To unhide, click ctrl + h, which will show the hidden folders/files.
Look for .wine and open it. The c drive is in there.

---

