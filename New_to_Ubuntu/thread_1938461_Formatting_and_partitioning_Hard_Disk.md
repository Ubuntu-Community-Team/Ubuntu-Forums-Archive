---
title: "Formatting and partitioning Hard Disk"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by rsb61 on 2012-03-09
[LEFT]I have an old desktop which stopped booting up in Windows XP.  I installed Ubuntu 11.10 to try and the 40GB HD is partitioned into 25GB for (the useless) WinXP and 15 GB for Ubuntu.

I like Ubuntu so much that I plan on installing 12.04 when it is released.  However, I may want to add something like Linux Mint in the future.

Here's my question.  Since I no longer want to keep the XP partition what are your recommendations for formating and partitioning the boot drive?  Please remember I want to leave it open to maybe add another Linux OS in the future.

Can I just let Ubuntu be the only OS and the later (other) Linux will take care of the partitioning correctly?  The most likely one is either Mint or Zorin; both are Ubuntu based.

Thanks 
[/LEFT]

---

### Post by cbanakis on 2012-03-09
> **rsb61 said:**
> [LEFT]Can I just let Ubuntu be the only OS and the later (other) Linux will take care of the partitioning correctly?  The most likely one is either Mint or Zorin; both are Ubuntu based.  
[/LEFT]
 
I believe so.

I have not tried dual booting, because I just switched straight over to Ubuntu.

But I have messed with several other distros, including Zorin, and Mint.

And as far as I know, they all give you the same
"Install along side current operating system"
option during setup.

---

### Post by kikotiger on 2012-03-09
My suggestion is that when installing Ubuntu 12.04 you do a fresh install. Format your whole drive and partition the drive into two equally sizes (after assigning a swap partition) using ext4, install Ubuntu 12.04 in one of the partitions and leave the other for future OS installation. If you decide that you will not install another linux OS you can use the other partition as an extra drive or delete it and extend your Ubuntu partition.

---

### Post by cbanakis on 2012-03-09
Another option...

If you mainly want to run Ubuntu, but still want to mess with other os's.

Install Ubuntu 12.04 (Use the whole disk for Ubuntu)
Get virtualbox from the software center.

Then you can have infinite OS's installed in virtual box, where you can easily check out different distros.

If you find one you don't like, you just delete the virtual machine from virtualbox.

no need for partitioning of any kind.
clean, smooth, and easy.

---

### Post by charleseddy on 2012-03-09
> **cbanakis said:**
> Another option...

If you mainly want to run Ubuntu, but still want to mess with other os's.

Install Ubuntu 12.04 (Use the whole disk for Ubuntu)
Get virtualbox from the software center.

Then you can have infinite OS's installed in virtual box, where you can easily check out different distros.

If you find one you don't like, you just delete the virtual machine from virtualbox.

no need for partitioning of any kind.
clean, smooth, and easy.

Unfortunately, I have to put forward that, in this case, what you said about VMs is incorrect cbanakisthis, given the context. Rsb61 spoke of an *old* desktop that couldn't even boot XP (with a 40gb hard drive even). Therefore, it's clear that Virtualbox will probably have trouble working well, since it depends on the resources that the host system can give it.

In my opinion, if you want to play with your system a bit, Rsb61, I would give a 15-20 or so GB partition to Ubuntu (with I'm guessiong ~2GB to the swap, which should generally be 1.5x or 2x the RAM the system has). If you know your other hard drives will be Linux, go ahead and format them as ext4 during your Ubuntu setup, and that way they'll be ready and you won't even have to format them with your other distro. No matter what, you'll always have the choice to delete one or other and resize them, as Gparted generally does a good job of safely resizing linux hard drives.

If I may also suggest, since you're looking at other OSs for your second partition, I'd recommend another linux OS than Mint...You're already using something with a Ubuntu base, so if you want to really experiment with linux, why stick with what you already started with? There are plenty of others. I love Ubuntu, but I'm all about trying the plethora of options that are out there too...nothing prevents you from coming back after having tried the alternatives!

At any rate, good luck with all this, and don't hesitate to ask further questions!!!

---

### Post by cmcanulty on 2012-03-09
be aware that ubuntu is no longer a lightweight system. If it is an old machine try xubuntu or Lubuntu that require less cpu and ram

---

### Post by ixtok on 2012-03-09
> **cmcanulty said:**
> be aware that ubuntu is no longer a lightweight system. If it is an old machine try xubuntu or lubuntu that require less cpu and ram

+1

---

### Post by charleseddy on 2012-03-09
> **cmcanulty said:**
> be aware that ubuntu is no longer a lightweight system. If it is an old machine try xubuntu or Lubuntu that require less cpu and ram

Agreed, XFCE is definitely a better option. :KS

---

### Post by rsb61 on 2012-03-09
Thank you all, great suggestions.

In answer to a couple of things, the desktop has a 2.4GHz processor with 1GB RAM.  The 40GB HD is my boot drive and is only for my OS (formerly Win XP).  I have a separate 250GB HD for data and programs.

The only reason to have Mint or Zorin as the second OS is for my wife to use this system.  But really, like charleseddy suggested, I do want play some more with other versions of Linux.

Thanks again everyone

---

### Post by audiomick on 2012-03-09
I would suggest setting up a separate /home partition for your various Linux installs.

Bear in mind that once you have set up a swap partition, any future Linux installs should see and incorporate and use it. All things being equal, you shouldn't have to make a new swap partition for any future installs.

Therefore, I would suggest that you create /home partitions on your large drive and / partitions on your smaller drive. I would also set up a swap partition a bit larger than your RAM on the smaller drive.

Bear in mind that you can only make 4 primary partitions on any given drive. If you think you will end up with a lot of partitions, the set up an extended partition right from the word go. You can make at least 15, I believe, logical partitions inside that.

This machine has used up nearly 4 GB of the / partition for this 10.04 UNR install. I think my desktop has used up something over 6 GB for the / partition. If you allow 15 or so for your / partition, you should be pretty right for a while, I think.

---

### Post by cmcanulty on 2012-03-10
i would buy a few dirt cheap ram 1-3GB on ebay. 1GB of ram and even linux is slow,of course I do several things at once

---

