---
title: "root partition size?"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-06-24
basically right now my setup is 4gb for swap and 390gb for basically the whole ubuntu installation. i was advised on this forum to do a home partition for when i want to upgrade that its easier and stuff like that. i didnt listen or in other words i didnt mind not having a home partition since i have all my files sorted out and can always move them to my external when i need to reinstall the os, repartition, etc. 

so heres the question, how much space does it give to the home directory? how much space does it give to other directories that get installed with the ubuntu installation? basically im asking because in case i wanted to make my /home directory as a seperate partition then what is the minimalist that should be given to the "/" partition?

---

### Post by MidnightGrey on 2013-06-24
> **mreyna16 said:**
> 

so heres the question, how much space does it give to the home directory? how much space does it give to other directories that get installed with the ubuntu installation?

Since you only have one partition, all your files are stored in that partition and share the storage space (of 390 GB) meaning you can have up to 390 GB of data in any of your folders (/ or /home or anything else). There is no space restriction on any one folder within the partition itself.

---

### Post by dave0109 on 2013-06-24
My root (/) partition is currently 7.5GB for Xubuntu 13.04.  When I did the upgrade from 12.10 recently, that increased temporarily to nearly 11GB.  I would expect standard Ubuntu to require a little more, but it depends on which packages you have.

My partition is actually 40GB so there's plenty of space for it to grow as I try different software or perform upgrades.

You can also see how big your current space requirements are, by bringing up a terminal and using:-
```

du -sh --exclude=/home /

```

---

### Post by mreyna16 on 2013-06-24
thanks guys, for me i find it just simpler to leave it the way it is... not that im scared of having a seperate home directory or making one, i mean thats what linux is all about (the do it yourself kinda thing) but like i posted, i dont mind getting all my info out since i have everything in order

---

### Post by fantab on 2013-06-24
The only problem with not having a separate '/home' or 'data' partition is that when you have to do re-install or install a newer version Ubuntu you'll be forced to back up all your data. If we have a separate partition for our data then we can simply format the '/' partition and install Ubuntu or any other distro without worrying about data loss.

If you have more that one distro or different versions of Ubuntu then separate '/home' too can create problems, as /home or just Home folder also stores your application settings and preferences in hidden dot folders. If different distros have diifferent versions of the same application then there will be conflicts and problems with those applications.

I boot multiple distros, so I have a separate 'data' paritions which is a simple parition formatted with ext4 without any mountpoint. I manually mount this parition as and when needed. If you want we can automount this data parition at system start by editing /etc/fstab.

My two cents...

---

### Post by 3rdalbum on 2013-06-24
In the olden days, installing or reinstalling Ubuntu would erase everything in / including the /home. That is why a different partition was recommended.

Since 2009, Ubuntu's installer has been smart enough to preserve your /home even when it is in the same partition as /

People still give the old advice because they don't know the Ubuntu installer that well. But as long as you choose the "Upgrade" function in the installer, or choose "Something Else" and don't elect to format / your home directory will be preserved. And your package set will be reinstalled, too.

---

### Post by mastablasta on 2013-06-24
having separate root and home is like separating C:\ and D:\ in widnows where you would put My documents on D:\

btw i have xubuntu on 8GB drive. the problem is i would have to clean it after every update. it still leaves about 2 GB for various programmes and files.

---

### Post by fantab on 2013-06-24
> **3rdalbum said:**
> 
Since 2009, **Ubuntu's installer has been smart enough to preserve your /home even when it is in the same partition as /**

People still give the old advice because they don't know the Ubuntu installer that well. But as long as you choose the "Upgrade" function in the installer, or choose "Something Else" and don't elect to format / your home directory will be preserved. And your package set will be reinstalled, too.

Well, I didn't knew that.
Can you please direct me to where I can learn more about 'Ubuntu installer'. 

Thanks for the info. 

Though I will confirm with the old school and keep my data separate. Its too much of a risk to trust the installer with my data.

---

### Post by 3rdalbum on 2013-06-24
> **fantab said:**
> Well, I didn't knew that.
Can you please direct me to where I can learn more about 'Ubuntu installer'. 

