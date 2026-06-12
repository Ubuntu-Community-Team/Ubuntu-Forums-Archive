---
title: "Shrinking Partitions"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by Kratos758 on 2013-11-24
Hi All,
New here, very excited to be here, and my goal is install Ubuntu 13.10 to Dual-boot with Windows 8 64-bit on my Asus laptop.

At the moment I'm putting together the last of my system images, recovery disks and OEM recovery files.
After this I'll put the Ubuntu iso onto a USB to boot and install from there.

I realise partition separation is somewhat personal, however; my question is:
I've got a C: and D: drive that could be reduced in volume to make way for Ubuntu - Should I shrink the C: (OS) drive (will allow to shrink to ~200GB from 300GB) or the D: (Data) drive (From 400GB, all of which is currently unallocated).
The guide I'm following says to shrink the partition with the OS on it (in my case, Win8 is on C drive).
Just wondering the differences here?
And is ~50GB enough on a separate partition for me to learn and play around with Ubuntu for awhile (my main doc works, gaming, music storage, etc will be from Win8)

It might be worth noting I am an absolute beginner to this. I've been doing some reading about terminal, I can use MS-DOS following advice/guides given, but other than that I'm new to this but this is just something I want to learn and experience for myself.

Any help is much appreciated!!

Edit: So I've been playing around, I created a partition from C: drive of 40GB, then booted into Ubuntu and went to install it, but it's not letting me create all the three partitions from within this partition I split in disc management (if this makes sense?). I just extended the 40GB back into C: drive, and I'm going to see if I can use D: drive at all as that is a 400GB drive.

---

### Post by Impavidus on 2013-11-24
For Ubuntu it doesn't really matter which one you shrink, as long as Windows is happy. One thing however, your will be able to use your D partition as a shared data partition, accessible both from Windows and Ubuntu. Don't hibernate Windows and disable fast boot to do so. You can better not use the C partition for shared data. You may also need a few GB swap partition.

50GB is more than enough to play with Ubuntu

---

### Post by Kratos758 on 2013-11-24
Thanks for the reply Impavidus.
Well as it so happens, I just completed the installation. First go and it seems to be working BRILLIANT.
I Power On my laptop, GRUB comes up with four options I believe, and both Ubuntu and Windows Boot Manager options boot right into their systems.

I ended up using the D: drive
- I shrunk the volume using Disc Management from 400GB -> 200GB
- When I went to install Ubuntu, I think I created the first partition at 50GB, the /Home at 100GB and the SWAP partition at 20GB (Not 100% sure on this, can I check this?)

And yeah mate, it seems the D: drive is now I guess a shared partition between the two operating systems, which is great.
I'll have to have a bit more of a play around in Ubuntu, but so far so good, great start to myself in experiencing Linux :D

Also, should I change back the fast boot settings, I disabled them in UEFI to boot the LiveUSB for Linux? And I think Secure Boot might be disabled too?

Thanks.

Edit: I've started to get a feel within Ubuntu, how do I start to look at downloading programs and plugins so I can play certain music and video types?
And I've noticed (because I'm on a shared network) that I can see other people's music libraries?
Seeing how I'm new to this, how can I look at my privacy/security settings so that nobody on this network can see into my system files, content or what I have/have not shared?

---

### Post by Mark Phelps on 2013-11-24
> how do I start to look at downloading programs and plugins so I can play certain music and video types?

You can start by creating a new thread for the new questions.  Folks generally respond to threads based on their titles, and your current title says nothing about needing help with playing movies or music.

Also, and if you did install Ubuntu in your "D:" partition, then you used WUBI to do that -- which has been discontinued.  You would have done better waiting for advice on how to create new partitions and install Ubuntu there.

---

### Post by VMC on 2013-11-24
> **Kratos758 said:**
> ...
- When I went to install Ubuntu, I think I created the first partition at 50GB, the /Home at 100GB and the SWAP partition at 20GB (Not 100% sure on this, can I check this?)...
Partition usage, assignment is actually a personal issue outside of root "/". I use to maintain massive Unix systems and we had several partitions, and several "raid" mirror disks. When I went to Linux, I use only one partition "/" to rule them all. I have never had any issues. Ever. 

It all depends on your usage - what programs you install and how many are running at any one time. How much ram you have makes a big difference.

As far as the 20gig Swap, I think that is excessive. Mine is 2gig, and it rarely if ever gets used. There was a rule-of-thumb of double your ram equals the Swap size. Also I don't know if you will ever use 100gig inside your home folder.

After you use the system for a while, and install programs of choice, then check your partition usage for a more accurate count.

All of this will become more clear as you use Linux.

---

### Post by oldfred on 2013-11-24
You do not have to turn secure boot back on unless you have one of the few Windows configurations that only boots with it on. 
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

You probably should not turn fast boot back on even with a separate shared NTFS data partition. Windows saves drive info and anything you copy into Windows from Ubuntu will be lost as Windows fast boot restores old configuration/file info.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I also suggest separate threads for different topics as title is vital to get those who may know more info may only respond to titles on that topic.
You can also search forum with its search, but Google search also works. 
 But using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term
And:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

