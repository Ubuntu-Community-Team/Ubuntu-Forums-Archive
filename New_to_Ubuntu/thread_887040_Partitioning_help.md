---
title: "Partitioning help ?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-11
Hello,Everyone   

This is my first time here, and also using Ubuntu its ver8.04.1, I have to say I think I am going to love it. The only problem well not really a problem more like not knowing what would be the best way to Partition the 250Gb hard-drive to use Ubuntu.

Here's  how I would like to set it up.

/
Home
Swap = 1000Mb
A backup if this can be done.

Well I think you get the idea. I am just not sure how much space to use, for each Partition. Please any help at all with this. Hm now that I think of it. Were would I install ubuntu after Partitioning? more or less like windows up to me. 

Thank you

Badoxide

---

### Post by SunnyRabbiera on 2008-08-11
Well its mostly possible but the thing is that there is a limit of four partitions per hard drive, plus if you are dual booting windows matters are made more difficult.
If you dual boot with windows, I would have a root partition, a home partition and swap and get a external hard drive or something for backup.

---

### Post by Riffer on 2008-08-11
I'm not quite sure what you're asking.  Are you trying to dual boot?  Are you also trying to setup a separate partition for your home folder?

Having said that, gparted is a great partitioning tool.  Also I believe that the install will look after the swap partition.

---

### Post by Badoxide on 2008-08-11
Wow that was fast ;)

OK I have a laptop with a 250Gb HD it has 2Gb of Ram. I would like if I can not use an external hard. What I am trying to get help with is how much space would you give, for the root partition that I will install ubuntu on. Then the same question, for home partition and swap. With so much space on this HD I have no idea how to go about this.

In windows I would have no problem doing this. 

@ Both of you I thank you.

Badoxide

---

### Post by starcannon on 2008-08-11
10gb for /
2gb for swap
Remainder to /home

that should be fine.

---

### Post by ntu on 2008-08-11
Is the compter going to be running Windows as well as Ubuntu? Or is this a fresh install of Ubuntu with nothing else you want on the hard drive?

---

### Post by Badoxide on 2008-08-11
Hello.starcannon

Thanks for the information and your time.

@ ntu

Yes I will be installing only ubuntu.

Thank you

Badoxide

---

### Post by unutbu on 2008-08-11
Sometime down the road you may want to upgrade your OS to a newer version of Ubuntu. The safest way to upgrade from one linux distro to the next is to do a clean install into an unused partition. This way, you can look before you leap.

Since most Linux distros fit comfortably in 10GB, you may wish to set aside a second 10GB partition for this purpose.

If you go with this option, then also note that some BIOSs have a hard time booting (i.e. can not boot) OSs that lie too far down on very large hard drives. To minimize the chance of this being an issue for you, you may want to place the OS partitions at the front of the hard disk.

For example:
/dev/sda1   10GB   First OS
/dev/sda2   10GB   Second OS
/dev/sda3    2GB   Swap      <-- Swap must be at least as large as RAM to do hibernation
/dev/sda4   all the rest for /home

---

### Post by ntu on 2008-08-11
You can choose to partition the hdd before installation or let ubuntu choose when installing or do your own partition sizes when installing. Ie a number of options. If you find you have got the partition sizes somewhat wrong after installation you can always resize with gparted after the install.

---

### Post by Badoxide on 2008-08-11
You guys are just to fast, for me.

@ unutbu

First thanks for your time on this. Now I have some questions will I have the option to name the drives as you say. /dev/sda1 to /dev/sda4 and the first OS is the drive were I am installing ubuntu ?

Thank you

@ ntu

You have been a big help, But may I ask for just a bit more from you. Where would I find this gparted. Sorry new to all this, so I am trying not to do anything dump.

Thanks

Badoxide

---

### Post by ntu on 2008-08-11
Gparted is a partition resizing, moving, etc, program on the ubuntu cd. In my Feisty (Ubuntu 7.04) it is in System>Administration>Gnome partition editor - or in short G-part-ed.

