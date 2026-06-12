---
title: "Plan on using Ubuntu alongside XP"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by franzrebs on 2008-05-02
Hi guys, I'm a newbie currently using Windows XP, and I plan on installing Ubuntu using dual boot. Can anyone enlighten me on where I should start and how to do it?

How much space should I allot to my Ubuntu partition? I have 80 Gb HDD, 1.7 GHz processor and 224 mb RAM. I will mainly use XP for games (like Sims 2, GTA: VC, etc.) and a few other applications which aren't compatible with Ubuntu.

I'm also wondering which version to use - Ubuntu, Kubuntu, or Xubuntu? :confused: I'm all for fast performance and ease of use (I share my computer with my younger sister), and some eye-candy too if it can be helped.

---

### Post by Bartender on 2008-05-02
Well, first off, your RAM is borderline.  You should be able to install via LiveCD but just barely.  If you can beef up RAM without breaking the bank you'd notice a vast improvement above 512.
Unless you went with Xubuntu, which is a lighter distro but not as user-friendly.  
There have been a million posts regarding your situation.  In the end you'll just have to do it.  Back up important personal data.  Defrag XP several times.  Be prepared to reinstall XP just in case.  At that point the simplest thing to do would be to allow the Ubuntu/Kubuntu/Xubuntu LiveCD to install using the automatic setting in the partitioner section.  That's not how I'd do it, but it's the easiest for the first-time user.

---

### Post by bjm1904 on 2008-05-02
I would recommend 12GB for Ubuntu (ext3) and a 256MB Swap partition minimum (if you don't plan on repartitioning for a while, then i would suggest 1GB swap space - which is what I've done). The Installer is fairly self explanatory, and you just need to go for the 'manual setup' option when it comes to hard disk partitioning. 

As ever though, I recommend you get a backup of your XP installation, as data can be lossed during resize if you haven't done a defrag for a while.

---

### Post by bjm1904 on 2008-05-02
Slight ammendment:

You'll need to download the 'alternate CD' for systems with 256MB RAM or less - this is in text mode, but it isn't too hard to work out.

---

### Post by Paqman on 2008-05-02
> **franzrebs said:**
> 
How much space should I allot to my Ubuntu partition?

Depends on whether you want room for data. The default system itself will fit within 10GB quite happily.

One good way to set up your system is to put the system files on one partition (called root or just / ) and you personal files on a different partition (called /home) In that case you'd want 6-10GB for / and as much as you like for /home. That setup would require a bit of manual partition, which you may or may not be keen to try at this stage.

You can either do your partitioning manually, let the installer do it for you, or you can use Wubi, which requires no partitioning at all.

---

### Post by xzero1 on 2008-05-02
Did you know you can boot from the live cd and try Ubuntu before you install anything? Do a test drive first. You will also get an idea how it performs with your current system although understand it will be running off of your cd which will slow things down.

---

### Post by oedha on 2008-05-02
you still can go with ubuntu
about learning....
[http://psychocats.net/ubuntu](http://psychocats.net/ubuntu)
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by linuxlizard on 2008-05-02
Are you guys sure about the ram?

I set my folks up with feisty fawn kubuntu and they've only got 256mb ram, an amd 1800+ processor, and a 64 mb nvidia card and It's been running quite snappy for some time, and they've got beryl with the cube and all the bells and whistles going no problem.

Because of the performance boost my own machine has had from hardy, I was thinking I'd do a clean install on my folks computer for them. But if you guys  are right about it being a resource hog, maybe I should leave it way back in feisty. Has ubuntu really become that bloated?

---

### Post by franzrebs on 2008-05-02
What is the swap space for? Is it really necessary? What happens if I only assign two partitions, one for XP and one for Ubuntu?

---

### Post by franzrebs on 2008-05-02
> **Paqman said:**
> Depends on whether you want room for data. The default system itself will fit within 10GB quite happily.

Yes, I will be using Ubuntu for creating text documents, graphic design (if I get Photoshop CS2 to work in it), downloading stuff from torrents etc. so yeah pretty much all (or most) of my data will be stored there. Games and several other applications (Python, Visual Basic, etc.) will be on XP. Will 35 Gb be enough for the XP partition?

> 
One good way to set up your system is to put the system files on one partition (called root or just / ) and you personal files on a different partition (called /home) In that case you'd want 6-10GB for / and as much as you like for /home. That setup would require a bit of manual partition, which you may or may not be keen to try at this stage.

So where should these system and personal files be placed - in the XP partition, Ubuntu partition or a different one?


Sorry if I ask too many questions. :confused:

---

### Post by Fedz on 2008-05-02
Swap space is the same as the swap file on window$ and is used if you run out of RAM ... :)

I used to dual boot back in the days of Ubuntu/6.10 but, soon found myself using Ubuntu more often as I found the 'eye-candy' from [Gnome-Look](http://www.gnome-look.org) ;)

Ubuntu is highly configuarable and the more you find and use this the more you wanna dump Window$ :)

Hope this helps :)

---

### Post by linuxlizard on 2008-05-02
oh yeah, I forgot to say,

for swap I've always set it for 2.5 times amount of ram or 512 mb whichever is less, and it's always worked great. I think someone recommended 256 and that seems too small to me.

---

### Post by mick.ng on 2008-05-02
Hi fellow experts,

I'm very keen to give Ubuntu a good go but I'm reluctant to give up my XP just yet. I want to go beyond just testing off the CD.

I'm also thinking of setting up partitions for my Ubuntu but I'm not sure which one to partition. Should I do it in **dev/sda** or **dev/sdb** and **fat32** or **ntfs**?? 
I don't understand what the differences are.:confused:

