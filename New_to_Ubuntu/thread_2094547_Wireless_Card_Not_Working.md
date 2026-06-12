---
title: "Wireless Card Not Working"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by TheOldHippie on 2012-12-14
First I must admit that I have absolutely no idea what I am doing but am willing to spend the time necessary to learn just to prove that the not so young generation in this country is not completely technically illiterate.
BAsic setup: have Acer Aspire 5517 laptop with Windows 7 installed. Trying to load Ubuntu in order to learn it well enough to discard Microsoft and having to purchase a new version every 2 or 3 years. All went well till trying to get network running. Found out I have broadcom card which doesn't work well with Linux. With a little research, found out I could install (?) other drivers for card, have downloaded 2 versions of 3 files that, as far as I can tell need to be copied to Ubuntu partition on hard drive and then manipulated in some way.

Files I have down loaded are:

C:\Users\Claudia\Downloads\Linux\Ubuntu\ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\ndiswrapper-common_1.57-1ubuntu1_all.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\ndisgtk_0.8.5-1_amd64.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112.orig.tar.gz
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112-8.debian.tar.gz
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112-8.dsc

Any and all help will be greatly appreciated, just remember that basically, I know nothing about Linux.
:confused:

---

### Post by coffeecat on 2012-12-14
First question: You've downloaded some stuff to Windows, presumably because you can't download to Ubuntu. Just to be sure - do you have Ubuntu installed and can you boot into it?

> **TheOldHippie said:**
> Found out I have broadcom card which doesn't work well with Linux.

Oh yes it can! :wink:

Some Broadcom cards work out of the box with Ubuntu, and some need either the proprietary driver or firmware (depending on chipset) which is easily installed if you can connect to your router with an ethernet cable. If you can't use an ethernet cable you can install the necessary packages from the install CD. 

> **TheOldHippie said:**
> 
Files I have down loaded are:

C:\Users\Claudia\Downloads\Linux\Ubuntu\ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\ndiswrapper-common_1.57-1ubuntu1_all.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\ndisgtk_0.8.5-1_amd64.deb
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112.orig.tar.gz
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112-8.debian.tar.gz
C:\Users\Claudia\Downloads\Linux\Ubuntu\broadcom-sta_5.100.82.112-8.dsc


First thing, discard that lot. You don't need to go anywhere near ndiswrapper except as a last resort. And you don't need the tar.gz files, and certainly not if you are new to Linux.

Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It's a bit daunting at first sight because it covers almost every eventuality, but be assured - getting your Broadcom card working will probably be very easy. If you want help with that, don't go further than the first part where you run this from a terminal:

```
lspci -vvnn | grep 14e4
```

If you do need help, post the output and we can take it from there. Tip: highlight the terminal output with the mouse, right-click -> copy. You can then paste it into your post.

---

### Post by TheOldHippie on 2012-12-14
First, thank you for your information, will start immediately with search. Second, you mentioned installation CD. I downloaded the files from web site, can I use them? 

Be back with info if needed.

Again, many thanks. Reminds me of my days learning DOS, back when dinosoars roamed. :P

---

### Post by coffeecat on 2012-12-14
> **TheOldHippie said:**
> First, thank you for your information, will start immediately with search. Second, you mentioned installation CD. I downloaded the files from web site, can I use them? 

That sounds as though you did a wubi install - that is running wubi.exe within Windows. Connecting to your router with an ethernet cable is the easiest way to go if you can, which will mean you won't need the installation CD. If you can't do that, then let us know. Also - which version of Ubuntu are you running, 12.04 or 12.10 or something else?

---

### Post by TheOldHippie on 2012-12-14
Sitting here trying to figure out what I want to ask. Results of:

lspci -vvnn | grep 14e4

