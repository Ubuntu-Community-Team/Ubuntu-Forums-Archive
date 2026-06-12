---
title: "Help setting up dual boot"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by cicada2 on 2014-04-16
Greetings, 
Being new to ubuntu, I have been chewing on all the posts. Right now everything is all XP/ all the time (one partition). I would like to keep existing XP until I am ready to make the jump to linux 100%, So I want this computer to be a dual boot for now. Would some kind soul steer me - Please? Let me know if you think I am missing steps. 
1. I think I have to create a whole disc clone before I resize or move the  existing partition? What is the best proggy for this (freeware if  possible)?
2. How many partitions are required to run ubuntu (and XP)? Is 2 enough? 
3. Best proggy to resize and create new partitions (if free that's better for me)?
4. Should i be looking for an older version of ubuntu? The website suggests **version 13.10 (32bit)** for older computers. Suggestions were made elsewhere to wait a few months before grabbing the newest upgrades to avoid buggy versions. How long has version 13.10 been around? Any suggestions here?
5. Probably no big deal, but I have been directed to **Mint** repeatedly. I guess because I am on XP. And - I use this machine primarily for torrents and lossless music (all legal, not pirated or copywrite stuff). I felt ubuntu is the way to go because the community seems bigger. Once I learn, the curve will be better into the future. 

Big thanks (in advance).
cicada

---

### Post by mastablasta on 2014-04-16
first thing to do is check if all hardware works. use the try it option on boot (this loads the OS into ram and doesn't make any changes to system). and also make sure you like the user interface (Ubuntu, Kubuntu, Lubuntu, Xubuntu each have different user interface but all are based on Ubuntu).

> **cicada2 said:**
> 1. I think I have to create a whole disc clone before I resize or move the existing partition? What is the best proggy for this (freeware if possible)?

Not necessary but highly advisable (to make this backup). best programs are clonezilla (advanced) or redo backup (more simple, less options).
> 
2. How many partitions are required to run ubuntu (and XP)? Is 2 enough? 

Ubuntu needs two windows xp needs one.
> 
3. Best proggy to resize and create new partitions (if free that's better for me)?

Use the windows disk manager. make sure you defragment the drive two times and run a checkdisk. programs that do all this are all included with windows XP.

Simply create free empty unformatted disk space you plan to allocate for Ubuntu. Ubuntu installer willd o the rest.
> 
4. Should i be looking for an older version of ubuntu? The website suggests **version 13.10 (32bit)** for older computers. Suggestions were made elsewhere to wait a few months before grabbing the newest upgrades to avoid buggy versions. How long has version 13.10 been around? Any suggestions here?

Heh buggy versions....
very buggy are testing and alfa versions. you probably didn't find the links to those.
12.04 is current LTS (long term support). Next LTS is 14.04 (currently still in beta) and comes out in a week or so. LTS have 5 years support, one can upgrade directly from LTS to LTS and they come out every 2 years.
13.10 is normal version (released in october 2013 = 13.10 = year.month). normal versions are supported for 9 months. new version is out every 6 months.13.10 support expires in June. I suggest you use 13.10 and upgarde to 14.04 in about a month or so. usually in the frist month after release there are more bug reports from end users than during beta stage so many bugs that remained get ironed out. however you can use either.
> 
5. Probably no big deal, but I have been directed to **Mint** repeatedly. I guess because I am on XP. And - I use this machine primarily for torrents and lossless music (all legal, not pirated or copywrite stuff). I felt ubuntu is the way to go because the community seems bigger. Once I learn, the curve will be better into the future. 

Mint is Ubuntu with tweaks. they use a Cinnamon interface and it comes with many things preinstalled. some things are a bit more user friendly. it's a good solid ditribution and like Ubuntu very suitable for beginners. they do not support upgrades from release to release. users instead do a fresh install. or at leats it used to be like that. 

Like i said above use the try it option on live boot to try out a few of them. 

selecting a distribution also depends on your computing power. what are your computer specs? If 512MB or less consider Lubutnu/Xubuntu, 1GB or more with good graphics card you can use any distribution. with poor graphics card (or with poor support) again use Lubuntu or Xubuntu instead. Yet another option for older mashcines is Mate user interface (desktop environment). Mint has a Mate version available.

if you have less than 256 MB ram use Chrunchbang or Bodhi.
If you have less than 128 MB ram - Slitaz, Puppy, DSL or Tiny core etc...

EDIT: also check if your CPU has 64bit support. if it does you may use 64bit version.

---

### Post by grumblebum2 on 2014-04-16
The dual boot procedure is normally fairly safe but....
if you are on a desktop pc, the foolproof way of installing ubuntu is to use a separate hard drive.
Disconnect your XP drive and connect the second drive and install ubuntu.
This way grub(boot menu) is written to the ubuntu drive and doesn't overwrite your boot partition on your XP drive.

Once ubuntu is installed, reconnect the XP drive and choose the ubuntu drive as the primary boot drive in the BIOS.
After booting into ubuntu, run ```
sudo update-grub
``` and grub will add your XP install to the boot menu.

Upon reboot you will see a Windows choice at the grub menu.
If you have any boot problems you can select the XP drive as the primary boot drive in the BIOS 
where you will boot as before, directly into Windows.

In any case you should always have a backup of your personal files.

---

### Post by 3rdalbum on 2014-04-16
A different perspective here.

1. Definitely make a backup. A whole disk clone is a good idea.

2. The Ubuntu installer will sort that out for you. It sets up a partition for OS and data, and another for 'swap'. It also downsizes the Windows partition to make space. You can have one partition for each OS but by default the installer sets up two for Ubuntu.

3. Don't worry, let the Ubuntu installer do it. If your disk is very fragmented it will be quicker to defrag in Windows first, but this is not strictly necessary.

4. Don't use old versions, they run out of support quickly and are stuck with older software. Ubuntu 14.04 is out tomorrow, use that. It has been tested by many community members including me - I found it very stable. If this is an older computer, try Xubuntu or Lubuntu. (14.04).

5. Everyone has preferences, but the Ubuntu community is larger. You may have been directed to Mint because it has codecs and Flash and Java preinstalled, but they are easy to install in Ubuntu anyway. Mint lags behind Ubuntu by a few months, too.

---

### Post by oldfred on 2014-04-16
Best to know what system, cpu & graphics card/chip you have.

I have two systems, desktop & laptop both originally from 2006 with XP, but desktop was upgraded.

I have 1.5GB of RAM in laptop and it has CoreDuo Intel processor with Intel video. It runs full 64bit Ubuntu, but I use fallback/flash back not Unity which is more of the old menus like older versions of Ubuntu. With only 1.5GB of RAM I cannot load more than one large app and several small ones before it starts using swap and then is slow. Unity needs a good video system to run well, flash back is lighter weight like some of the other flavors.

My desktop has CpreDuo Intel chip, 4GB of RAM with nVidia video card. It run 64 bit Ubuntu well but I added SSD and now it loads everything very quick. I now have shutdown XP, but drive is still connected. I also use flashback. I have installed every versions since 6.06 on this sytem, but use 12.04 as my working system, and will soon convert to 14.04 as my working version. I have 14.04 installed in a test partition and with limited use has run well.

---

### Post by cicada2 on 2014-04-16
I have Compaq laptop currently running XP SP3. Only 752MB of RAM (not bad in those days). Intel Pentium 4 CPU 2.4 GHz. 

Not  sure what video graphics is installed. I looked in device mgr and couldn't find the answer. Honestly, I don't use this for  watching anything. It's an audio workhorse. The latency (cycling) is so  bad since last fall when I took one of those XP updates... now the sound  just stutters and burps. I have tried a lot of stuff to identify the  weakness. I think it's all the crap that Windoze has loaded over the  years (can't be my fault). 

I am prolly going to grab 1404 when it is released. Thanks to everyone for the thoughtful replies here!

---

### Post by oldfred on 2014-04-16
You will probably be better off with Lubuntu not Ubuntu.

       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by mastablasta on 2014-04-17
your GPU whichever it is uses 16MB of ram. Lubuntu should really do the trick here. maybe even Xubutnu could pull it off. don't expect much in performance of flash and such.

---

### Post by peter-spolenak on 2014-04-17
Hello,

maybe reading this article will help: [http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by stalkingwolf on 2014-04-17
The first thing to remember when installing a Mint or *buntu distro is it expects you to know what you are doing.  IT is different from windows.

Back up your important data.  read each screen before clicking next or continue.  when you get to the type of installation screen you usually have 3 options.
1. use entire HDD.  this completely wipes the drive and installs system
2 install alongside other OS . this will install the buntu distro alongside windows.
3 other.  lets you manually choose the partition you want to install to.

I am running Mint 13 Mate on 2 HP mini 110's and 2 asus EEE 1005's  with no problems.  Also have it on 2 HP 5000 series desktops with 3 gb of ram, one that runs my tv.

I would try several live disks  and choose which runs best and you like the best.  I like the Mate desk top and have installed it on all the distributions mentioned . also look at the preinstalled packages one distro might have all you want while another doesnt.  That is the main difference between the distros i have found.

---

### Post by Mark Phelps on 2014-04-17
> 1. I think I have to create a whole disc clone before I resize or move the existing partition? What is the best proggy for this (freeware if possible)?

Personally, I have had better experience using Windows products to image Windows partitions, and Linux products to image Linux partitions.

What is probably the best Windows imaging product out there is Macrium Reflect.  You can download, install, and run it for free.  Install it to your PC and do an image backup to an external drive.

Then, you should consider using Minitool Partition Wizard Boot CD to shrink the WinXP partition.  It's perfectly safe, and it's also FREE.

Once you do that and boot back into XP, I would suggest making another image backup with MR -- of the shrunken partition.  This will allow you to reinstall the current XP setup in only a few minutes.

Also use the MR option to create and burn a Linux Boot CD.  This is needed to boot should you decide to restore from the image backup, as you can't modify a partition that is in use

---

