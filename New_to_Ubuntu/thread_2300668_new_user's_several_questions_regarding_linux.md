---
title: "new user's several questions regarding linux"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by ivan107 on 2015-10-27
Hello people,i am new here and it will be my first thread.
I am sorry if there is similar thread but didn't really find my type of question on forums.

I have some questions about linux ubuntu 15.10 and that is:

1.Is there any way i can force screen resolution when testing the system and installing it ? 
I mean,for example,when i boot from USB drive there are options like : try linux,install linux, etc. etc. and when i press try linux it loads but then it sets the screen resolution to 1440x900 (normal for widescreen 19" monitors BUT mine is 19" non-wide) and it gives me "Out of Range" error and i can't see anything on screen.So is there any way i can manually set my resolution with some commands and even if that's possible how can i adjust the resolution afterwards,because if the installation is successful but the screen res is 1440x900 instead of 1280x1024 which i want that would suck :D

2.I have 100GB C: Drive for Windows and i want to use it to install linux on.Last time i deleted C: drive on linux installation my D: was deleted too i want to keep my information on D: and use C: for linux storage/swap and root directories.

3.How do i install AMD Mesa drivers?I was watching a lot of youtube videos showing performance of that driver and i really liked it,that's one of the main reasons i switch to linux - because i don't like being spied and most of my games are ported on linux so yeah..

I think that pretty much is.Thanks for your time and i hope my problem with monitor is solved :D :)

---

### Post by grahammechanical on 2015-10-27
Just to clear up a few things.

The Ubuntu live/try session uses an open source video driver. In System Settings there is a utility called Screen Display. You can use that to detect the screen display. That might give you a better result for the duration of the live session.

When Linux loads it interrogates the monitor to get the optimum settings set by the manufacturer and stored in a chip that holds the Extended Display Identification Data (EDID). That is where those settings are coming from

When we install Ubuntu we get an option to install at the same time some third party software that includes not only some free but proprietary audio and video codecs but also a proprietary video driver for our video adapter. I have not tried installing a proprietary video driver from a live session. It could be possible because the OS is running in memory. You can open a terminal and run

```
ubuntu-drivers list
```

To see a list of drivers for your graphic adapter. Or

```
ubuntu-drivers devices
```

to see information about the graphic adapter and available drivers. You need to be connected to the internet. To install a proprietary driver you can go to System Settings>Software & Updates>Additional Drivers tab. You need to be connected to the internet and to wait to allow the utility to search the repositories for the drivers. In this way you might be able to test the proprietary driver in the live session. The driver will be lost when you end the live session.

Mesa is part of the open source video driver. Do not tick that box to install third party software. In the live session go to About this computer. That will open the Details page of System Settings. That will give information about the video driver being used in the live session.

[http://www.mesa3d.org/intro.html](http://www.mesa3d.org/intro.html)

When we install Ubuntu and tick the box Erase disk and install Ubuntu then for a certain all partitions on the hard drive will be lost. To select a specific partition to install Ubuntu into we choose the Something Else option. You will need two partitions for Ubuntu. One for Ubuntu the OS mounted as / and one partition mounted as swap. Linux uses a swap partition and not a swap folder.

Regards.

---

### Post by eddiefiggie on 2015-10-27
> **ivan107 said:**
> 
1.Is there any way i can force screen resolution when testing the system and installing it ? 
I mean,for example,when i boot from USB drive there are options like : try linux,install linux, etc. etc. and when i press try linux it loads but then it sets the screen resolution to 1440x900 (normal for widescreen 19" monitors BUT mine is 19" non-wide) and it gives me "Out of Range" error and i can't see anything on screen.So is there any way i can manually set my resolution with some commands and even if that's possible how can i adjust the resolution afterwards,because if the installation is successful but the screen res is 1440x900 instead of 1280x1024 which i want that would suck :D

I too am new to this.  =)  Welcome aboard.  That being said, I read recently that when "Trying" Linux (from USB for example), I believe it is using the "non-proprietary" video driver.  With the full installation you are able to easily select proprietary drivers for your graphics card if you please.  This may be why you have this resolution limitation.  I'll let someone more experienced than myself chime in.  While you wait, I figured I'd offer this.

> **ivan107 said:**
> 
2.I have 100GB C: Drive for Windows and i want to use it to install linux on.Last time i deleted C: drive on linux installation my D: was deleted too i want to keep my information on D: and use C: for linux storage/swap and root directories.

Be VERY VERY VERY careful when installing if you intend on protecting your existing partitions.  Look at this resource:  

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

```




**Back Up Your Data**

[COLOR=#333333][FONT=Ubuntu]Although this may seem obvious, it is important to [/FONT][/COLOR][back up]("https://help.ubuntu.com/community/BackupYourSystem")[COLOR=#333333][FONT=Ubuntu] your files to an external backup medium before attempting a dual-boot installation (or any other hard drive manipulation), in case your hard drive becomes corrupted during the process. External hard drives, USB flash drives, and multiple DVDs or CDs are all useful for this purpose[/FONT][/COLOR]
```

I barely understood what I was doing when I was tinkering with various partition configurations (you can do a lot of tuning here), I ended up wiping a windows partition...  =(  Be wise and back up valuable content. 


> **ivan107 said:**
> 
3.How do i install AMD Mesa drivers?I was watching a lot of youtube videos showing performance of that driver and i really liked it,that's one of the main reasons i switch to linux - because i don't like being spied and most of my games are ported on linux so yeah..

I think that pretty much is.Thanks for your time and i hope my problem with monitor is solved :D :)

I'll leave this one for the experts.

---

### Post by ivan107 on 2015-10-27
Thanks for the fast replies but it didn't quite help me because..

Well i can't see what is going on the screen to use the display settings,turns out that my monitor's EDID sets max resolution to 1440x900 which is unsupported by my monitor.Is there any way i can modify the monitor's EDID and save the settings in the monitor chip?

---

### Post by QIII on 2015-10-27
Hello!

Be careful with the AMD video driver.

If your graphics adapter is earlier than the HD 5000 series, the AMD proprietary driver does not support it.

Even if you have an HD 5000 or later, there is a problem with installing the AMD proprietary driver in 15.10 as described in [this bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888").

If you are a novice, I would recommend against attempting to update from the -proposed repository to test the fix.  Just use the default open source driver that is installed with Ubuntu, subscribe to the bug and wait for the announcement that that the fix has been moved from "Fix Committed" to "Fix Released" before installing the driver.

---

### Post by yancek on 2015-10-27
> Last time i deleted C: drive on linux installation my D: was deleted too  i want to keep my information on D: and use C: for linux storage/swap  and root directories.

Linux doesn't use the same method of identifying drives.  You will need to know which partition is C and which is D and the simplest way to identify them is by going into Computer in window to get the partition size and then using the Ubuntu install medium, open a terminal and run this command to identify partitions by size:

```
sudo parted -l
```

That's a Lower Case Letter L in the command.

---

### Post by ajgreeny on 2015-10-27
> **QIII said:**
> If you are a novice, I would recommend against attempting to update from the -proposed repository to test the fix.  Just use the default open source driver that is installed with Ubuntu, subscribe to the bug and wait for the announcement that that the fix has been moved from "Fix Committed" to "Fix Released" before installing the driver.
I would add to QIII's comments that you may actually do a lot better, and will not have a need to keep updating to new distro versions if you installed 14.04 instead of 15.10.

14.04 is supported until 2019 but 15.10 only for 9 months.

---

