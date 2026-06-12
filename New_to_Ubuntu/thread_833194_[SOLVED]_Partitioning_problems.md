---
title: "[SOLVED] Partitioning problems"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by hedniskhjartad on 2008-06-18
Hi,
I've forever been a windows user, and only now have i decided to install linux (specifically ubuntu). I'm trying to use the os installer partitioner to partition my one physical drive to be able to dualboot xp and ubuntu.
I tried looking up guides, but some were for command prompt installers, some showed options differently, some were for other versions of ubuntu. the version i'm trying to install is ubuntu 8.04. I thought of using the guide that i've linked below (and have also looked at the stickied thread in the beginners forum here), and either couldn't find an answer, or didn't understand what i was seeing.

```
http://www.psychocats.net/ubuntu/installing
```

In that guide, it says that once the partitioner comes up in the installation process, it should give me 4 options:
1)Guided resize and use freed space
2)Guided - use entire disk
3)Guided - use the largest continuous free space
4)Manual (for intermediate to advanced beginners).

It doesn't though... it gives me only two options:
1)Guided - Use entire disk
       SCSI1(0,0,0)(sda) - 80gb ATA WDC WD800BB-00JJ
2)Manual.

So I have two questions:
1) Why don't I get the other two options, one of which seems very relevent to what i want to do?
2) How do i progress?

Any help would be appreciated.

---

### Post by yragrelluf on 2008-06-18
use manual, and make sure you adjust the "slidebar" to where you would like it to be, so your two OS have the appropriate amount of disc space. I don't know why you arent getting the other choices, but you shouldn't need them.

---

### Post by forestpixie on 2008-06-18
Have you defragged - it is important that you do - at least twice. You could alos get the auslogics defrag which seems to do a better job of it.

If you still have a very defragmented drive - turn off the pagefile and do it again, then turn pagefile on again.