02:00.0 Network Controller [280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Using ethernet cable to router is kind of inconvenient, is it possible to go through another computer that is on the network? Will do either one, desparately want to say bye-bye to MS.

And yes, I ran Wubi to install my Ubuntu, would using a DVD/CD be better?

As mentioned, am BRAND new to this and pray that y'all don't get tired of me asking for help.

Thank you.
The Old Hippie

---

### Post by TheOldHippie on 2012-12-14
Sorry, forgot to say that I am attempting a 12.10 install.

---

### Post by DuckHook on 2012-12-14
Having a forum admin on your case is like having a Norse god on your  side. You're in good hands on the wireless issue and won't need meddling  from me.

> **TheOldHippie said:**
> And yes, I ran Wubi to install my Ubuntu, would using a DVD/CD be better?

WUBI is meant to let Windows users try out Ubuntu first. There's nothing wrong with a WUBI install in theory, but it suffers from fragility because it sits as a file within your Windows partition and is therefore dependent on the health of your Windows filesystem. Almost no long-term Ubuntu veterans install via WUBI, so forum support is also somewhat limited. Would suggest you start a new thread on the WUBI vs. Separate Partition question. When posting, please provide following info for best help:

1. Windows version
2. In Ubuntu, do:

```
sudo parted -l print
```and include results with your post. If easier, create a file of this output on your Ubuntu desktop by doing:

```
sudo parted -l print > ~/Desktop/partition_table
```then attach this file (or its contents) to your post.

Welcome to the forums! We hippies have to stick together. And I suspect that you'll like the world's biggest community garden that is Linux.

---

### Post by coffeecat on 2012-12-15
> **TheOldHippie said:**
> 
02:00.0 Network Controller [280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

You have the BCM4312 which, according to the link I posted earlier, should work with either the proprietary STA driver, or the open source b43 driver so long as you install the proprietary firmware. By the way - as an aside - if you are thinking that this is all very inconvenient, you would be absolutely right, but this is not a reflection on Ubuntu or the wider Linux world. This is down to a legacy of Broadcom's previous licensing policy. Most wireless chipsets of other makes simply work out of the box in Ubuntu. Indeed, I usually find setting up wireless in Ubuntu easier than in Windows. Anyway, back on topic... :)

> **TheOldHippie said:**
> Using ethernet cable to router is kind of inconvenient, is it possible to go through another computer that is on the network? Will do either one,

Inconvenient or impossible? Installing the requisite driver by using an ethernet cable will take you a couple of minutes. The alternatives are - fiddly. I give an outline below.

Going through another computer on the network would require connection to the network, which you do not have. Besides, offhand I'm not sure how one would do that.

**Installing from the CD.** If you were to go that route, you would need to download an approx 700MB ISO file from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

But first, we would need to know whether you are running the 64-bit or 32-bit version of Ubuntu. Another terminal command for you to run which will tell us, and which will also include some information which we might need. Please post the output of this:

```
uname -a
```

While you have a terminal open, please also post the output of this:

```
dpkg -l | grep headers
```

Sorry about all this terminal stuff. If you choose the ethernet route it simply isn't necessary but I'm trying to anticipate what information will be needed if you use one of the alternatives.

Having downloaded the ISO file, you would have to burn it to CD. This can all be done in Windows, and how to do that is described here:

[https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows)

I'm not suggesting you do that just now, simply telling you what is involved, but please do post those terminal outputs.

**Downloading driver packages using Windows**. Another alternative would be to download the requisite packages using Windows, transfer them to your Ubuntu system and then install them from there. You would need to be sure you downloaded the correct versions and their dependencies if necessary. The terminal output and what you've already told us should be enough, but we can come back to that if need be. 

> **TheOldHippie said:**
> And yes, I ran Wubi to install my Ubuntu, would using a DVD/CD be better?

DuckHook has mentioned what wubi is. Briefly, with wubi you have a virtual partition for Ubuntu contained within a single file within your Windows filesystem, usually in your C:\ partition, but it can be in a D:\ or E:\ or whatever if you have one. It's a perfectly valid way of trying Ubuntu, but has a few drawbacks. Installing from the DVD/CD involves creating a dedicated separate partition for Ubuntu. This is the preferred way but since you have wubi up and running, you might just as well continue for now so that you can get used to the way Ubuntu works. When you feel more confident with Ubuntu, you could do a "proper" installation if you wish and discard your wubi one.  

One last comment - I've not had direct experience of the BCM 4312 chipset, but I have read in other threads that some seem to work better with the STA driver and some with the b43. There appear to be subsets of that particular chipset which makes matters more complicated than they should be. I'll pm another forum member who takes an interest in wireless issues and ask him to take a look at this thread as well.

---

### Post by wildmanne39 on 2012-12-15
Hi, this is the information on that card to get it working but it is best to have an ehternet connection, because as coffeecat said you will need to install the headers and build essential I believe even for this method but you can try it without first if you wish.

I like to use b43 driver it works better in most cases.

If you have any other driver installed you will need to remove it first.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Copy and paste commands for accuracy.
Thanks

---

### Post by TheOldHippie on 2012-12-16
> **DuckHook said:**
> Having a forum admin on your case is like having a Norse god on your  side. You're in good hands on the wireless issue and won't need meddling  from me.



WUBI is meant to let Windows users try out Ubuntu first. There's nothing wrong with a WUBI install in theory, but it suffers from fragility because it sits as a file within your Windows partition and is therefore dependent on the health of your Windows filesystem. Almost no long-term Ubuntu veterans install via WUBI, so forum support is also somewhat limited. Would suggest you start a new thread on the WUBI vs. Separate Partition question. When posting, please provide following info for best help:

1. Windows version
2. In Ubuntu, do:

```
sudo parted -l print
```and include results with your post. If easier, create a file of this output on your Ubuntu desktop by doing:

```
sudo parted -l print > ~/Desktop/partition_table
```then attach this file (or its contents) to your post.

Welcome to the forums! We hippies have to stick together. And I suspect that you'll like the world's biggest community garden that is Linux.

Okay, trying to get all the information everyone wanted. I got Ubuntu (64 bit) installed side by side with Windows 7. Found out that I've got a lot to remember with the changes from the last 30 years or so. Here is print out you requested.

Results of sudo parted -l print 
 Model: Kingston DT 100 G2 (scsi)
Disk /dev/sdb: 4008MB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number    Start     End        Size        Type     File    system  Flags 
 1             4129kB     4008MB   4004MB  primary  fat32             boot, lba   


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 
has been opened read-only. 
Model: TSSTcorp CDDVDW TS-L633C (scsi) 
Disk /dev/sr0: 4700MB 
Sector size (logical/physical): 2048B/2048B 
Partition Table: mac 
 Number   Start     End         Size     File system  Name   Flags  
1            8192B       24.6kB  16.4kB                   Apple  
2             3179MB  3189MB  9306kB                  EFI

---

### Post by TheOldHippie on 2012-12-16
> **coffeecat said:**
> You have the BCM4312 which, according to the link I posted earlier, should work with either the proprietary STA driver, or the open source b43 driver so long as you install the proprietary firmware. By the way - as an aside - if you are thinking that this is all very inconvenient, you would be absolutely right, but this is not a reflection on Ubuntu or the wider Linux world. This is down to a legacy of Broadcom's previous licensing policy. Most wireless chipsets of other makes simply work out of the box in Ubuntu. Indeed, I usually find setting up wireless in Ubuntu easier than in Windows. Anyway, back on topic... :)



Inconvenient or impossible? Installing the requisite driver by using an ethernet cable will take you a couple of minutes. The alternatives are - fiddly. I give an outline below.

Going through another computer on the network would require connection to the network, which you do not have. Besides, offhand I'm not sure how one would do that.

**Installing from the CD.** If you were to go that route, you would need to download an approx 700MB ISO file from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

But first, we would need to know whether you are running the 64-bit or 32-bit version of Ubuntu. Another terminal command for you to run which will tell us, and which will also include some information which we might need. Please post the output of this:

```
uname -a
```While you have a terminal open, please also post the output of this:

```
dpkg -l | grep headers
```Sorry about all this terminal stuff. If you choose the ethernet route it simply isn't necessary but I'm trying to anticipate what information will be needed if you use one of the alternatives.

Having downloaded the ISO file, you would have to burn it to CD. This can all be done in Windows, and how to do that is described here:

[https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows)

I'm not suggesting you do that just now, simply telling you what is involved, but please do post those terminal outputs.

**Downloading driver packages using Windows**. Another alternative would be to download the requisite packages using Windows, transfer them to your Ubuntu system and then install them from there. You would need to be sure you downloaded the correct versions and their dependencies if necessary. The terminal output and what you've already told us should be enough, but we can come back to that if need be. 



DuckHook has mentioned what wubi is. Briefly, with wubi you have a virtual partition for Ubuntu contained within a single file within your Windows filesystem, usually in your C:\ partition, but it can be in a D:\ or E:\ or whatever if you have one. It's a perfectly valid way of trying Ubuntu, but has a few drawbacks. Installing from the DVD/CD involves creating a dedicated separate partition for Ubuntu. This is the preferred way but since you have wubi up and running, you might just as well continue for now so that you can get used to the way Ubuntu works. When you feel more confident with Ubuntu, you could do a "proper" installation if you wish and discard your wubi one.  

One last comment - I've not had direct experience of the BCM 4312 chipset, but I have read in other threads that some seem to work better with the STA driver and some with the b43. There appear to be subsets of that particular chipset which makes matters more complicated than they should be. I'll pm another forum member who takes an interest in wireless issues and ask him to take a look at this thread as well.


Router sits in closet upstairs so hooking up via ethernet cable, though a little easier, still is not a practical solution. Work space, atmosphere and what have you. So I downloaded 64 bit ISO and installed 12.10 side by side with Windows 7 and will run that  for a while until I am a little more familiar or atleast until I can get wireless adapter to work. Here are results of your posts:

tony@tony-Aspire-5517:~/Desktop$ uname -a Linux tony-Aspire-5517 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
Results of: dpkg -l | grep headers ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0  

Still working on getting files back and forth between Ubuntu and windows  but getting more familiar with all this work.

---

### Post by DuckHook on 2012-12-16
Hi, @TheOldHippie

*parted* info was incomplete, but let's not overwhelm you any further. If @coffeecat and @Wild Man have, between them, managed to solve your network issue, then my best advice is to leave well-enough alone at this point. I suspect that you have a pretty typical Windows 7 installation on your HDD which leaves no open partitions for a standalone Ubuntu install. Repartitioning is not trivial, and we just won't go there. When you get comfortable enough with Ubuntu that you want to see it permanently on your HDD, then I would suggest:

1. having excellent backup practices down pat,
2. lurking about further on these forums to see what others have experienced,
3. reading this [guide]("https://help.ubuntu.com/community/DualBoot/Windows"),
4. familiarizing yourself and practicing with partitioning first, preferably on something like a USB stick or an external USB drive.

Until you are ready to make that decision, enjoy your new OS!

---

### Post by squakie on 2012-12-16
I have the same adapter in an old Dell laptop.  Wild Man's instructions were the same to me and they worked great - I didn't have to install build-essential or the headers at that time.  Just download the firmware zip he has attached in his message, copy it over to Linux - perhaps a USB stick, then run the commands.  It's possible that the /etc/modules file will need updating afterward, but do everything he has said and it should work.  If you lose it upon a reboot, just post back as it is a very easy fix.

---

### Post by TheOldHippie on 2012-12-17
> **Wild Man said:**
> Hi, this is the information on that card to get it working but it is best to have an ehternet connection, because as coffeecat said you will need to install the headers and build essential I believe even for this method but you can try it without first if you wish.

I like to use b43 driver it works better in most cases.

If you have any other driver installed you will need to remove it first.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Copy and paste commands for accuracy.
Thanks


I am extremely happy to inform all that were involved that they got me up and running and am in fact no posting this from a connection through Firefox on Ubuntu. Very first thing I'm doing. Many, many thanks for each and every suggestion. Brings back memories of bulletin boards. Will be watching and learning until I can give a little help also. Again, thanks.

The Old Hippie.
:KS

---

### Post by peterv1 on 2012-12-31
I am a new Ubunto user. This fixed my wireless problems. Thank you

---