[https://wiki.ubuntu.com/Ubiquity](https://wiki.ubuntu.com/Ubiquity)

It's just the regular installer for Ubuntu, the one that runs from the live CD or Desktop CD.

> Thanks for the info. 

Though I will confirm with the old school and keep my data separate. Its too much of a risk to trust the installer with my data.

I've found it to be very reliable. I've done it multiple times on two different computers with no problems*. I've never lost data with it.

Don't get me wrong, there are still good reasons to have a separate /home partition: You have a lesser liklihood of filesystem corruption affecting your data, and if you've already got a /home partition there's no benefit to moving it back onto the / partition. Other Linux distros can't preserve /home if it's on the same partition as /, so if you want to try any Linux distro that's not based on Ubuntu you should have a separate /home. On my main desktop I have /home on a different hard disk altogether, although this is for speed reasons and "because I can".

My father's computer and my laptop have /home on the same partition as /, and as I say, I have had no problems*.

*The "preserving /home" feature appears to be incompatible with btfs filesystems, although you shouldn't be using btfs because it's not stable yet. I still didn't lose any data, the installer just refused to continue.

---

### Post by oldfred on 2013-06-24
I have seen what used be called a "dirty install" where you just did not click the reformat. But do not suggest it. Not sure if then you do not get any housecleaning of old kernels & logs and all the other cruft that builds up over time.

 Over install without formatting to reuse same home data. 
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by grahammechanical on 2013-06-24
> [COLOR=#000000]*The "preserving /home" feature appears to be incompatible with btfs filesystems, although you shouldn't be using btfs because it's not stable yet. I still didn't lose any data, the installer just refused to continue.[/COLOR]

I am running Saucy Salamander on btrfs right now. I have all my data on a separate partition. The issue is not so much with btrfs but with Grub os-prober not being able to read a btrfs partition. It will not detect Ubuntu on a btrfs partition and Ubiquity, when installing Ubuntu on to btrfs, may fail to install grub into the MBR unless we are using a separate boot partition or left at least 1GiB of unallocated space at the beginning of the drive.

This has been the experience of a couple of us on the Ubuntu+1 section after recent testing. I cannot comment on the reliability of btrfs as a file system. I am trusting it now with what I will use as my rolling development release. I like the roll back feature. I do know that there is almost a complete lack of a GUI btrfs management utility and that, in my opinion, prevents btrfs from being used by ordinary Ubuntu users.

Regards.

---

### Post by mreyna16 on 2013-06-24
hmm ill keep in mind all of this info, maybe in october when the newer version is out ill create a seperate /home partition. if i do happen to do that i would probably like most of my space on that partition. so giving the / partition 10gb of space should be enough? or should i go higher just in case? and just to understand the / partition, what exactly is stored there? temporary files that are needed when theres updates and stuff like that?

---

### Post by Impavidus on 2013-06-24
The OS, programs, libraries, program data, system configuration, logs etc. 10GB for / may work, but is small. Better make it maybe 20GB. I don't think you'll notice the difference between a 370GB /home and a 380GB /home. If you can fill one, you'll need just another month to fill the other.

---

### Post by mreyna16 on 2013-06-24
just to make sure, 20gb more than enough? or 30 just to make sure?

---

### Post by Impavidus on 2013-06-24
30GB to be really sure. It depends on what you're going to install. Some programs (flight simulators and planetarium programs come to mind) store a lot of data on your root partition. If you use programs like those, make / larger than 20GB, or put their data on another partition.

---

### Post by monkeybrain2012 on 2013-06-24
If you have separate /home and / all your install software goes to /, so if you install a lot of stuffs it doesn't hurt to make it bigger. If you install paid software from third parties they tend to be big (I heard Matlab, e.g may use 3g+ ) you should take that into account too (but I think you can install those in /home as well, normally). I think normally though  12-15G would be quite comfortable, 20G would be ample (unless you have some special programs that store a lot data in / like impavidus says above and some games)

---

### Post by C0R3T3CH on 2013-06-24
The root partition depends on the person. If you are going to have a lot of users or packages, separate /usr and /home from /

---

### Post by mreyna16 on 2013-06-24
no itll only be me using this laptop... and i dont use paid programs (as of yet) so then lets say i leave it at 20gb for the / partition, IF i ever run out of space i can always take some away from my /home partition (200+ gb) and make my / partition bigger right?

---

### Post by Impavidus on 2013-06-25
Yes, you can, but shrinking one partition to add space to the other can be quite a time consuming job, with the added risk of file system corruption if anything goes wrong during that time (like a power failure). Alternatively, you can leave some unallocated disk space inbetween the / and /home partitions, that you can add to either of them whenever the need arises. Expanding partitions into unallocated space is relatively save and quick.

---

### Post by mreyna16 on 2013-06-25
true, good point... well thanks for the advice guys, ill keep it in mind

---

### Post by mikodo on 2013-06-25
> **grahammechanical said:**
> I am running Saucy Salamander on btrfs right now. I have all my data on a separate partition. The issue is not so much with btrfs but with Grub os-prober not being able to read a btrfs partition. It will not detect Ubuntu on a btrfs partition and Ubiquity, when installing Ubuntu on to btrfs, may fail to install grub into the MBR unless we are using a separate boot partition or left at least 1GiB of unallocated space at the beginning of the drive.

This has been the experience of a couple of us on the Ubuntu+1 section after recent testing. I cannot comment on the reliability of btrfs as a file system. I am trusting it now with what I will use as my rolling development release. I like the roll back feature. I do know that there is almost a complete lack of a GUI btrfs management utility and that, in my opinion, prevents btrfs from being used by ordinary Ubuntu users.

Regards.
I am glad you chimed in. Eventually, we will be using btrfs in linux when it is ready. I was disheartened to hear from an earlier poster that we couldn't have a separate /home or /mnt/data partition with that FS. So, if we have to have a small boot partition at the beginning of the drive, so be it. Isn't that how windows does it? I am sure the guys will sort out the Grub2 stuff, before we masses start using it in linux. 

Thanks, for the clarification.

;p

---

