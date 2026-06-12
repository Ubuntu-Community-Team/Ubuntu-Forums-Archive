---
title: "Ubuntu dual-boot question. Help!?!?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by rdg11 on 2008-08-04
There may very well be a thread or post regarding this, but I just wanted to ask a very specific question. Now I downloaded the .iso from ubuntu.com and ran it on Daemon Tools. What I want to do is install Ubuntu as its own operating system (and then reinstall Windows [to clean it and set it up so it can't go online] over the amount of space I have set aside for Windows. How can I go about doing this? I have an 80 gb harddrive (meaning I actually have 74.5 gb of space) and I would like to devote 45 gb to Ubuntu and the rest to Windows. So...help!?

If you have any questions feel free, I'm here trying to figure this out, and have turned on instant email notification.

---

### Post by ConMan318 on 2008-08-04
Install Windows first and don't worry about the space it takes up.  Then install Ubuntu over it (it's easier in this order because of the bootloader setup, and the partitioning is easier this way).  When you install Ubuntu you can allocate 45 GB for Ubuntu and the rest to Windows.

---

### Post by bpowell2005 on 2008-08-04
How about installing Ubuntu, and then downloading and installing VMWare Player, and then installing Windows as a virtual machine...then you could control the connectivity aspects of the Virtual machine...you said you didn't want Windows to connect to the internet, this would be a good solution.

I haven't tried this myself, but it should work.

---

### Post by cdtech on 2008-08-04
Here's a good site to check out:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paqman on 2008-08-04
It's easiest to set up Windows first, then Ubuntu. That's because Windows always assumes it's the only operating system, but Ubuntu is quite happy to share the drive with others. If you install Windows second it overwrites the Ubuntu bootloader and you have to go back and reinstall it. Which is not a big haslle, but a hassle nontheless.

So if you want a clean install of Windows, do that first. Defrag Windows thoroughly once you've installed everything you need. Then you can think about Ubuntu. The Ubuntu installer can handle creating the partitions you need to install.

---

### Post by beanhead on 2008-08-04
Ok your running xp? If so you can use xp to set it up to make it very easy.
go to my computer right click and a list will appear, select manage, then storage, you should defragment the disc, then make a new partition, chose a size then write it. then set your bios to boot from the cd dvd drive. enter set up and change the boot order when your computer starts so cd dvd drive is at the top. then when you select install whle running ubuntu you will have a clean place to put your new ubuntu os, bear in mind that ubuntu will control your boot manager and you will chose between windows and ubuntu when your computer  starts. should be very easy if you have any questions just post away WELCOME TO UBUNTU !!!!  ,ron

---

### Post by rdg11 on 2008-08-04
Thanks for all the replies. Follow-up question:

So let's say I install Windows first and set it up and everything. Then I want to install Ubuntu as it's own partition. What do I select, is it what's indicated in the picture below?

[IMG]http://img46.imageshack.us/img46/9646/86923927fo5.jpg[/IMG]

---

### Post by lisati on 2008-08-04
> **rdg11 said:**
> Thanks for all the replies. Follow-up question:

So let's say I install Windows first and set it up and everything. Then I want to install Ubuntu as it's own partition. What do I select, is it what's indicated in the picture below?

[IMG]http://img46.imageshack.us/img46/9646/86923927fo5.jpg[/IMG]
The way shown on the screenshot will install Ubuntu "in" Windows. Another way is to leave the CD in the disk drive, and reboot from the CD. Doing so will let you set things up so that you don't need to start Windows to use Ubuntu.

---

### Post by Paqman on 2008-08-04
> **rdg11 said:**
> 
So let's say I install Windows first and set it up and everything. Then I want to install Ubuntu as it's own partition. What do I select, is it what's indicated in the picture below?


If you click that button, Ubuntu will be set up on virtual hard drive located on your Windows partition. It's a lot easier than creating new partitions, so unless you really feel a burning desire to get into partitioning i'd go for it.

You can always transfer your Ubuntu to it's own partition later if you like.

---

### Post by rdg11 on 2008-08-04
> **lisati said:**
> The way shown on the screenshot will install Ubuntu "in" Windows. Another way is to leave the CD in the disk drive, and reboot from the CD. Doing so will let you set things up so that you don't need to start Windows to use Ubuntu.
Problem is, I'm installing it from a disk image (using Daemon Tools) and even though I've told it to Automount and Autostart, it's not letting me reboot from the CD. Is there another virtual CD program that might work better?

---

### Post by Sunfist on 2008-08-04
Well now that you bring it up there are actually 2 ways to install Ubuntu on a Windows install, what you have highlighted is called Wubi, which requires NO partitioning work at all and actually installs Ubuntu Linux as a windows application (sort of). That is by far the easiest way to do it, but if you want Linux running all by itself in its own partition you would pick the top option and when you get to the partitioning part of it choose, Use largest Free space, assuming you have repartitioned your HD to leave a chunk of free space for Ubuntu to use.

---

### Post by Paqman on 2008-08-04
> **lisati said:**
> Doing so will let you set things up so that you don't need to start Windows to use Ubuntu.

That's not quite right. You don't need to start Windows to use Wubi-installed Ubuntu. Wubi is a proper dual-boot, it just uses a virtual partition instead of a physical one.

---

### Post by Paqman on 2008-08-04
> **rdg11 said:**
> Problem is, I'm installing it from a disk image (using Daemon Tools) and even though I've told it to Automount and Autostart, it's not letting me reboot from the CD. Is there another virtual CD program that might work better?

You're normally supposed to burn the .iso to a disk, but Wubi might work with the .iso mounted in Windows.

---

### Post by rdg11 on 2008-08-04
I've managed to do it with Daemon Tools on Windows, but I may just burn it to a disk. Another question, you guys all seem very knowledgeable.

Can I set up Windows (I have Norton for virus protection/firewall) so that nothing at all can access the Internet unless I give it permission. i.e. **if the only thing I wanted to be able to access the Internet (besides Windows updates themselves obviously) would be an online video game? Or can the program Wine sufficiently run Steam/Counter-Strike**. Thanks!

---

### Post by HotCupOfJava on 2008-08-04
OK - I have done this several times and here is what I suggest:

Burn that .iso to a disk. That will make your life WAY easier (your burning software should give you an option on burning "Disk Images", which is what an .iso is). 

Since you want Windows "clean", reinstall Windows first. It is MUCH easier to create a dual-boot with Windows already installed than vice-versa.

Once Windows is installed, load your Ubuntu CD. It will open the live desktop. You can then go to "System" on the top toolbar and open an application called "Partition Editor". This is the GParted partition editor. Use it to resize the Windows partition down to what you want. Free (no filesystem) space will be created on the hard drive when you do this. 

Restart the computer with the CD in it. Choose "Install Ubuntu". You will be asked a series of questions. When you get to the part where it presents several install options, choose "Guided - use largest contiguous free space". Finish out the installation. When you restart again, you will get a choice of operating systems to boot from.

The first time you boot back into Windows, it may want to examine the filesystem. Let it do so. Everything should work fine.

Hope this helps.

---

### Post by Paqman on 2008-08-04
> **rdg11 said:**
> 
Can I set up Windows (I have Norton for virus protection/firewall) so that nothing at all can access the Internet unless I give it permission. 

I'm sure most Windows firewall apps could do this for you. It might take a bit of tweaking.

You'd probably also want to allow Windows updates a connection if you're worried about security.

---