Also, I'm wondering if it is possible to install Ubuntu on an USB external hard drive? I tried the other day but it wouldn't let me. I wonder if there's another way.

Any help/ advice will be appreciated.


Regards,
Mick:KS

---

### Post by franzrebs on 2008-05-03
*bump*

How does Wubi work?

---

### Post by Ducatiboy-stu on 2008-05-03
i installed ubuntu 7.10 ( gutsy ) and used the grub to do my partition, then i upgraded

First thing to do is defrage your HD ( several times ) BEFORE you run grub

also do backups in case XP crashes

when you do the install from grub choose the first option, it will ask you for the size of your partition. This is the size that grub will allow for XP...so make sure that you make this partition BIGGER that your used disk space in XP...ie if you have a 100Gb HD and XP is currently using 40GB, then make the partition bigger than what XP currently uses....you have to think backwards, cause grub is taking over your HD and allocating towards ubuntu

Ubunut can use 10Gb with ease

---

### Post by franzrebs on 2008-05-09
Alright, I just installed Xubuntu. I noticed that it's actually pretty slow, almost slower than (freshly installed XP), even if I have 256mb RAM and a 1.7GHz processor. Am I doing something wrong here?

I'm also having trouble connecting to the internet. I tried to insert the installer CD of the modem (Speedtouch) but I can't execute the setup.exe.

Hmm, maybe I should create a new topic for this.

---

### Post by RobHK on 2008-05-09
> **franzrebs said:**
> Yes, I will be using Ubuntu for creating text documents, graphic design (if I get Photoshop CS2 to work in it), downloading stuff from torrents etc. so yeah pretty much all (or most) of my data will be stored there. Games and several other applications (Python, Visual Basic, etc.) will be on XP. Will 35 Gb be enough for the XP partition?



So where should these system and personal files be placed - in the XP partition, Ubuntu partition or a different one?


Sorry if I ask too many questions. :confused:

If you go with the default setup, you will find the system files are installed to the root folder (/) and a /home folder within that contains your personal user folder. This in turn contains folders for your documents, videos, pictures and downloads.

I only got into this myself very recently, and I know from experience that none of it makes any sense until you do it.

I found the partitioning instructions a bit confusing, and with my first install I wiped my Windows document partition (yes, I had backed it up :)). The most foolproof option is shrinking your Windows partition beforehand (see next para), leaving enough empty space for Ubuntu and then giving the instruction to install in the largest free space. If you do that, the installation disk will automatically create a Ubuntu partition and a swap partition. (Don't worry about the swap partition: you never need to do anything with it yourself. It's as invisible a Windows swap file.) 

If you don't have a partitioning tool google for gparted (boot disk version)and burn it to a CD. (When you boot gparted it offers a menu. The first option (automatic) didn't work for me, but the second option covers most PCs.) Once you have set up the new size of your partition (leaving empty space for the Ubuntu installation later) you instruct gparted to apply your changes and go away for about 30 minutes (can be less).

DO NOT ATTEMPT TO DO ANY KIND OF PARTITIONING WITHOUT A BACKUP OF ALL IMPORTANT DOCUMENTS. Accidents are rare but can happen.

You will be able to access, modify and create documents on your Windows partition from Ubuntu, but not vice versa.

I second other people's recommendations to get more RAM, though I think Ubuntu is less demanding than XP; buy another Gig if you can, but another 512 will do. If you are afraid of running out of disk space, a USB external hard disk will work on both Windows and Ubuntu.

---

### Post by RobHK on 2008-05-09
> **franzrebs said:**
> Alright, I just installed Xubuntu. I noticed that it's actually pretty slow, almost slower than (freshly installed XP), even if I have 256mb RAM and a 1.7GHz processor. Am I doing something wrong here?

I'm also having trouble connecting to the internet. I tried to insert the installer CD of the modem (Speedtouch) but I can't execute the setup.exe.

Hmm, maybe I should create a new topic for this.

My last post is now redundant as you have now installed. 

I think I know the SpeedTouch modem. It's a USB job isn't it, supplied by TalkTalk? You won't be able to run EXE programs in Ubuntu as they are for Windows, so you might be stymied there. I have no idea whether setting it up in Windows will allow it to work in Ubuntu. If you use a router, and the router was already connected and set up in Windows, the Internet connection is made automatically by Ubuntu.

I'm surprised you find Ubuntu slow compared with XP, but I'd advise more RAM. My system came with 256, I added 512 and the difference (in XP) was big. I later added another Gig and had some improvement , but nothing like as much as the first jump.

---

### Post by RobHK on 2008-05-09
> **mick.ng said:**
> Hi fellow experts,

I'm very keen to give Ubuntu a good go but I'm reluctant to give up my XP just yet. I want to go beyond just testing off the CD.

I'm also thinking of setting up partitions for my Ubuntu but I'm not sure which one to partition. Should I do it in **dev/sda** or **dev/sdb** and **fat32** or **ntfs**?? 
I don't understand what the differences are.:confused:

Also, I'm wondering if it is possible to install Ubuntu on an USB external hard drive? I tried the other day but it wouldn't let me. I wonder if there's another way.

Any help/ advice will be appreciated.

Regards,
Mick:KS

I _think_ dev/sda and dev/sdb are external hard disks. As far as I am aware, internal hard disks are labelled dev/hda and dev/hdb etc. I'm not an expert, but I think you could install on an external disk, provided your system will boot from USB, but this _might_ only apply to sticks.

It doesn't matter whether the disk you partition is currently formatted in NTFS or FAT32. These are formats used by Windows; Ubuntu installation will create a new partition in a different format (ext3) used by Linux.

---

