---
title: "WUBI Issue"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by lh12345 on 2008-08-31
I installed WUBI onto a seperate blank partition. Win XP is drive C and The new Drive is F (D and E are optical). I get a dual boot menu when it reboots, and if I select UBUNTU it puts me into GRUB. I'm a Windows expert, but I'm totally lost here even after reading parts of the grub manual (which would be nice if I could run commands with windows running but its all text mode). I've written many scripts but not sure where to turn here. Could anyone tell me how to bootstrap ubuntu from here? Thanks

---

### Post by _Atreides_ on 2008-08-31
What do you mean it takes you into GRUB? The dual boot menu is grub in action.

---

### Post by lh12345 on 2008-08-31
> **_Atreides_ said:**
> What do you mean it takes you into GRUB? The dual boot menu is grub in action.

First it says choose:

Windows XP
Ubuntu

When I hit enter on Ubuntu, I see:

[Minimal BASH like ..(sic)..device/filename]

GRUB>

Where do I go from here? I did some research but not sure specifially what to do.

---

### Post by Elfy on 2008-08-31
What is it you are trying to achieve here, from my understanding wubi will give you the option of windows and buntu, choosing buntu will get you grub from which to boot into buntu; though I've not installed through wubi.

---

### Post by Mine's Ultimate R on 2008-08-31
sounds like there was a problem with the install...
it shouldn't do that, after choosing ubuntu, it takes you into grub automatically to startup ubuntu

_Atreides_: the dual boot menu is the windows boot manager, not grub

---

### Post by lh12345 on 2008-08-31
> **forestpixie said:**
> What is it you are trying to achieve here, from my understanding wubi will give you the option of windows and buntu, choosing buntu will get you grub from which to boot into buntu; though I've not installed through wubi.

Well if I have the GRUB command line, what do I do next to get to buntu?

---

### Post by Elfy on 2008-08-31
aah - grub's not installed properly then it seems.

Try this

```
find /boot/grub/stage1
```
it should echo where it is - maybe hd0,1 - use that to set tthe root

```
grub> root (hd0,1)
``` - change to suit
install grub
```
grub> setup (hd0)
``` - change 0 if find boot fro instance gives hd1,0
```
grub> quit
```
 Then reboot, but be aware they are the commands to boot a normal buntu installation

---

### Post by lh12345 on 2008-08-31
> **forestpixie said:**
> aah - grub's not installed properly then it seems.

Try this

```
find /boot/grub/stage1
```
it should echo where it is - maybe hd0,1 - use that to set tthe root

```
grub> root (hd0,1)
``` - change to suit
install grub
```
grub> setup (hd0)
``` - change 0 if find boot fro instance gives hd1,0
```
grub> quit
```
 Then reboot, but be aware they are the commands to boot a normal buntu installation

Tried, no results. /boot/grub/stage1 is not found, seems like it is searching my floppy. 

root reports
(hd0,0) and is an unrecognized file system 0x0

setup fails because it cant find stage1.

Is there anything I can edit while I am in windows?

I think WUBI screwed up because I installed on windows logical drive F and it its really the second partition on the drive.

---

### Post by bdfoster on 2008-08-31
What was the reason why you didn't install off of a disk or download?

---

### Post by Elfy on 2008-08-31
I have to say I'm not sure how to deal with wubi - it's quite new as an official method and I've never used it, however you can access it from within windows with the aid of a driver. It might be best to access it from your livecd assuming you have one, boot with that and then we can look at getting at it's virtual drive from there.

There are 2 specific parts of the wiki which will help to acces the files -
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I access the Wubi files from Windows?

---

### Post by lh12345 on 2008-08-31
> **bdfoster said:**
> What was the reason why you didn't install off of a disk or download?

Well, I bought into the fact that it works well with windows, but I'm thinking that its probably designed to be installed to the C windows drive as a virtual partition. Since I have a partition I'm going to Install it straight. Is the iso included with WUBI ok to burn and install UBUNTU?

ubuntu-8.04.1-desktop-i386.iso?

---

### Post by Mine's Ultimate R on 2008-08-31
> **lh12345 said:**
> Well if I have the GRUB command line, what do I do next to get to buntu?

Oh yeah, this happened to me. What I did was re-install ubuntu ):
so i think we have similar problems, but no one was able to help me :/

yes you should be able to use that iso to install ubuntu
doesn't it ask you for options like "full install", "install inside windows", and "demo"?

---

### Post by Elfy on 2008-08-31
Yes that will allow you to install buntu; installing the wubi to a seperate partition shouldn't make any difference.

Make sure it's burnt as an iso/image and it will be fine as long as the iso is intact, reboot with the cd in the drive and as long BIOS is set to boot from cd first it will give the menu, if you haven't checked the md5sum use the menu option to check the cd for defects at least.

---

