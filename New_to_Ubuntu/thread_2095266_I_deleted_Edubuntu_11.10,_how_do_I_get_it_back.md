---
title: "I deleted Edubuntu 11.10, how do I get it back?"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Stelloria on 2012-12-16
Let me first off say that my netbook currently has no operating system  on it. I was trying to install windows 7 on my netbook and I deleted the  Edubuntu files off my harddrive during the Windows 7 setup when I had  to choose a Partition to install Windows 7 on. Now, since the windows 7  installation failed, I restarted my computer to find out that I was  greeted with  a Grub Rescue prompt. How do I retrieve my Edubuntu 11.10  back?? Do I have to type something into command to get it back? I'm new  to this, and never had experience with this. Neither with installing an  OS so I have NO IDEA why I even attempted to install windows 7. That was  stupid of me.
i tried to google for some help but everyone's talking about using some  sort of live CD, which I don't have because I didn't install Edubuntu  onto my netbook. Someone else did. Plus, there's no CD drive..

All I have is a usb drive with 8gb on it. No live CD. I want to restore  edubutu back onto my computer.  My mom can't afford to send it to a  professional to repair..
Please help me!! I'm freaking out...

It would also help if you guys give me some step-by-step guidance so I  can try to fix this issue. Try not to talk too advanced, I'm computer  illiterate. Thank you in advance!

---

### Post by mips on 2012-12-16
Did you try and install win7 to a new/spare partition? if you did not then I suspect edubuntu got overwritten and it's probably gone, hopefully I'm wrong.

---

### Post by Stelloria on 2012-12-16
> **mips said:**
> Did you try and install win7 to a new/spare partition? if you did not then I suspect edubuntu got overwritten and it's probably gone, hopefully I'm wrong.


