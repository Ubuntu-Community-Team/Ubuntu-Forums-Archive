---
title: "I want Ubuntu to succeed, but..."
date: 2007-11-27
forum: Recurring Discussions
---

### Post by jackpetrilli on 2007-11-27
As the title suggests, I LOVE the idea of open concept software and I want the "Ubuntu ideal" to succeed with all my heart.  So please understand the following critique is made with an aim towards improving the OS and not with a hidden malicious agenda.

1.  I initially wanted to install Ubuntu to an external USB drive.  NO GO.  I tried 2 different drives and a flash drive, all of which the Ubuntu Live CD said "would not accept address" or something like that.  Plugging in the drives later on while the Live CD was active, also did not work.  These drives were recognized easily by both Windows XP on the same computer, and Windows Vista on my other computer.

Next, I looked up solutions for this problem.  I found 3 different ones, all of which involved complicated terminal mode commands.  Having once been a DOS expert, I eventually was able to figure out how to drop down to root level and execute the different solutions, ALL OF WHICH DIDN'T WORK.

This shouldn't happen folks.  You want  this operating system to be accepted by a lot of people instead of just Linux power users, then you need to make damn sure that the system recognizes common USB devices on the fly.  And the average user is NOT going to be able to type in complicated terminal level commands, that will die if even an upper/lower case mistake is made.

2.  I have 3 computers at home, linked with a D-Link wireless router.  All of my Windows setups easily found the network and had internet connectivity.  As I write this message, I still cannot get Ubuntu to join this wireless network. (I'll be asking for more help on this in a separate thread.)  I've already tried joining an existing network and creating a new one.  This simply shouldn't happen.  I'm thinking that Ubuntu hasn't turned the "wireless radio" on this Lenovo laptop.  But if it hasn't, shouldn't this option be present on the wireless setup? Good thing that this isn't my only computer, otherwise I wouldn't have internet right now.  I can imagine that a lot of people would remove Ubuntu right away, if this happened to them on their only computer.

3.  Use plain English on your setup.  I made room for Ubuntu with partition magic.  I left 25 gig unpartitioned so that I could allow Ubuntu to auto install to that free space.  So what do I get?  Unintelligible computerese on the choices for partitioning.  I already knew that my existing partitions were called sda1 and sda2 by Ubuntu, but all the choices upon install said "sda".  If I hadn't already imaged my drive as a security measure, I doubt I would have had the courage to proceed on what I thought was the right choice.  (Turned out it was right.)

The choices should have said, "Hey, I see you have Windows on your drive and some unpartitioned free space, should I wipe out Windows or leave it alone and give you a dual boot setup." Now I am being a bit funny here, but PLAIN ENGLISH options for the non-power user would be much better.  

(How ridiculous that I had to do a "sudo -i" and an "fdisk -l" to actually make sure Ubuntu had done what I wanted it to do!)

Please folks, make this operating system usable for the average user.  I would love to see this OS "take off" and unseat the evil empire MS.  It's already so close to being there.  Gnome is a really great graphical interface and Ubuntu does so many things better than Windows.  It just needs to go that little extra mile (and get a kick-*** game) to really have a chance.

- Jack

---

### Post by aysiu on 2007-11-27
If you want help with your problems, post a support thread asking for help.

If you want to know constructive ways to improve Ubuntu, read [this thread](http://ubuntuforums.org/showthread.php?p=424972).

Threads of the "it's not ready" variety are great for recurring discussions that lead nowhere, so I've moved this thread to the recurring discussions subforum.

---

### Post by 23meg on 2007-11-27
> 3. Use plain English on your setup. I made room for Ubuntu with partition magic. I left 25 gig unpartitioned so that I could allow Ubuntu to auto install to that free space. So what do I get? Unintelligible computerese on the choices for partitioning. I already knew that my existing partitions were called sda1 and sda2 by Ubuntu, but all the choices upon install said "sda". If I hadn't already imaged my drive as a security measure, I doubt I would have had the courage to proceed on what I thought was the right choice. (Turned out it was right.)

The choices should have said, "Hey, I see you have Windows on your drive and some unpartitioned free space, should I wipe out Windows or leave it alone and give you a dual boot setup." Now I am being a bit funny here, but PLAIN ENGLISH options for the non-power user would be much better.


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/131084](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/131084)

---

### Post by Hybrid86 on 2007-11-27
100% agree. I currently run ubuntu off my laptop, and it took me quite a while (and quite a few terminal commands) to get it working properly.
it's actually pretty cool when you think about it though; with just a few simple changes, ubuntu could easily become to windows what firefox has become to internet explorer.

---

### Post by Xavieran on 2007-11-27
If you don't remember you actually had to install software on windows to get your wireless card working on windows...
and maybe it was easy for your card but peoples mileage differs...my moms computer is continously connecting and disconnecting from the network...thats the main reason she switched to linux :)...

And please understand this is a work in progress and Ubuntu is definitely making progress...My wireless card which didn't work in Fesity now works in Gutsy...

> The choices should have said, "Hey, I see you have Windows on your drive and some unpartitioned free space, should I wipe out Windows or leave it alone and give you a dual boot setup." Now I am being a bit funny here, but PLAIN ENGLISH options for the non-power user would be much better.

Not a bad Idea...maybe if it saw an NTFS partition it could ask you whether you wanted to touch it or not.

---

### Post by Bigbird999 on 2007-11-27
Re the plain English.  OP has a very valid point.  Just look at how many threads there are where a newb has lost all his data and/or overwritten his windows partition because of the cryptic description at the partition page.  And then the number of times it has been posted "Oh, you should have chosen manual install.

Plain English would go a long way to making things easier for new to Linux folks.

BB

---

### Post by Chrisj303 on 2007-11-28
I also agree on the 'Plain English' idea totally.

Things of major importance, such as the partition/install screen, which could result in disaster should be written as so *anybody* could understand it. 

Regarding the installer, many people want to install Ubuntu alongside Windows/OS X - I think the installer should also be clearer if this is the case.
I.e - A lot of people don't know what a 'SWAP' partition is. And don't understand the 'Mount Point's' setup page.

The option to install GRUB to the partition rather than the MBR sholdn't be hidden either - it should just be explained in *Plain English*!

---