The beauty of having a 'fresh' hard drive to 'play' about with is that if you make a mistake or 2 when installing and can't fix it, you can always just start installing again - no worries about munching up a Windows installation. And you learn a lot in this process.

I used to take out my windows hdd and put in a fresh one just to learn.

---

### Post by unutbu on 2008-08-11
When you boot from the Ubuntu LiveCD, open up a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo gparted
```

GParted can create the partitions with device names /dev/sda1 thru /dev/sda4, but it is not critical that they be named that way. They don't have to be primary partitions either -- logical partitions inside of an extended partition will work fine too.

GParted's GUI is quite easy to use. Moreover, there is also a tutorial here:
[http://gparted-livecd.tuxfamily.org/larry/generalities/gparted.htm](http://gparted-livecd.tuxfamily.org/larry/generalities/gparted.htm)
[http://gparted-livecd.tuxfamily.org/documentation.php](http://gparted-livecd.tuxfamily.org/documentation.php), including lots of helpful pictures.

---

### Post by sandysandy on 2008-08-11
URL for gparted live CD 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by Badoxide on 2008-08-12
Hey a good day to all. Well here's where I am at not sure I may have done this right. I say this because I only see one drive when I open Places Computer the only items I can see are Filesystem, and CD-RW/DVD-ROM Drive. Which is odd when I did the install I Partition it like so.

For example:
/dev/sda1 10GB First OS
/dev/sda2 10GB Second OS  <---- I tried doing this had no luck, so I just made it /tmp
/dev/sda3 2GB Swap <-- Swap must be at least as large as RAM to do hibernation
/dev/sda4 all the rest for /home

Thanks unutbu

Everything else worked out great. I just don't get why I can only see Filesystem drive, and CD-RW/DVD-ROM in Computer - File Browser, or is this the way it should be. I just need to make sure I did this the right way.

P.S

When I use this  sudo fdisk -l  

I can see all the Partitions I did during the install. 


Badoxide

---

### Post by unutbu on 2008-08-12
Badoxide, 
  It sounds like the installation succeeded. Congratulations! 

Your "Filesystem drive" or perhaps more accurately, your root '/' filesystem is actually composed of many hard drive partitions. Each partition has its own filesystem. But your operating system has the ability to "mount" the partition's filesystems at a mount point -- a subdirectory of the '/' filesystem.

The /dev/sda1 is mounted at '/'.
/dev/sda4 is mounted at /home. So when you click Places>Computer and go from the / directory to the /home directory, you are actually going from /dev/sda1 to /dev/sda4.
Similarly, /dev/sda2 has been mounted at /tmp.

/dev/sda3, the swap partition, will be used by the operating system, but its use will largely be invisible to you.

If at some future point you wish to install a second OS into /dev/sda2, you can still do so, but first you will need to edit your /etc/fstab and "comment out" the line that looks something like this:
```

# /dev/sda2
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /tmp ext3 defaults 0 2
```

You comment out the line by putting a pound symbol (#) in front of it:
```

# UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /tmp ext3 defaults 0 2
```

You would need to do this, because if you install a second OS into /dev/sda2, but your current Ubuntu OS thinks /dev/sda2 is /tmp, then Ubuntu will try to write stuff on top of /dev/sda2 thereby messing it up.

Anyway, the second OS idea is something that can wait until you get more familiar with your new system. So don't worry about it too much. It sounds like you are good to go.
Enjoy!

---

### Post by ntu on 2008-08-12
Hi Badoxide. At Places>Computer I only see partitions that I have something in, eg I do not see my swap partition. Do you have anything in sda2 and sda4?

edit: I see unutbu has told us about sda2 and sda4.

---

### Post by Badoxide on 2008-08-12
Hello.To all

I have to say at first I was not all to sure about dropping Windows. But now I don't think I'll be going back anytime soon. ;)  All of you have been a great help to me, here.

@ unutbu  and  ntu

Thanks for staying in there, and holding my hand through this. My buddy is doing the same thing the only problem he, is having playing a DVD unlike me, where I just put the disk in, and it plays the movie. :(

Thanks all

Badoxide

---

