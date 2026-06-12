---
title: "Merging two partitions"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by sezhiana on 2014-04-13
Hi,

I have a Sony Laptop and it has 120 GB hard drive. I have both Windows XP and Ubuntu 13.10 installed. I am trying to increase the Ubuntu partition size. I resized the Win partition and so now i have 30 GB (sda3) of unallocated space. i want to merge it with Ubuntu partition (sda2). After reading in this or other forums, I got a live CD, booted with it and then merged both these to a 50 GB partition and then installed Ubuntu 13.10 in it afresh. Before doing that I used Clonezilla to make image of the hard drive. After I made the fresh Ubuntu 13.10 install and restored the diskimage using Clonezilla and I am back to square one - Ubuntu 20 GB and unallocated 30 GB and their drive #s have changed. How to do this the right way? I dont how to post the GParted result. It shows sda1 (ntfl - windows - 50 GB), sda3(ext4- 30 GB), sda2(extended, 20 GB), sda5 (ext4, mountpoint -/, 19 GB) sda6 (linuxswap, 1 GB).

Thanks for your help.

```
sezhiana@sezhiana-VGN-NR110E:~$ sudo fdisk -l
[sudo] password for sezhiana: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x62abe731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122882047    61440992+   7  HPFS/NTFS/exFAT
/dev/sda2       192491518   234440703    20974593    5  Extended
/dev/sda3       122882048   192489471    34803712   83  Linux
/dev/sda5       192491520   232364031    19936256   83  Linux
/dev/sda6       232366080   234440703     1037312   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Mark Phelps on 2014-04-13
When you restore using Clonezilla, it recreates the saved partition using the characteristics it had when you saved it.  So, basically, if you image off (for example) sda2 which is 30GB, then resize sda2 to 50GB, when you restore, it will be put back into the state (snd size) it was when you imaged it.

With other imaging tools, you have the option to MOUNT the saved image, turning it into a filesystem, from which you can "drag and drop" files and folders onto your hard drive.

Unfortunately, Clonezilla will not mount its image files, so I know of no way to copy the files and folders out of the image onto your hard drive.

---

### Post by sezhiana on 2014-04-13
Thanks Mark,

How can I add the unallocated space (sda3) to my ubuntu partition (sda2)? I have also backed up files using Backin Time.

---

### Post by monkeybrain20122 on 2014-04-13
Use fsarchiver instead of clonezilla, it just clones and restores the file system therefore much more flexible, it makes no difference where you restore the image to as long as the target partition is large enough to hold the contents. you can clone a partition and then do crazy things to change the partition size and hard drive layout and restore the image anywhere and it will still work.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by sezhiana on 2014-04-13
So your suggestion is to clone my system using FSArchiver, then boot from a LiveCD, use GParted to delete my Ubuntu partition (20 GB) and make one unallocated partition (50 GB), install ubuntu 13.10 in it and then restore my file system from FSArchier. Did I understand correctly?

Thanks.

---

### Post by monkeybrain20122 on 2014-04-13
What is the end result you want to achieve?  It would help if you can post a screenshot of the current layout of your drive (with gparted) and indicate how you want to change it.
Edited: It is not clear from your description why you want to make a fresh install of Ubuntu and then restore a clone over it.. it sounds a bit confusing to me.

With fsachiver you don't need to clone the disk, just the partitions.

---

### Post by sezhiana on 2014-04-13
I have a Sony Laptop and it has 120 GB hard drive. I have both Windows  XP and Ubuntu 13.10 installed. I am trying to increase the Ubuntu  partition size. I resized the Win partition and so now i have 30 GB  (sda3) of unallocated space. i want to merge it with Ubuntu partition  (sda2) so that it can become from 20 GB to 50 GB in size.

Thanks.

[IMG]/home/sezhiana/Pictures/GParted.jpg[/IMG]

---

### Post by oldfred on 2014-04-13
To attach a screen shot use Go advanced and in the edit panel use the paper clip icon to attached the screenshot. Do not put in line.

Your sda2 is the extended partition. That is just a container for all the logical partitions.

You cannot merge partitions, but if you have unallocated space that is not a partition then you can usually move a partition left and expand right. You may have to move other partitions around and the screen shot makes it easier to visualize.

---

### Post by sezhiana on 2014-04-13
[ATTACH=CONFIG]252035[/ATTACH]

---

### Post by monkeybrain20122 on 2014-04-13
What is sda5? What do you want to do with it?

---

### Post by oldfred on 2014-04-14
If you want a larger 50GB / (root) then you have to backup & delete sda3. Then you can expand extended partition left into the unallocated space to in effect move unallocated into the extended partition. Then you can move sda5 left and then expand to fill the space on the right. You must have good backups as moving a partition means it will be writing & rewriting all the data. Any interruption or power failure will corrupt a half moved partition.
You have to run that from live installer as all partitions must be unmounted. And even live installer mounts swap so you have to click on swap and unmount it.

A couple of other options are to just use sda3 as a data partition and mount with fstab and use the space for storing anything you want.  Bit more advances as you have to mount, give yourself ownership & permissions and link folders in your data partition back into /home so data partition is easily used.

Or you can move /home into sda3.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by monkeybrain20122 on 2014-04-14
You said Ubuntu is on sda3 (but it actually looks like it is on sda5) What you can do is clone sda3 (for which you don't need a live cd, fsarchiver can do live cloning), then delete it. shrink Windows, expand sda2 all the way to the left. Then I don't know what you plan to do with sda5. You can either create a new partition sda7 say to cover the recovered space from windows and what sda3 used to be (now all within sda2), so now you have sda7 sitting next to sda5,  or you can backup the data in sda5 and delete it and create one big ext4 partition sda7.

Then restore your clone to sda7 with fsarchiver, for this you need a live cd/usb (either a ubuntu one and install fsarchiver or a rescue cd with fsarchiver in it)

You also need an external device to store the clone.

This way you can avoid the writing and rewriting involved in moving/resizing partitions that old fred warned about.

**Edited:** if ubuntu is on sda5 (which looks more like it even though you said sda3), you can clone sda5, then delete it, delete sda3, shrink Windows, expand sda2, make a big ext4 partition sda7 inside sda2 that covers all the space recovered from Windows + sda3 used to be + sda5 used to be, then restore the clone to sda7.

You don't need the extended partition sda2 if you don't plan to add more partitions later.

You may need a Windows tool to shrink the Windows partition other than gparted.

---

### Post by Impavidus on 2014-04-14
+5 to oldfred's post #11

You can't simply merge partitions, but you can expand partitions into unallocated space. You called sda3 unallocated space, but it isn't really unallocated but only unused. It's allocated to sda3. There's only some file system overhead stored there. Your Ubuntu install is on sda5. So boot from a live disk, open gparted, turn swap off, delete sda3. Then expand sda2 to put the unallocated space inside the extended partition and then expand sda5. But simply using sda3 as /home partition is a good option too. Make sure you have backups of any vital files on your Ubuntu partition. Changing the partitions this way is quite safe, but unexpected things might happen.

I think that you shrunk the Windows partition (sda1) and then created a new ext4 partition, planning to merge it with sda5. That is not how we make partitions larger.

---

### Post by sezhiana on 2014-04-14
I think sda5 is the ubuntu partition (19 gb and mount point) and is a part of sda2 which is an extended partition also containing 1gb of swap (sda6). sda5 has all of my ubuntu stuff. I actually want to add the unallocated space (sda3) to sda5.

---

### Post by sezhiana on 2014-04-14
I have backed up my files using BackInTime. Is that enough or do I need to use FSArchiver and clone sda5?

Thanks.

---

### Post by Impavidus on 2014-04-14
A clone would make things complicated as you would be restoring to a larger partition than what you have now, but any copy of your user files (which can't be a lot, given your disk usage) on an external drive will do. Don't bother about the system files, if things go wrong you can easily reinstall. If all goes well using oldfred's instructions you shouldn't need your backups. Those instructions will add the space of sda3 to sda5.

---

### Post by monkeybrain20122 on 2014-04-14
> A clone would make things complicated as you would be restoring to a larger partition than what you have now, 

No, not with fsarchiver, that is the beauty of it. It only has to restore to a partition big enough to hold the contents. With clonezilla you need a larger drive, that's why I don't use it.

A clone actually makes things really simple in this case. With fsarchiver you can clone sda5 while it is mounted and for partition that size may take 20-25 minutes and restore is even faster and it is not risky like resizing/moving a bootable partition with gparted.

---

### Post by monkeybrain20122 on 2014-04-14
So for your setup the procedure is as follows.

Boot into sda5. install fsarchiver
```
sudo apt-get install fsarchiver
```
Attach an external media with about 20G capacity to hold the backup archive (actually it can be less as you don't have 20G of data and it will be compressed), create a folder called 'backups' in this drive. Find the device name with 
```
sudo blkid
```
Let's say the path to  backups is /dev/sdb1/backups
now run fsarchiver
```
sudo fsarchiver -a -A -v -j2  savefs /dev/sdb1/backups/ububak.fsa /dev/sda5 --exclude=junks1 --exclude=junk2
```
1)here -a -A are options that allow you to run fsarchiver to clone partitions currently in use. You can use ubuntu while cloning it but don't install/uninstall things or sync with dropbox etc for these will render the backup inconsistent. Going on internet, watching movie or listening to music, reading ebooks etc are fine.
2)-j2 means use two threads, you can use more if applicable. If you don't have multi thread just omit the option.
3) -v means verbose
4) --exclude is optional, to exclude directories that you don't want cloned. So to exclude Downloads will be --exclude=Downloads.
5) you can of course call the backup archive/clone anything, but it has to end with .fsa

Now you just wait for 20-25 minutes while you can listen to music, watch videos and what not.

When done. Shut down, shrink the windows partition  somehow. People have said that you should use Windows tools to shrink Windows and then run checkdisk. I don't use Windows and I don't know what tools are available or recommended so this will have to be a bit of a blackbox for me.

When this is done. Boot off a live usb, use gparted to delete sda5, sda3 and if you only plan to use two partition you can delete sda2 (the extended partition), otherwise you can extend sda2 to cover all the unused space. Create a new ext4 partition that covers all the unused space, say sda7. If sda7 lives inside sda2 (the extended partition) then it should be a logical partition. If you decide to delete sda2 then sda7 should be a primary partition.

Now unmount sda7. Install fsrachiver in live session. 
```
sudo apt-get install fsarchiver
```

This should work in the live usb as it doesn't require reboot (you can always make the usb persistent) but if for some reason it cannot access the repo or something there is a rescue live cd that contains fsarchiver.

Now attach the external device that holds the backup archive (ububak.fsa). Check the name of the device again with
```
sudo blkid
```
Note that when we did the cloning the device was /dev/sdb, but this may change as now you are on a live usb. Usually the bootable usb drive would become /dev/sdb. So let's say the device is now /dev/sdc

Run  fsarchiver to restore the backup
```
sudo fsarchiver -v -j2 restfs /dev/sdc1/ububak.fsa id=0,dest=/dev/sda7
```

Wait may be 10 minutes for it to complete, reboot, that's it. No need to reinstall programs etc.

Be careful about the dev and partition names, don't just copy and paste the commands. Check the names first.

---

### Post by monkeybrain20122 on 2014-04-14
> **sezhiana said:**
> I have backed up my files using BackInTime. Is that enough or do I need to use FSArchiver and clone sda5?

Thanks.

Backintime only backs up data, does not clone the system and you will have to reinstall the system and all the programs. If you have a simple install then by all means. But I find fsarchiver route simpler as everything is good to go after restore. The operation is really very simple and fast as there is no Moving/Resizing of the partitions involved except for the Windows partition, but that you have to do anyway.

fsarchive claims it can clone ntfs partitions as well, but I haven't tried it so I won't recommend it. I don't recommend procedures that I have not done myself.
 
**Edited:**I take great exception to the approach usually taken in this kind of threads: tell the user to just backup data and then reinstall. Well I don't really care much about the data as backing up data is more or less trivial and there are a gazillion of ways of doing it. It is backing up system that is interesting and you don't want to reinstall if you have install a lot of software and have optimized them to your liking, and you don't want to reinstall if a problematic update hoses your system. 

Now in your case using fsarchiver to clone -> reconfigure drive -> restore is much faster, safer, more elegant and 100x more flexible than the backup data -> resize/remove -> reinstall routine. Also, fsarchiver gives you much more flexibilities in reconfiguring your drive comparing to tools like clonezilla or redobackup.

---

### Post by sezhiana on 2014-04-14
Thanks 'monkeybrain20122' for your details reply. Unfortunately, I started the process as suggested by 'oldfred' and 'impavidus'. I backed up my data using Backintime and the booted using a liveCD (USB) and then deleted sda3 and then increased sda2 to include sda3 portion and then increased the size of sda5 to 50 gb. Rebooted and everything was fine.

Still I installed fsarchiver from ubuntu software center for future use. Should I use fsarchiver and periodically clone my system like data backup, to use in case of any system crash?

Thanks 'oldfred' and 'impavidus'.[ATTACH=CONFIG]252076[/ATTACH]

---

### Post by oldfred on 2014-04-14
Glad that worked.

You can never have enough backups, but of course failure always occurs just before you were going to do a backup. It depends on how valuable your data is on how best to backup.

Many like the image backups.

I tend to prefer just to backup /home and some other internal data and plan on a new reinstall. But I have several drives all bootable and do not expect them all to fail at once. Of course lighting could strike or house burns down and entire system is wiped.

---

### Post by erind on 2014-04-14
> **sezhiana said:**
> [...]

Still I installed fsarchiver from ubuntu software center for future use. **Should I use fsarchiver and periodically clone my system like data backup, to use in case of any system crash?**

[...]

Definitely! The more recent the backup the better*. In case of disaster you'd have a fully operational OS in a matter of minutes. 
***fsarchiver*** is worth every second of your efforts & learning ! 


[*] While *fsarchiver* can do live-backups, I prefer cold backups - the partition that is being cloned is unmounted, (* fsarchiver* is run from a, say, Live CD/USB ).

---

### Post by monkeybrain20122 on 2014-04-14
Other than catastrophes like hard drive failure and lightning strikes I use cloning for several purposes

1)  OS upgrade. Now 14.04 is going to be released. But I am not going to trade in my optimized 13.10 for an OS barely out of beta. So what to do, wait 4 months til 13.10 reaches eol. But how do I know that everything will work then, how much time do I have to spend on tweaking the system to get something working in case it needs tweaking? Remember by then 13.10 is no more and 14.04 may take time to set up, how to manage the gap?  Solution: I will just install 14.04 on an external drive, check in on it once or twice a week and take my time to optimize and customize it, keep it up to date but no rush to install it as my main system. By late july when I have to upgrade I will already have a fully optimized 14.04. I'll just clone it, wipe out 13.10 and restore the 14.04 image. Takes less time than both 'upgrade' and 'clean instal', no nasty surprises and no need to reinstall software and optimize from scratch. 

This is going to be smooth sailing from one Ubuntu version to the next with no gap in between.

2) Restructuring hard drive layout. I multiboot several Linux, if I want to add a partition, merge some, resize others the easiest would be clone --> restructure --> restore. Using gpatrted is slow and potentially risky depending on which end of a partition you want to resize. It is also much less flexible so say you cannot reorder the partitions.


3) Testing. I like to use some very bleeding edge stuffs like graphic driver for performance, but this can be rather risky. So I clone first before such updates. Since I have a separate /home I only need to clone the / partition which is  around 15 g and fsarchiver can clone it in less than 10 minutes and restore in 5. So I can even switch between different drivers and experiment without fear.

4) migrating systems (need changing some config files for different hardware)

As I said, I don't care too much about user data as backing them up is rather trivial, basically just copying/syncing.  It is system configurations that I want to preserve (like apache config files, optimized grub xorg.conf etc) It takes more time and efforts to set up these things properly than reinstalling software.

---

### Post by Impavidus on 2014-04-15
> **oldfred said:**
> ... but of course failure always occurs just before you were going to do a backup.
Or even worse: a failure occuring because you try making new backups.
I once had the habit of creating tarballs as backups of my vital files, mostly TeX files and source code. The weakness was that I overwrote the old backups while creating the new ones by using a command like```
tar -cvzf /media/backupdisk/texfiles.tar.gz ~/texfiles/
```After I accidentally hit x instead of c and hit enter before checking, resulting in restoring the old backups instead of creating new ones, I immediately changed my backup habits. I now have scripts safely backing up all vital files. The only time I ever needed backups was the only time when I didn't have them. It took 10 days to restore the work I had deleted.

---

### Post by sezhiana on 2014-04-15
Thank you guys for your wonderful discussion.

---

