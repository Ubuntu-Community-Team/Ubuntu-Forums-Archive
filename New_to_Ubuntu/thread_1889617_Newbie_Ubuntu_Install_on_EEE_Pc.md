---
title: "Newbie Ubuntu Install on EEE Pc"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by Chaz46 on 2011-12-01
Hello folks,

Bought an Asus EEE pc not long back and have been wanting to install ubuntu on something for a while now, so felt that this was a good start. 

Installed ubuntu 11.10 using the wubi installer, pretty much a temporary installation just now for me to start to get my head around. 

I dont have a huge background in this so my apologises if some of the questions that I may post in future are not the brightest. The first of which is; is there really any major issues in continuing to run the installation with wubi or should I really look to install it alongside windows from a USB drive for more permanent use?

Thats about it at the moment, looking to learn as much as possible through doing this.

Cheers

---

### Post by blackbird34 on 2011-12-01
Hi and welcome
I installed direct from cd to a separate partition so i can't say from  experience. But if ssomething nasty happens to your windows partition,  it could hit ubuntu too.

As an afterthought, an idea for you to help save lots of battery if you ever install properly: the Jupiter applet [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)
[http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)
with special tools for ... the EEE.

Signed: an ex noob ;)

---

### Post by bluexrider on 2011-12-01
> **Chaz46 said:**
> Hello folks,

Bought an Asus EEE pc not long back and have been wanting to install ubuntu on something for a while now, so felt that this was a good start. 

Installed ubuntu 11.10 using the wubi installer, pretty much a temporary installation just now for me to start to get my head around. 

I dont have a huge background in this so my apologises if some of the questions that I may post in future are not the brightest. The first of which is; is there really any major issues in continuing to run the installation with wubi or should I really look to install it alongside windows from a USB drive for more permanent use?

Thats about it at the moment, looking to learn as much as possible through doing this.

Cheers

After you have given it a try and want to get serious about it then I would install it the HDD. It just works better that way. 

I have heard of the wubi breaking windows boot loader and if doing upgrades to kernels some issues there but I can't say how much human error was involved.

---

### Post by LinuxFan999 on 2011-12-01
Why keep Windows on the netbook? Also, I would recommend Xubuntu or Lubuntu for a netbook because they use less resources (memory and disk space).

---

### Post by Chaz46 on 2011-12-01
Thanks for the quick responses folks, its much appreciated. I will definitely look into doing a proper install from USB then, to be honest with you the prospect of partitioning etc. is quite scary which is what puts me off but to be honest I dont think it is something which I couldn't do.

In terms of keeping windows, its largely because it is useful for university work, creating documents etc in Offices is kind of a must. Although I probably missing something and haven't fully grasped how good libre office is...

---

### Post by Ms. Daisy on 2011-12-01
> **Chaz46 said:**
> , to be honest with you the prospect of partitioning etc. is quite scary which is what puts me off but to be honest I dont think it is something which I couldn't do
Speaking from (a failed) personal experience, if you're going to dual boot it's important to follow ALL the directions carefully.  That includes the preparation, like backing up important stuff on windows & running defrag.  But once you do it you'll find it a great experience.

---

### Post by roger_1960 on 2011-12-01
Hi

I have a dual boot on a 1011PX, very similar.

Wubi is intended for trials of ubuntu, not for long term use.  You will eventually run out of storage and be unable to increase it without installing ubuntu "properly"

Suggest before you change anything you follow the asus instructions and create an external recovery backup which will allow reinstall of factory state if needed. You can't do it after you have changed partitions (at least I couldn't!)

I deleted the 183Gb partition sda3 using gparted (present on the live CD/USB) and then installed into the empty space (this partition should be almost empty  - if not, don't proceed - both ubuntu and swap should be created as logical partitions within the space) by using the "install alongside exiting" option. All works with no problems. You should disable "fast boot" in BIOS before installing or grub might not work.

If you are not sure about this, please post back here before doing anything.

---

### Post by Chaz46 on 2011-12-02
Thanks for the replies folks, much appreciated and helps a newbie like me learn what it is that im doing!

I have backed up the OS onto a USB stick, first thing I did before I started mucking around!

In order to properly dual boot I need to make room for ubuntu, that right? So in the computer managment is it the drive I have selected here D: drive? And am I deleting or shrinking the volume in this volume?

[IMG]http://i642.photobucket.com/albums/uu144/chaz46_2009/Partitions.png[/IMG]

Sorry for what must be very basic questions for you guys, if someone has the time to give an utterly step by step guide for what I should do that would great!

Cheers Charlie

---

### Post by Ms. Daisy on 2011-12-02
No, it's much easier than that.  See this link [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)
which explains some important preparation you must do.  Really follow it.

Then follow the directions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
There are 4 steps and you just have to click on the "show me how" buttons to expand the instructions.  The installation CD (or stick) that you make will automatically partition your hard drive.

edit: I just noticed that you said you backed up your OS- excellent!  Make sure you backed up your data and you created a recovery CD, too.

---

### Post by Rubykuby on 2011-12-02
Just insert the CD/USB and follow instructions. It'll do partitioning for you according to your instructions.

---

### Post by Chaz46 on 2011-12-04
Okay so live USB created everything backed up and defragged. Am I right in saying I'm all set to go for it, I don't need to do any manual partitioning in Win 7? Thanks again for the help!

Ps I have uninstalled Wubi!

---

### Post by Ms. Daisy on 2011-12-04
Installing Ubuntu as a dual boot with Windows is as easy as following the instructions on Ubuntu's webpage [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
The process will ask you what you want to do (there are details on the link above).  Choose "install ubuntu along side windows 7". Partitioning will be taken care of by the installer.  

To answer your question: As I understand it (I could be wrong), when you partition in the Windows GUI, you are creating more windows partitions.  Ubuntu needs its own, non-windows partition.  That's why the Ubuntu installation process does it for you.  You can choose "something else" and manually configure partitions during ubuntu installation.  But there's no need if you're doing dual boot.

---

### Post by corncob on 2011-12-04
I might be missing something here but it looked like you already have four primary partitions, the maximum allowed, and its not going to give you the "install along side" option.  You can go up to that point and back off if it looks scary without writing to the disk.  Is there any content in that first partition on your list?

---

### Post by Ms. Daisy on 2011-12-04
4 partitions is the max.

---

### Post by roger_1960 on 2011-12-05
Hi again

The OPs hard drive already has 4 partitions so he will have to delete one and create a new extended partition (created by the install disk) to house ubuntu.  You can't add a fifth primary partition even if there is empty space.

---

### Post by Chaz46 on 2011-12-05
> **roger_1960 said:**
> Hi again

The OPs hard drive already has 4 partitions so he will have to delete one and create a new extended partition (created by the install disk) to house ubuntu.  You can't add a fifth primary partition even if there is empty space.

Sorry if Im being a bit slow on this one, but how would I do this? Is it the D: drive that I would use?

---

### Post by Chaz46 on 2011-12-05
Okay, so I think I am understanding this a little better now. I delete the D: drive in the picture I posted early and that should create unallocated space? From there I put the usb back in and install ubuntu into this new space? Sound about right?

Sorry again for all of the truly beginner questions, hopefully this will be one of the last of them regarding the install.

Cheers again folks!

---

### Post by Chaz46 on 2011-12-06
Went ahead and deleted the D: drive and then I was able to install ubuntu from the usb! Really impressed with it so far, thanks again for your help!

---

