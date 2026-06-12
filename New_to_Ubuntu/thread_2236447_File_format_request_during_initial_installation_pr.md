---
title: "File format request during initial installation process"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by Roxy_Robinson on 2014-07-26
First, I know absolutely nothing about Linux and how it operates, or any terms associated with its operation. I have been using computers since before the original IBM PC's, and lots of folks will come to me with questions about that part of the computer world - when they need help. I have a Dell Dimension E310 with Win XP and 3 gigs of ram. It is a nice running machine - has been very stable ever since I bought it new. I want to set it up for my grandson, but since XP is no longer supported, want to dual boot with Ubuntu - using Ubuntu for internet access. This would keep XP off the internet; safe and secure, and still running the programs he wants to run.
So, since every where I read Ubuntu is the best choice, especially for ease of installation. I purchased 5 of the Ubuntu 12.04 CD's. I've read all of the installation instructions I can find here but have not found anything that relates to my question. When I get to the point where Ubuntu is going to format its partition, it pops up a window asking me to choose from about 10-15 different file formats to do the formatting with. I have no earthly idea what to choose!!!
This system also has a GeForce 8400 video card - I have recently found and downloaded a fairly large upgrade file for the card but have not installed it yet.
Would appreciate some guidance on how to proceed, and some help on where I can find some basic "training" on the operation of the system once its installed.
Thanks in advance!   Roxy

---

### Post by Tristan_Williams on 2014-07-26
Go with Ext4