No :[ I didn't try to install win 7 on another partition.

---

### Post by Cheesemill on 2012-12-16
It sounds like you've deleted everything from your machine.

Before you install Edubuntu is there anything that you need to try and recover or do you have all of your personal files backed up?

---

### Post by Stelloria on 2012-12-16
> **Cheesemill said:**
> It sounds like you've deleted everything from your machine.

Before you install Edubuntu is there anything that you need to try and recover or do you have all of your personal files backed up?

I didn't back up any of my personal files because I suspected that I didn't need any of it.

---

### Post by mips on 2012-12-16
> **Stelloria said:**
> No :[ I didn't try to install win 7 on another partition.

In that case it sounds like Win7 tried to install over the edubuntu install.

Do you have access to another PC? Just trying to figure out if you can create a bootable linux USB stick to boot from.

What's the make and model of the netbook?

---

### Post by Cheesemill on 2012-12-16
> **Stelloria said:**
> I didn't back up any of my personal files because I suspected that I didn't need any of it.
But is there anything important that you need before we install Edubuntu again, such as photos, schoolwork, CV's etc.

If not then we can go ahead and instruct you through installing Edubuntu. If there are files that you must try and recover then we have to do this first.

---

### Post by Stelloria on 2012-12-16
> **mips said:**
> In that case it sounds like Win7 tried to install over the edubuntu install.

Do you have access to another PC? Just trying to figure out if you can create a bootable linux USB stick to boot from.

What's the make and model of the netbook?


Yes I do access to another computer. I have a Windows XP laptop. The model of the netbook I'm using is MSI U270
Okay, I'm reading these specs straight off the computer.
CPU; AMD Dual-Core E-450
HDD; 320GB
RAM; DDRIII2GB

Does that help??

---

### Post by Stelloria on 2012-12-16
> **Cheesemill said:**
> But is there anything important that you need before we install Edubuntu again, such as photos, schoolwork, CV's etc.

If not then we can go ahead and instruct you through installing Edubuntu. If there are files that you must try and recover then we have to do this first.

No. I have any files or  anything important. I have all of my pictures saved on an online account before I damaged the operating system, so I'm good to go.

---

### Post by Cheesemill on 2012-12-16
You're going to have to install Edubuntu from scratch. Does it have to be 11.10 that you install or can you install a newer version?
I'm asking because support for 11.10 runs out in April, at this point there will be no more updates available and you will have to upgrade to the new version. If you don't mind installing 12.04 now then it will save you the hassle of having to upgrade your system in a few months time.

---

### Post by mips on 2012-12-16
Do you still have the edubuntu ISO image?

Just make a bootable usb with the image and boot from it then we can check what actually happened on the netbook.

Do you have/had any important data on the netbook? Did you have a separate /home parition on the laptop?

Maybe we can get some of your data back if required else we can just reinstall edubuntu or some other version of linux.

---

### Post by Stelloria on 2012-12-16
> **Cheesemill said:**
> You're going to have to install Edubuntu from scratch. Does it have to be 11.10 that you install or can you install a newer version?
I'm asking because support for 11.10 runs out in April, at this point there will be no more updates available and you will have to upgrade to the new version. If you don't mind installing 12.04 now then it will save you the hassle of having to upgrade your system in a few months time.

I don't mind upgrading in a few months time, but I'd just prefer 11.10 since I'm rather familiar with this version.

---

### Post by Cheesemill on 2012-12-16
OK, first you need to download the Edubuntu iso file from here:

[http://cdimage.ubuntu.com/edubuntu/releases/11.10/release/edubuntu-11.10-dvd-i386.iso](http://cdimage.ubuntu.com/edubuntu/releases/11.10/release/edubuntu-11.10-dvd-i386.iso)

When the download has finished you need to write the iso file to your USB stick. Make sure you copy everthing off the USB that you need to first as this process will erase everything on the USB stick. Then follow the instructions here:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Once you've done this you need to boot your laptop from the USB stick and follow these instructions to install Edubuntu:
[http://edubuntu.org/documentation/12.04/installation-guide](http://edubuntu.org/documentation/12.04/installation-guide)

Thoses instructions are for 12.04 but they should be exactly the same for 11.10.

---

### Post by Stelloria on 2012-12-16
> **mips said:**
> Do you still have the edubuntu ISO image?

Just make a bootable usb with the image and boot from it then we can check what actually happened on the netbook.

Do you have/had any important data on the netbook? Did you have a separate /home parition on the laptop?

Maybe we can get some of your data back if required else we can just reinstall edubuntu or some other version of linux.

No I don't have the edubuntu ISO image. :[ 
And nah, I don't have any important data on the netbook. I'm not sure if there was a separate partition on the netbook either..
Since I don't need to recover anything I guess we can get started on reinstalling it. I'd prefer Edubuntu, though.

---

### Post by mips on 2012-12-16
> **Stelloria said:**
> No I don't have the edubuntu ISO image. :[ 
And nah, I don't have any important data on the netbook. I'm not sure if there was a separate partition on the netbook either..
Since I don't need to recover anything I guess we can get started on reinstalling it. I'd prefer Edubuntu, though.

Ok in that case just download the iso image of your choice and follow Cheesemill's advice.

You really should look at a newer version though. If it's Unity you don't like then install Xubuntu and add you own educational apps.

---

### Post by Rockstarever on 2012-12-16
hi there,
look if u want to restore your edubuntu i will refer you use [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") which is the best way to boot from usb it will help u create a Edubuntu boot-able usb drive that u can just plug in and get back your normal OS back. hope this helps.

---

### Post by Stelloria on 2012-12-16
> **Cheesemill said:**
> OK, first you need to download the Edubuntu iso file from here:

[http://cdimage.ubuntu.com/edubuntu/releases/11.10/release/edubuntu-11.10-dvd-i386.iso](http://cdimage.ubuntu.com/edubuntu/releases/11.10/release/edubuntu-11.10-dvd-i386.iso)

When the download has finished you need to write the iso file to your USB stick. Make sure you copy everthing off the USB that you need to first as this process will erase everything on the USB stick. Then follow the instructions here:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Once you've done this you need to boot your laptop from the USB stick and follow these instructions to install Edubuntu:
[http://edubuntu.org/documentation/12.04/installation-guide](http://edubuntu.org/documentation/12.04/installation-guide)

Thoses instructions are for 12.04 but they should be exactly the same for 11.10.

Thank you so much for this info. Although, when I got to the last stage of the installation my computer screen just randomly.. went on a black screen during installation . I don't know what to do now..

---

