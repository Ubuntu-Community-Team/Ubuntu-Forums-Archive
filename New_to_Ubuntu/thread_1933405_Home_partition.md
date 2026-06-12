---
title: "Home partition"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by Inisfad on 2012-02-29
I am preparing to get ready to update my Lucid distro to Pangolin within the next few weeks.  In the past, I have updated, rather than a clean install, and now think that my distro is filled with downloads and files that I really don't need or use. I currently have a dual boot - a small partition with Windows, and the main partition with Ubuntu plus the small swap partition.  I have been reading about having my home folder in a separate partition, so that, when upgrading, I am able to keep my files and settings, and do a clean install each time.  I have been reading about this on various websites, and often find conflicting and confusing information. Would it be possible for someone really explain the benefits of having a separate home partition, and to list the step by step procedure that must be done to get the home partition, so that a newbie can understand it?  Really appreciated!!

---

### Post by grahammechanical on 2012-02-29
The benefits first but to give step by step takes longer.

Imagine something going wrong with the OS to such a degree that a re-install is necessary. If you have a separate /home partition you can re-install the OS into the / partition and reformat that partition without losing the data and documents in the /home partition. It is a quick and painless way of getting back to a working computer.

It is always best to make backups of important documents before doing this. I have upgraded from 11.04 to 11.10 in this way without losing any data. During the month of May I will upgrade my 11.10 install to 12.04 by doing a clean install.

I am also considering backing up everything that I want to keep in my /home partition and then re-formatting the /home partition at the same time. I feel that it is sometimes beneficial to clean out the /home partition in this way from time to time. As you have noticed, stuff that we do not need gets left on the computer.

That is all for now.

Update:

It is easier to create a /home partition when first installing or doing a re-install than trying to do it while keeping the present Ubuntu installation. Here is a link to a guide. Please study it.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

The information is a bit old but the principles and methods are correct even if the actual screen images look different to these ones.

I suggest that you do some preparation by running the latest live CD in Try Ubuntu mode and then running the Partition manager and making a note of your present partition layout. This will get you used to using the partition Manager and will help in deciding what sizes to use for your partitions.

Regards.

---

### Post by mapes12 on 2012-02-29
I used to be a big fan of having a separate /home partition but after using Ubu as my main machine now for 5 years I have reservations. Having /home separate is great if you break your OS and you need to install it quickly with the _same version_ of Ubu. You just reinstall the OS to /(root) and leave /home alone (excuse pun) except telling the installer where it is. The problem comes when you are upgrading. /home contains tons of hidden files some of which change with different versions, hence your observation that your system is becoming stacked up with old files. The same happens when you uninstall software packages. Sometimes the applications hidden file doesn't get removed. So these days I have a separate /data partition that I use just for my stuff. This way I keep my stuff and the hidden files in /home apart. So, to do an upgrade I do a clean install. The only problem with my config is that I need to keep a note of settings for some apps that I would otherwise loose. For example, I backup using Grsync but the config for how I like Grsync is in one those hidden files in /home. But it works for me.

Good luck :)

---

### Post by forrestcupp on 2012-02-29
I'm personally not a fan of separate partitions. One reason is because you're limited to whatever size you set for everything. Later, if you decide you didn't set the partition sizes how you should have, it's a real pain and risk to resize them.

Another reason is that I don't trust or prefer it when I'm upgrading to a new version. One of the great things about version upgrades is seeing the new changes. Sometimes when you use the same /home folder, you force all of your old user settings, and don't even notice some of the changes. So my preference is to back up all of the files I care about and restore those backups after doing a clean install. The .wine folder is one that's important to not forget to backup, though, if you use Wine.

But that's just my preference. There are some pluses about having a separate /home. If you multi-boot various distros, you can mount the same partition for each, whereas, you'd have to have multiple separate /home folders if you don't have it on a partition. Also, there's the other side of the upgrade thing. Some people would rather keep their old settings so they don't have to set everything up again. It's just good to know that some of those things don't always carry over.