### Post by lh12345 on 2008-08-31
> **Mine's Ultimate R said:**
> Oh yeah, this happened to me. What I did was re-install ubuntu ):
so i think we have similar problems, but no one was able to help me :/

yes you should be able to use that iso to install ubuntu
doesn't it ask you for options like "full install", "install inside windows", and "demo"?

Yeah, I'm burning it now so I can try it off the CD, later I will install.

Thanks

---

### Post by lh12345 on 2008-08-31
> **forestpixie said:**
> Yes that will allow you to install buntu; installing the wubi to a seperate partition shouldn't make any difference.

Make sure it's burnt as an iso/image and it will be fine as long as the iso is intact, reboot with the cd in the drive and as long BIOS is set to boot from cd first it will give the menu, if you haven't checked the md5sum use the menu option to check the cd for defects at least.

It don't like my RW CD, I think I have to get one of the 80min CDs, not enuf space...

---

### Post by L Campbell on 2008-08-31
> **lh12345 said:**
> I installed WUBI onto a seperate blank partition. Win XP is drive C and The new Drive is F (D and E are optical). I get a dual boot menu when it reboots, and if I select UBUNTU it puts me into GRUB. I'm a Windows expert, but I'm totally lost here even after reading parts of the grub manual (which would be nice if I could run commands with windows running but its all text mode). I've written many scripts but not sure where to turn here. Could anyone tell me how to bootstrap ubuntu from here? Thanks

I'm a real Linux dummy (please believe me) but all I did was go here:-

[http://wubi-installer.org/](http://wubi-installer.org/)

and let it install itself.  It seemed to install faultlessly and seems to work perfectly well for me.

---

### Post by lh12345 on 2008-08-31
> **L Campbell said:**
> I'm a real Linux dummy (please believe me) but all I did was go here:-

[http://wubi-installer.org/](http://wubi-installer.org/)

and let it install itself.  It seemed to install faultlessly and seems to work perfectly well for me.

did you install it to your windows drive?

---

### Post by Elfy on 2008-08-31
> **lh12345 said:**
> It don't like my RW CD, I think I have to get one of the 80min CDs, not enuf space...

How big is the iso you have to burn? You will need a 700Mb cd to burn it.

---

### Post by Mine's Ultimate R on 2008-08-31
> **lh12345 said:**
> did you install it to your windows drive?


actually i installed it to my windows drive and it works fine

wait...did you say you did some partitioning? because wubi doesn't need any partitioning and partitions itself

---

### Post by fidamehran on 2008-08-31
Come on, people. Why all the problem? From the looks of the problem, there was some problem either with the Wubi or the Ubuntu install.
Dear "lh12345", since you installed through Wubi, it should be very easy to uninstall from Windows Add/Remove Programs. Just do that, then re-download Wubi and the Ubuntu installer ISO or maybe burn the Ubuntu CD ISO (please please check the md5 checksum for integrity of the download) and install through Wubi.

I have installed Ubuntu in my D: Drive (my Windows drive is C;). So rest assured that no problem happens if you install Ubuntu into any drive.

Also please make sure you download the main CD Installer ISO, not the Alternate CD image from Ubuntu.com.

Just install the fresh downloaded/CD burned items through Wubi in your drive of choice with the largest space you can give to Ubuntu (preferably 10 GB) and INstall.

Enjoy Ubuntu.

---

### Post by L Campbell on 2008-08-31
> **lh12345 said:**
> did you install it to your windows drive?


Yes, as far as I know that's where it is.

I'm not at my house right now so I can't check but I did not direct the installation to do anything other than what it wanted to do.

I checked, it is in C:\ Documents and Settings

---

### Post by Mine's Ultimate R on 2008-08-31
same, and i think fidamehran is right...you could even install wubi to an external hard drive (not something i would do, but you could)

---

### Post by fidamehran on 2008-09-01
> **Mine's Ultimate R said:**
> same, and i think fidamehran is right...you could even install wubi to an external hard drive (not something i would do, but you could)

See, I told you. Can I get a thanks? :guitar:

---

### Post by Mine's Ultimate R on 2008-09-02
yeah i only agree with you because what you said is basically what i had said earlier lol

i said that there must be something wrong with the install

but i kind of want to find out what's wrong and if it could be fixed because i had a similar problem once...oh yeah, i lost all my settings and stuff ):

---

### Post by noughtypixy on 2009-03-23
am fairly new to ubuntu myself but had a similar problem when instaling it on a second machine after using successfully on my first for some time
was perplexed at first, then realised that the drive I had installed to on machine 2 was formated as ntfs and this was stopping it work
I re,formated the drive (it was only 16G and full of Norton ghost backup files {was quite suprised that norton had partitioned itself so much drive especialy as had uninstalled in favor of another antivirus over a year ago}) as fat32 tried again and success

---

