---
title: "Ubuntu partitions"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by reeloo on 2011-11-07
Hi, im gonna try to go for an Ubunut install, running it on a seperate disk from windows..

but what size partitions do i need ? iam installing ubuntu on a 500gb drive, is there any rules on how big home/root should be ?

and was told home is for personal files like pic, music, documents etc. but what about the root partition, what does this contain?

thanks

---

### Post by wildmanne39 on 2011-11-07
Hi, 
1. /root 10gigs unless you are going to install a lot then I would go 20 gigs.
2. /Swap 2 gigs
3. /home as large as you like I usually give it the rest of my hard drive. 

But I do not use windows, if you use windows you may want to cut it down in size and also create a /data partition formatted to NTFS for personal files so you can share them easily with windows.
Thank you

---

### Post by critin on 2011-11-07
Hi, reeloo

Are you new to installing os's?  If you know something about partitions and want to do it, use the search option to find some pretty good advice on how to.  If you're brand new to the whole 'install' thing and your disk is empty or has only one other os on it, you can just let it do the work and install itself. (basically)

If you have another os already, a choice to install side-by-side will be given you before installing.  You can dual boot either system.   If no other os, you have the choice to 'use the entire disk' and it will do the partitioning for you.  It's the easy, safe way to go for new users who haven't done it before.  The instructions inside the install are clear.

Enjoy the journey.  :)

---

### Post by Miljet on 2011-11-07
> but what about the root partition, what does this contain

The root partition contains your system files (the actual operating system).

---

### Post by scradock on 2011-11-07
To be more precise, the root partition, /, contains everything except what you tell the installer to put in a separate partition, such as /home. If you don't specify an additional /home partition, the root partition (/) contains ALL the files and folders of your system.

Inside the system, there is another "root", which is a folder, called /root, which (in Ubuntu) contains a few files and folders with system default configuration options - most of which are over-ridden by options specified in corresponding files and folders in your /home folder or partition. To be even more confusing, some people use a separate partition (/root) to contain these files and folders.

In some Linux distros there is a "root user", who has his/her own "home" files in the /root folder, but Ubuntu doesn't set up a root user.

It's important not to confuse the true root partition (/) with the /root folder or the /root partition... - but all too easy, until you get used to it.

---

### Post by reeloo on 2011-11-08
Thanks that made sense too mee :)

just another thing, now i have 5 identical 500gb harddrives in my system... When i boot up in ubuntu, and is about to select the partition i need for the installation, can i lable the specific drive in windows ie. "ubuntu disc" (so that i dont select another drive with files on by accident) ?

---

### Post by mastablasta on 2011-11-08
sure. it's just that linux will say something like /sbd instead of D: drive for example. It marks the drives differently. 
 
I would suggest you read a manual before partitioning (or at least take a look at it - see my signature). Also you should know that if you simply create for example 25 Gb empty partition (non formated space) you can easilly install it all there (just select it to install to free empty sace). and Ubuntu installer will do all partitioning automaticly. The rest of the disk can be NTFS formatted and later used for data (which will be shared with windows).
 
have a look also here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by wildmanne39 on 2011-11-08
Hi, also a lot of people disconnect their other drives until they are done with the install so they can not possibly partition the wrong drive.

Then hook the drives back up and boot ubuntu and open a terminal and run:
```
sudo update-grub
```
That will put a menu to boot all your operating systems in one place.
Thank you

---

### Post by audiomick on 2011-11-08
Here is a bit more reading.
On this page
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
I use the "separate home" variation, with about 10 GB for the / partition.

Here are some pages on partitioning

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by reeloo on 2011-11-08
> **wildmanne39 said:**
> Hi, also a lot of people disconnect their other drives until they are done with the install so they can not possibly partition the wrong drive.

Then hook the drives back up and boot ubuntu and open a terminal and run:
```
sudo update-grub
```That will put a menu to boot all your operating systems in one place.
Thank you


Thanks for the suggestion, sounds like the smart thing to do :) 

ive read a bit in the ubuntu manual about partitioning, and when i here a couple of minutes ago was into the installation process i cant seem to figure out which partition ubunto is gonna use for ie, root/home/swap etc (i just cant see how i decide where the OS installation will go and where the home folder will be and so on?

---

### Post by audiomick on 2011-11-08
Ok, I understand your concern, having had it myself. In fact, it isn't that hard.

Are you wanting to install to a new drive, or overwrite an old one? If it is new, it will be easier.

I would suggest booting into the live CD and having a look at your drives with Gparted. If you look around in there, it should become a bit clearer, I think. Gparted is a partitioning program which shows you the partition table of a drive, and how it is all formatted. A new drive will show up as empty. If there is something on there, it tells you what it is and how much space it is using. The screenshot shows mine. You can see where the windows recovery partition is on sda1, the Vista install on sda2, and the linux partitions on sda5, sda6 and sda7. Gparted only shows you one drive at a time. You have to select them in the drop-down at the top of the window. Have a look and see if that helps.

The advice from critin that the "side by side" option is easiest is correct if there is only one drive. I am not quite sure how it behaves if there are multiple drives. I prefer to use the "manual" option when I get to the partitioning stage of an install so that I can specify where it all goes and how big the partitions should be.

You are also fairly safe running the installer just to have a look if you keep your wits about you. Before it does anything irreversible, it asks you if you are sure. If your aren't, you can go back and have another go or bail out. It doesn't do the changes until you tell it to.

edit: forgot to add the screenshot. It's there now

---

### Post by wildmanne39 on 2011-11-08
Hi, audiomick gave you a link for partitioning.

You can choose to let ubuntu use the whole disk and it will create the partitions for you but it will not separate /home, /root or create a separate data partition if you want to share documents with windows.

If you want to have a separate /home, /root and all then when you start the installer you have to choose to create partitions manually in 11.04  and 11.10 the tab is called something else.
Thank you

---

### Post by oldfred on 2011-11-08
Lots of good advice above. I prefer to partition in advance so I have more control over partition sizes. But if it is your first install it is not as important. With a 500GB drive you have lots of room, since Linux is small. And if most of your data is on other drives you will have lots of space.

This is one of the few guides specifying a second (or more) drive. Lots of detail, but has screen shots. If you do not disconnect drives as suggested above be sure to note the combo box and choose the same drive's MBR that you are installing Ubuntu into to install the grub2 boot loader. Otherwise it defaults to sda. 

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by reeloo on 2011-11-09
Thanks for all the links and answers, my installation went pretty good and is now dual booting side by side with windows7 :)

(was pretty easy after all) =)

---

### Post by audiomick on 2011-11-09
Glad to hear it. Well done. :)

---

### Post by wildmanne39 on 2011-11-09
Hi, Your welcome! I am glad everything went well.
Enjoy

---