Also, a good beginner guide can be found here:
[http://itsfoss.com/ubuntu-12-04-manual/](http://itsfoss.com/ubuntu-12-04-manual/)

As a side note, you didn't need to purchase any of those CDs. You can burn LiveCDs and LiveUSBs for Ubuntu for free

---

### Post by kira-yamato-2008 on 2014-07-26
A second side note: You can also download Lubuntu, Xubuntu, and other flavors of Linux for free and burn LiveCDs, LiveDVDs, and LiveUSBs with them too. On an older XP machine like the one you're describing Lubuntu or Xubuntu might be better choices just because they're meant for older systems/Systems with lower system specs. Basically you'll get a snappier over all performance with a lighter weight distro.

---

### Post by Tristan_Williams on 2014-07-27
> **kira-yamato-2008 said:**
> A second side note: You can also download Lubuntu, Xubuntu, and other flavors of Linux for free and burn LiveCDs, LiveDVDs, and LiveUSBs with them too. On an older XP machine like the one you're describing Lubuntu or Xubuntu might be better choices just because they're meant for older systems/Systems with lower system specs. Basically you'll get a snappier over all performance with a lighter weight distro.

Yes, Xubuntu and Lubuntu are also much more similar to Windows, so you will have less of a learning curve than with Ubuntu

---

### Post by Roxy_Robinson on 2014-07-27
I guess the main reason I chose Ubuntu 12.04 was because of its long term support status. Do the other discos of Linux also offer LTS? If the manual mentioned above is halfway decent I probably wouldn't have too much trouble with Ubuntu. I guess my only other real concern was the GeForce video card - seems like I've seen some posts about problems with them???

---

### Post by ibjsb4 on 2014-07-27
> Do the other discos of Linux also offer LTS?

Ubuntu LTS has five years of support.

Lu and Xu LTS has three.

---

### Post by grahammechanical on 2014-07-27
Ubuntu has a default video driver that is open source. For Nvidia cards it is called Nouveau. When we install we get an option to tick a box called Install Third Party Software. If we tick that box then the installer will install a proprietary video driver, which in your case would be by Nvidia. If we don't tick the box then we will get Nouveau and we can install those useful video and audio codecs through the Ubuntu Software Centre by searching for Ubuntu Restricted Extras.

Regards.

---

### Post by buzzingrobot on 2014-07-27
The current Ubuntu release, 14.04, is an LTS.

Support time for Linux distributions other than Ubuntu varies.  On one extreme there are so-called rolling distributions that roll out updates as they are released for users by developers.  On the other extreme are distributions like Red Hat Enterprise 
Linux and its binary clones (CentOS, for example) that are more or less locked down as far as features go after the initial release, but receive security and kernel patches and bug fixes for 10 years.

---

### Post by Roxy_Robinson on 2014-07-27
So you are saying that I SHOULD NOT tick the box called "install Third Party Software"? And does Nouveau automatically get installed then, and do I have to go find it?

---

### Post by kira-yamato-2008 on 2014-07-27
> **Roxy_Robinson said:**
> So you are saying that I SHOULD NOT tick the box called "install Third Party Software"? And does Nouveau automatically get installed then, and do I have to go find it?

Nouveau is automatically installed, no worries there. It is however a bit on the limited site. If you plan on running games on the system you're gonna want a driver that can handle it. If no gaming just leave the Nouveau driver and everything should run well enough.

---

### Post by yancek on 2014-07-27
If you are going to use Ubuntu 12.04, after you have installed and booted, go to the System Settings icon in the left panel (gear/wrench icon) and open it.  Under hardware in that window is an icon for Additional Drivers.  Click that and wait for it to finish and it will give you options including a recommended one.  Click the radio button for it if you want it and it will install.

---

### Post by tagy011 on 2014-07-28
[COLOR=#333333][FONT=Ubuntu]Best choice for a mix of stability and advanced journaling  is XFS file system . Ext4 journaling is choice for new installations where super-standard isn't necessary which i recommend you to use being a beginner  . [/FONT][/COLOR][FONT=sans-serif][COLOR=#000000]In modern distros such as Ubuntu ,ext4 is the default file system ,  and you don't need to modify your system to run ext4 , chooce that and installation is automated , it will partition and format itself . On some occasions , that i have seen , installing ubuntu as dual boot ,it might ask you to set the size of swap partition (necessary for linux) since the drive has NTFS (win. partition) , that size needs to be at least double the amount of RAM you have . Steps are pretty self-explanatory during installation .  [/COLOR][/FONT]

---

### Post by ibjsb4 on 2014-07-28
> **tagy011 said:**
> [FONT=sans-serif][COLOR=#000000]it might ask you to set the size of swap partition (necessary for linux) since the drive has NTFS (win. partition) , that size needs to be at least double the amount of RAM you have [/COLOR][/FONT]
 this "recommendation" dates back from a time when physical RAM was very  expensive and most Unix systems ran with many processes in swap space -  a situation that hardly applies in most situations these days, but  ancient Unix/Linux myths like this "recommendation" tend to survive well  past their "use by" dates

[https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F](https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F)

---

### Post by oldrocker99 on 2014-07-28
Oh, by all means, check "Install third party software." It's there for your convenience, not to confuse you, and you'll be able to play most media files as soon as you reboot.

---

### Post by tagy011 on 2014-08-01
You are right , and not to argue with you i did say on some occasions . Those with 2 GB of RAM and less  , with less then 200 GB HDD should have equal amount of space in swap , with more then 250 GB HDD  , double the swap as its only downside is HDD space , having plentiful space in HDD there is absolutely nothing wrong with having double the swap size , and is beneficial when using hibernate mode , i do .  [COLOR=#333333][FONT=Arial]Linux divides its physical RAM (random access memory) into chucks of memory called pages. Swapping is the process whereby a page of memory is copied to the preconfigured space on the hard disk, called swap space, to free up that page of memory. The combined sizes of the physical memory and the swap space is the amount of virtual memory available.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Swapping is necessary for two important reasons. First, when the system requires more memory than is physically available, the kernel swaps out less used pages and gives memory to the current application (process) that needs the memory immediately. Second, a significant number of the pages used by an application during its startup phase may only be used for initialization and then never used again. The system can swap out those pages and free the memory for other applications or even for the disk cache . Swap is absolutely necessary .[/FONT][/COLOR][COLOR=#333333][FONT=Arial]It is possible to run a Linux system without a swap space, and the system will run well if you have a very  large amount of memory  ,  but if you run out of physical memory then the system will crash, as it has nothing else it can do, so it is advisable to have a swap space, especially since disk space is relatively cheap. Since this guy has 3 GB of RAM if i was him i would most definitely have that swap partition at 6 GB .[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-08-01
> **Roxy_Robinson said:**
> I guess the main reason I chose Ubuntu 12.04 was because of its long term support status.

This is common among new users - the understandable desire to minimize the unknown (though very easy) tasks of installation, upgrade, and/or reinstallation.

It's a good choice, but it's often made for the wrong reasons.

In Windows, an OS upgrade is opaque, highly disruptive, and occasionally expensive. No wonder new users want to avoid them.

But in Ubuntu (and other Linux distros), an OS upgrade is a normal part of business. They are transparent and try to be minimally disruptive. The OS is *designed* to be upgraded -even reinstalled- easily.

The difficulty and risk to install Ubuntu and XP side-by-side is entirely caused by Windows (you *paid them* for that feature!). Once you have a Linux distro installed, upgrades and different partitions and other mucking about are easy and reasonably safe.

An LTS is not more stable or safer. That's not it's purpose. All it does is lock you into older versions of software for the next few years; keeps you in the old XP upgrades-should-be-avoided mindset.

---

