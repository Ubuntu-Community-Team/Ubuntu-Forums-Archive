---
title: "add Windows?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by syerges on 2012-01-14
I have deleted Windows from my system and went completely to Ubuntu.... now I find that I need Windows for certain things and have no clue how I can manage to put it back on without messing up Ubuntu. I tried using gparted but I can't unmount the ubuntu partition to make room for Windows. Is there a seemless way to do this?

---

### Post by nothingspecial on 2012-01-14
You would need to do that from a live cd/usb. You cannot resize/change a mounted partition.

Another option, if you have the RAM is to install windows to a virtual machine.

---

### Post by syerges on 2012-01-14
I have been debating the Virtual Machine option...I was really hoping to not have to go there though. Is it somehow possible to move Ubuntu as it stand on my desktop somewhere else without losing how I have it looking and set up? like to a USB/CD? I've been having trouble accomplishing this as well in my efforts...I'm not as computer terminology educated as most and descriptions are complex when looking for software to do this.

---

### Post by aeronutt on 2012-01-14
> **syerges said:**
> I have been debating the Virtual Machine option...I was really hoping to not have to go there though. Is it somehow possible to move Ubuntu as it stand on my desktop somewhere else without losing how I have it looking and set up? like to a USB/CD? I've been having trouble accomplishing this as well in my efforts...I'm not as computer terminology educated as most and descriptions are complex when looking for software to do this.

Create a live CD or USB by following the pretty simple directions on the Ubuntu home page.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Boot from live CD or USB.

From there, you can run gparted and resize your current partition to make room for Windows.

---

### Post by syerges on 2012-01-14
that would be a fresh version... i want my edited one....

---

### Post by aeronutt on 2012-01-14
> **syerges said:**
> that would be a fresh version... i want my edited one....

The above directions will allow you to KEEP your current version of ubuntu. Follow the steps as stated:

Create live CD.
Use the live CD to run gparted and resize your CURRENT partition of Ubuntu on your harddisk. This will NOT load a new version of Ubuntu, unless you explicitly tell the live CD boot to load a new version. All you're doing is using gparted running from the CD to resize your partition, which you must do so that the current Ubuntu on your harddisk is not mounted.

Use gparted to created a new partition to load Windows.

(Recommend you backup any important data prior to repartitioning...but I've never had gparted corrupt data.)

---

### Post by Kingnothing412 on 2012-01-14
> **syerges said:**
> I have deleted Windows from my system and went completely to Ubuntu.... now I find that I need Windows for certain things and have no clue how I can manage to put it back on without messing up Ubuntu. I tried using gparted but I can't unmount the ubuntu partition to make room for Windows. Is there a seemless way to do this?
What programs n stuff do you need?  Mean what certain things? Ubuntu might be able to run them , theres always an equal alternative for windows programs in linux i think

---

### Post by syerges on 2012-01-14
no there's not, not even close... my GPS for one... there are workarounds for the others but I'm tired of working around stuff. I need Windows for certain things and was silly thinking anything could replace it. Linux is good for speed and security.... In all other area's it's substandard. I'm just going to try out XUbuntu and KUbuntu to see if I like either of those first...then start fresh.

---

### Post by aeronutt on 2012-01-14
> **syerges said:**
> no there's not, not even close... my GPS for one... there are workarounds for the others but I'm tired of working around stuff. I need Windows for certain things and was silly thinking anything could replace it. Linux is good for speed and security.... In all other area's it's substandard. I'm just going to try out XUbuntu and KUbuntu to see if I like either of those first...then start fresh.

The applications available in Xubunut, Kubuntu are the same as Ubuntu.

---

### Post by oldfred on 2012-01-14
What Windows do you have to reinstall? If you still have your recovery partition or made the recovery DVDs you will reinstall to exactly as you purchased system. That usually reinstalls to the entire drive or no Ubuntu. Only if you have a legal full install copy will you be able to easily install without deleting Ubuntu.

Windows only installs to a primary NTFS partition with the boot flag. The recovery version is not a Windows installer but just an image of hard drive to restore.

---

### Post by syerges on 2012-01-14
I have to install Windows regardless so I'm not trying them to see if they have other applications but rather to see if they start out similar to my liking and how they work with my system, if they're any faster with my system, if their interface is any better and so forth. If I have to run off my usb, I might as well explore.

---

### Post by Kingnothing412 on 2012-01-15
Im not really sure about this but i think that those have less applications and don't support as many things as ubuntu.....Also , ubuntu is very customizable as well i think , so you can make it look however you want if im not wrong. (that's what ive understood at least from all the reviews , articles and videos i've seen about ubuntu. Nothing really professional to be honest , i know nothing :/ )

---

### Post by nothingspecial on 2012-01-15
You need to boot the live cd to shrink your Ubuntu Partition and create one for windows.

Then install windows to the newly created partition.

---

### Post by syerges on 2012-01-17
I gave up and put Windows on the second hard-drive, on a computer from the attack. I just don't think Ubuntu and Windows gets along enough for the head-aches.

---

### Post by s1wood on 2012-01-17
I did  install Wndows on Virtualbox so I could use my Yahoo Sitebuilder. - it works very well. I just haven't bothered installing all the updates.

Susan

---

### Post by tkabir11 on 2012-01-17
> **syerges said:**
> **I have been debating the Virtual Machine option...I was really hoping to not have to go there though**. Is it somehow possible to move Ubuntu as it stand on my desktop somewhere else without losing how I have it looking and set up? like to a USB/CD? I've been having trouble accomplishing this as well in my efforts...I'm not as computer terminology educated as most and descriptions are complex when looking for software to do this.

And why are you debating? I know VM isn't an ideal option if you have low RAM against memory-hogging software to run in windows (specially games). But you shouldn't really write it off if you're thinking its difficult to set up- compared to setting up/partitioning hard disk for a dual boot, I'd say VM is a much easier option.

---

### Post by syerges on 2012-01-18
I did install VM - networking problems that I didn't want to mess with, I installed it as dual boot, it didn't want to show Windows XP as an option, I can guess that it wanted XP to be first but I didn't want to have to keep moving stuff around so now it works peacefully upon it's own PC and allows my PC to have it's single function as my pc... It's what I should have done in the first place I guess since it's what I was really looking for even if I didn't know it.

---