[http://www.auslogics.com/en/software/disk-defrag/download](http://www.auslogics.com/en/software/disk-defrag/download)

I think that if there is not enough contiguous space then it can't give you the other options.

---

### Post by hedniskhjartad on 2008-06-18
> **yragrelluf said:**
> use manual, and make sure you adjust the "slidebar" to where you would like it to be, so your two OS have the appropriate amount of disc space. I don't know why you arent getting the other choices, but you shouldn't need them.

So if I click manual, it brings me to the "prepare partitions" screen. Here, I see my one NTFS partition. If I click on "edit partition, it says "use as", and the options for file system are:
ext2
ext3
reiserFS
and so on...
I chose Reiser. Then there's a format check, and below it is "mount point":
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

I don't know what to choose there.
But even if i randomly select something and click next, it commissions the entire hard disk again for switching to reiser, instead of creating another partition. I saw no slidebar either. The next step would have committed me to the changes, so I stopped.

---

### Post by hedniskhjartad on 2008-06-18
> **forestpixie said:**
> Have you defragged - it is important that you do - at least twice. You could alos get the auslogics defrag which seems to do a better job of it.

If you still have a very defragmented drive - turn off the pagefile and do it again, then turn pagefile on again.

[http://www.auslogics.com/en/software/disk-defrag/download](http://www.auslogics.com/en/software/disk-defrag/download)

I defragged the drive and checked the drive for errors. once I was done defragging, windows defragger reported no further need to defrag. since you say at least twice, i'll run it once or twice more and then try the installer again.

---

### Post by MasterSander on 2008-06-18
You first have to resize your ntfs partition in windows. You can do this by going to the config screen and type in partition in the search box (use new view of config screen), then shrink it to how many disk space you'd like to have ubuntu. Then start the livecd and install. Pick manual at partition screen, set 1 gig of the free space as SWAP, and the rest as ext3 and as mount point on that /

---

### Post by forestpixie on 2008-06-18
How much room do you have on your drive that you want to use for ubuntu - you might be better using the partition editor to get it right.

You will need at the minimum 2 partitions - 1 for root and 1 for swap.

---

### Post by forestpixie on 2008-06-18
> You first have to resize your ntfs partition in windows.Does have xp have a partition editor?

---

### Post by MasterSander on 2008-06-18
I think they do, vista has one anyway, I thought he was using Vista :S. The ubuntu resizer can't resize NTFS. Always resize in windows, if needed with anoher resizer than the standard.

---

### Post by Hamchan on 2008-06-18
You want to leave the NTFS as NTFS (that means it's your windows partition, changing this to EXT3 would delete everything windows). You just need to resize it to make room for an EXT3 filesystem

---

### Post by Colin82 on 2008-06-18
One caveat on the swap partition, if it is a laptop and you plan on using hibernate/suspend, make your swap partition at least the same size as the amount of memory you have.  Since hibernate writes everything on the memory to HDD, you will have issues if your swap is not big enough.

---

### Post by hedniskhjartad on 2008-06-18
> **MasterSander said:**
> I think they do, vista has one anyway, I thought he was using Vista :S. The ubuntu resizer can't resize NTFS. Always resize in windows, if needed with anoher resizer than the standard.

thanks for all the help people. 
MasterSander, I'm using xp, but i have a third party partitioner. I didn't know the ubuntu installer couldn't resize an ntfs partition. that could be the reason i'm not seeing a resize bar in manual.

---

### Post by forestpixie on 2008-06-18
> The ubuntu resizer can't resize NTFS gparted will resize ntfs afaik - I've used it many times. Never use the resizing bit of the installatio process to do it though.

---

### Post by avtolle on 2008-06-18
Another possible reason is that for some reason the partition is mounted. You are trying this from the installation CD (Live CD), correct? Sometimes, while using gparted on the Live CD, a partition is mounted for reasons I cannot explain. If this is happening unmount the partition and try again.

---

### Post by melrom on 2008-06-18
> **forestpixie said:**
> gparted will resize ntfs afaik - I've used it many times. Never use the resizing bit of the installatio process to do it though.

Yes. I exclusively trust gparted to do things with partitioning.

Pop open a terminal. Type

```
sudo gparted
```

Click on the NTFS partition. Click on the button that says, "Resize/Move". It is an orange arrow. Then, you will be able to select a new drive size by sliding the arrow, or specifying a specific number of gigs for your new NTFS. Click apply. This will resize the Windows partition.

Here are some pretty pictures to go along with what I just explained:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

After this, you should be able to go into the Ubuntu partitioner and select, "use the largest amount of free space." The Ubuntu partitioner will do the work. :)

---

### Post by hedniskhjartad on 2008-06-18
yes, I am using the live cd. i'll look for an unmount option when it comes back up, just went back into windows for a second. if this whole operation fails, i'll get the command prompt installer, or try to get a friend over and stand at his shoulder.

---

### Post by melrom on 2008-06-18
> **hedniskhjartad said:**
> yes, I am using the live cd. i'll look for an unmount option when it comes back up, just went back into windows for a second. if this whole operation fails, i'll get the command prompt installer, or try to get a friend over and stand at his shoulder.

Try resizing with gparted. Then see if anything more comes up on the installer menu [i.e. use largest amount of free space].

P.S. YAY for being from NJ!!!

---

### Post by phoenix_abhi on 2008-06-18
First u have to check whether ur shutdown the XP properly,if yes, log back to XP delete a partition of the windows through disk management (for ubuntu installation) and do not format it. Reboot with Live Cd inserted and select install to hard disk.
In the partition select manual method. First select a logical partition and use it as swap. it should be 2x of ur RAm. Part the remaining disk to '/' (root) and /home as per requirement. Remember keep the home folder largest. Continue the installation process

---

### Post by hedniskhjartad on 2008-06-18
melrom: yay back =D

I'm going to try doing what you said with gparted. If that doesn't work, I'll create another partition through windows, delete it (like phoenix_abhi says) and try to have the installer work with that.

thanks a lot for everyone's help.

---

### Post by forestpixie on 2008-06-18
I really would suggest using the partition editor that is included on the livecd in the system admin menu to deal with it.

If you haven't got a spare partition, which I doubt, you can't go into windows tro delete one.

You do not need to have seperate /home although it can be useful, it depends on how much room you have as to whether you should do it.

---

### Post by phoenix_abhi on 2008-06-18
> **forestpixie said:**
> I really would suggest using the partition editor that is included on the livecd in the system admin menu to deal with it.

If you haven't got a spare partition, which I doubt, you can't go into windows tro delete one.

You do not need to have seperate /home although it can be useful, it depends on how much room you have as to whether you should do it.

I suggested him to do the all job in windows coz he said in his post that he is new to Ubuntu. for newbies partitioning through window partitioner is the easy method. Resizing with Gparted required some more idea which u people are not provided

---

### Post by hedniskhjartad on 2008-06-18
> **forestpixie said:**
> I really would suggest using the partition editor that is included on the livecd in the system admin menu to deal with it.

If you haven't got a spare partition, which I doubt, you can't go into windows tro delete one.


What I meant to say was that I would instead use a windows based partitioner that I am familiar with, to first create a partition, then remove it to create unallocated space; but I see your point. Instead of going into the installer, i'll load up the "try ubuntu without installing" feature, and look for the partitioner there.

---

### Post by forestpixie on 2008-06-18
Try it - it's in the sys/admin menu - I can understand you wanting to use apps you are comfortable - I started the installer about 3 times before I said go :)

Also from the livecd you can get online assuming that you are connecting with a router so can ask questions before you hit go.

It might be worth working out how much room you are going to have availabla and asking about a partition scheme - you can do all of these steps in the partition editor so that when you do go into the installer it is much simpler.

---

### Post by melrom on 2008-06-18
> **forestpixie said:**
> I really would suggest using the partition editor that is included on the livecd in the system admin menu to deal with it.



that's gparted...

---

### Post by forestpixie on 2008-06-18
Yes I know :) - just trying to make it easy for the op - in the menu it's called partition editor and I'm trying to differentiate between the editor in the installer and the one in the menu.

I personally prefer to use partedmagic now after I had a few problems with gparted not booting and stuff.

Everyone should download and burn themselves a copy of a partition editor and supergrub - partedmagic comes with testdisk and other bits and bobs and I can get ti to use the lan as well, useful to have firefox.

[http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic](http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic)

---

### Post by hedniskhjartad on 2008-06-18
i've got bigger problems... gparted/that partition manager is reporting my hard drive as having bad sectors. It's an extra office computer, so i'm calling the tech guy right now...
This thread's basically solved my questions; it's my hardware that's acting up. I know almost exactly what to do once i get a replacement drive. Thank you very much! :)

---

### Post by yragrelluf on 2008-06-18
I dont know why you guys are saying that the partitioner on the liveCD/install disc cannot resize an nfts partition, because it can. I used it to set up a dual boot vista/hardy system, before I decided to remove anything windoze related. Well. do what you like, but this is being turned into a bigger project than it needs to be. P.S. I doubt their is hardware issues if you are still able to boot windows.:lolflag:

---

### Post by melrom on 2008-06-19
> **yragrelluf said:**
> I dont know why you guys are saying that the partitioner on the liveCD/install disc cannot resize an nfts partition, because it can. I used it to set up a dual boot vista/hardy system, before I decided to remove anything windoze related. Well. do what you like, but this is being turned into a bigger project than it needs to be. P.S. I doubt their is hardware issues if you are still able to boot windows.:lolflag:

the Ubuntu partitioner *can* resize NTFS. This wasn't the issue. That option never came up for the OP, as indicated here: 

> **hedniskhjartad said:**
> 

It doesn't though... it gives me only two options:
1)Guided - Use entire disk
       SCSI1(0,0,0)(sda) - 80gb ATA WDC WD800BB-00JJ
2)Manual.

So I have two questions:
1) Why don't I get the other two options, one of which seems very relevent to what i want to do?
2) How do i progress?


So we were suggesting that the OP use gparted, which is also included on the live CD.

-Melissa

---