I guess my honest preference is to usually just do an upgrade and not even do a clean install at all. But if I need to do a clean install, I'd rather just back up my files, and not have a separate partition.

---

### Post by miegiel on 2012-02-29
> **mapes12 said:**
> ... 

The problem comes when you are upgrading. /home contains tons of hidden files some of which change with different versions, hence your observation that your system is becoming stacked up with old files. The same happens when you uninstall software packages. Sometimes the applications hidden file doesn't get removed. 

...

Good luck :)

I've been using a separate /home partition and "saving" what I have there since hardy. When I reinstall to a newer version of (x)ubuntu I just dive in my hidden directories en files and remove old junk, but most of it I prefer to keep. It saves me a lot of time getting my "look & feel" back the way I like it.

BTW, it's "normal" that stuff in your home doesn't get removed when you uninstall programs. There are good reasons why, but I'll skip on elaborating on that.

---

### Post by oldfred on 2012-02-29
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I often suggest a separate /home partition to new users to get them started on having more than just / (root). New clean installs then can be easier as you just have to select your current /home but DO NOT format /home as part of the install. All you data then is preserved. But you still should have backups.

You may also want a separate shared NTFS partition. That was the first additional partition I created and had my Firefox & Thunderbird profiles in the NTFS partition. I do not use XP much but still have not moved the profiles into Linux partitions.

But I also am like mapes12 and have separate Linux data partition. My /home only has the user settings and .wine which I understand is difficult to move. Because /home now is only 1 or 2GB and most is .wine I now leave it in / (root) and copy user settings in /home to new install. I keep / at about 20 or 25GB and have data in large partitions.

More discussion here:

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by jerome1232 on 2012-02-29
> **forrestcupp said:**
> I'm personally not a fan of separate partitions. One reason is because you're limited to whatever size you set for everything. Later, if you decide you didn't set the partition sizes how you should have, it's a real pain and risk to resize them.

One solution for that (for advanced users) is to use LVM, it makes it very easy to grow partitions later on, even while the system is up and running.

---

### Post by mapes12 on 2012-02-29
> One solution for that (for advanced users) is to use LVMWhat is LVM? Never seen this as an option in GParted and good ole Google doesn't recognise it either? And why is it only the privy of "advanced" users? How are you defining "advanced"?

:confused:

---

### Post by oldfred on 2012-02-29
LVM is logical volume management. It gives you flexible or logical partitions across physical bountries. Even across hard drive. It does add a layer of complexity to give flexibily. You cannot use gparted but have to use the LVM tools to manage partitions. I just resize if need be, and often by the time my drive has filled up, I buy a new much large drive as I know drives do not last forever anyway.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by audiomick on 2012-02-29
My 2 cents: I'm really in favour of using a separate /home. It has saved me loads of grief a number of times. I had cause to appreciate it once again this evening. I had re-installed last week after breaking something by fooling around too much. Tonight I noticed that syncevolution was missing, a package for sychronising Evolution with things like Funambol and telephones. I reinstalled and started it, expecting to have to set it up again, but I didn't. It just found the config files in the /home folder and off it went.

 I'm going to redo my /home soon. I think that is not a bad idea now and then to get the dross out, but to give you and indication of how long it has been going, one of the reasons I am going to re-new it is that it is still formatted to ext3. ;)

---

### Post by jerome1232 on 2012-02-29
Oldfred; That's one reason I like LVM, I can pop the new drive in, add it to the volume group, migrate the volumes over to it, remove the old drive from the volume group or keep it and let the volumes span over the disks. No need to image over etc, and aside from the actual physical installation of the disk, the system can be up the entire time.

That being said, I only use it (lvm) on my little home server since I enjoy that flexibility there. With my desktop I just stuck to a big / partition, I dual boot with windows and didn't want anything complex. Most of my irreplacable data is stored on a external drive and I use symbolic links to make it "transparent" to me. This way if I ever need to reinstall etc... my configurations get wiped out, only my personal data will remain intact, and that's the way I want and like it.

---

