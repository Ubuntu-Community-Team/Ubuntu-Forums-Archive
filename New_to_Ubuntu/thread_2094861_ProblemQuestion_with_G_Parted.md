---
title: "Problem/Question with G Parted"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by ChessMasterJoe on 2012-12-15
Hey guys, 

I was on here about a month ago and you helped me get my wifi card working on a dell laptop. Thanks again! 

I was wondering if you could help me use G Part to partition my hard drive so I could dual boot with Windows 7. 

I tried using G parted. (Device, Create Partition Editor and then a got an error message "**1 partition is currently active on device/dev/sda. **A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.

Any suggestion.

---

### Post by haqking on 2012-12-15
> **ChessMasterJoe said:**
> Hey guys, 

I was on here about a month ago and you helped me get my wifi card working on a dell laptop. Thanks again! 

I was wondering if you could help me use G Part to partition my hard drive so I could dual boot with Windows 7. 

I tried using G parted. (Device, Create Partition Editor and then a got an error message "**1 partition is currently active on device/dev/sda. **A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.

Any suggestion.

it would need to be unmounted, best way is to boot to a Gparted Live DVD/USB and not run it from within Ubuntu

---

### Post by mlentink on 2012-12-15
Please never use GParted from a mounted harddisk partition. The mounted partition GParted is complaining about is most likely the one you booted from, and for obvious reasons you cannot remove that. 

So yes,as haqking said: boot from a LiveUSB (or LiveCD) 

But first: BACK UP  all your valuable data!

---

### Post by Cheesemill on 2012-12-15
Also I don't think you want to create a new partition table, doing so will delete all of the existing partitions on the drive.

If you can post a screenshot of gparted and tell us what you are trying to achieve we can probably me more help.

---

### Post by ChessMasterJoe on 2012-12-15
I was thinking I would have to boot from a Live CD. How would I go about making one of those? I already have the G Parted program in my computer. 

I'm not even sure hove to take a screen shot. Does Unbuntu 12.1 having anything comparable to the Sniping tool in windows. 

I want Windows 7 so I can run varies chess and weather programs. All of which were very expensive. 

I guess I have to put all the episodes of Star Trek on another hard drive. 


There's isn't a way to spit the hard drive in half without effecting the data inside? This may seem like a stupid question, but since I have about 600gigs free, why can't I just trim 100gigs off and make the new drive from which I will boat Windows.

---

### Post by Cheesemill on 2012-12-15
> **ChessMasterJoe said:**
> There's isn't a way to spit the hard drive in half without effecting the data inside? This may seem like a stupid question, but since I have about 600gigs free, why can't I just trim 100gigs off and make the new drive from which I will boat Windows.

You can do this with gparted, but you can't do it from your installed copy because the drive you want to resize is currently in use, you need to boot from a Live CD so that you aren't using the drive.

You may already have a Live CD, it's the one you installed Ubuntu with. If not then download and new copy of the Ubuntu disk and either burn it to CD or create a USB stick with it, instructions are on the website [here]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install") (links to different instructions are on the right).

To take a screenshot you can use the screenshot tool that comes with Ubuntu, just hit the Super key and start typing 'screenshot'.

---

### Post by GordThompson on 2012-12-15
I hope I am not further confusing the issue too much, but...

> **ChessMasterJoe said:**
> since I have about 600gigs free, why can't I just trim 100gigs off and make the new drive from which I will boat Windows.
It sounds like the machine currently has just Ubuntu on it, and you want to add Windows_7 as a second OS. If that is correct then before you dive in and start repartitioning you may want to search for more information on the following:

1. I gather from a number of other threads that installing Windows (with the intention of dual-booting) *after *Ubuntu can lead to confusion because the Windows boot loader replaces the Ubuntu boot loader (which is called 'GRUB', I believe) and Ubuntu "goes away". It's still there, but you don't get the choice of which OS to start (you just go straight into Windows). It's almost certainly fixable, but it could be a nuisance.

2. If the Windows applications you plan to use are not hugely resource-intensive (e.g., high-resolution, high-speed 3D graphics; massive memory requirements) then you might consider using VirtualBox in Ubuntu to run Windows_7 as a virtual machine. There is a version of VirtualBox available from the Ubuntu Software Centre that could very well meet your needs without having to mess around with dual-booting. (If you prefer to use Synaptic Package Manager then you can install 'virtualbox-qt' from there too.)

---

### Post by vallvi on 2012-12-15
yes,
trying to install windows after you've installed ubuntu can mess things up with the boot system. The safest to do is to start from scratch: install windows, and after that install ubuntu again. You don't need gparted for that.

---

### Post by Cheesemill on 2012-12-15
You don't need to re-install everything from scratch, that's completely unnecessary.

Just be aware that installing Windows will overwrite the Ubuntu boot-loader, it only takes seconds to get it back however.

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

---

### Post by oldfred on 2012-12-15
More info on Forum, please use paper clip to attach screen shots:
 Guide to Forum features ** INCLUDES: Beans, titles, searching, and more 
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
How to attach file, screenshots
[http://ubuntuforums.org/showpost.php?p=12229098&postcount=4](http://ubuntuforums.org/showpost.php?p=12229098&postcount=4)
[http://i.stack.imgur.com/0E6qS.png](http://i.stack.imgur.com/0E6qS.png)


       
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by offgridguy on 2012-12-15
oldfred; Thank's again for even more helpful url's.

---

