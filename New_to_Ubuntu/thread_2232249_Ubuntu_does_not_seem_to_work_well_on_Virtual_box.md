---
title: "Ubuntu does not seem to work well on Virtual box"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by jon80 on 2014-06-30
It turns out that Ubuntu on Virtual Box
a) is very slow to run notwithstanding that I have deducated around 1Gb of RAM to the virtual machine.
b) having installed kde-plasma-desktop I cannot find a way to load the desktop, although I am trying a few more help files are there are many options.
c) building dependencies (apt-get) takes ages i.e. more than 6 hours to install a program and this is not acceptable on a laptop which runs a 64 bit processor and 6Gb of RAM hosting a virtual machine with 1Gb of RAM.
d) running startx is unsuccessful as xinit finally reads: unable to connect to x server: resources temporarily unavailable.  I cannot quite understand why and this seems to be a known issue as per warning at [http://ubuntuforums.org/showthread.php?t=1586633](http://ubuntuforums.org/showthread.php?t=1586633).

This seems to be a problem with Virtual Box, however, there might be underlying issues with Ubuntu itself as well and I cannot quite find a way to post content from the virtual machine itself, as I cannot copy and paste directly from the virtual machine but I would need to have some sort of ftp service which cannot be run simultaneously while other programs are running, and, given the performance issues I do not wish to run them in the background, but prefer verbose output.  Hardware specs of laptop at [https://onedrive.live.com/?cid=B712073B3513EB8E&id=B712073B3513EB8E%217145](https://onedrive.live.com/?cid=B712073B3513EB8E&id=B712073B3513EB8E%217145).

I have another computer with Virtual Box, and, still I have encountered these slowness issues with Ubuntu and also with other operating systems.  Downloading the latest version of Virtual Box only resulted in an installation problem so I had to revert to Virtual Box 4.3.10r93012, as the installer did seem to create a shortcut on my windows-based guest operating system and an application executable within the Program Files directly making the installation totally unusable.  The issue has been reported separately to the Oracle forums in hope for a newer version that works.

Oracle Virtual Box at [https://www.virtualbox.org/](https://www.virtualbox.org/).

---

### Post by The Cog on 2014-06-30
There is something badly wrong if apt-get takes 6 hours to do anything. I stand by my suggestions below, but there may well be something else horribly wrong. All I can think of is very slow disk access - IO errors or heavy paging perhaps?

Firstly, I would suggest giving it 2G of RAM. 

Secondly, I suggest avoiding Ubuntu in a VM - I don't think VirtualBox provides the kind of 3d acceleration that the Ubuntu desktop needs. I really don't know about KDE - it's been a few years since I used KDE and I'm not up to date on its requirements. 

Thirdly, make sure Ubuntu has at least 2 virtual CPUs. That makes a big difference. You may have to enable virtualisation support in the BIOS before you can do that. And actually, it may be the virtualisation support rather than the second CPU that made the big difference in my case.

Fourthly, there are VirtualBox guest additions available for *buntu which improve performance:
```
sudo apt-get install virtualbox-guest-utils virtualbox-guest-x11
```

I use Xubuntu inside VirtualBox on windows7 at work, and don't see a performance problem. I give it 2G RAM and 2 CPUs

---

### Post by QIII on 2014-06-30
Hello!

I virtualize both Ubuntu and Kubuntu during development and have no problems at all.

I suspect a bum install, but let me mull over your initial post a bit more.

---

### Post by ajgreeny on 2014-06-30
Installing Guest-additions will give you the option of bi-directional copy/paste to clipboard; I use it all the time, as I need a WinXP VM to update my TomTom satnav regularly.  Guest additions also enables USB in the VMs and offers you shared folders between your host and guest.

I agree with the above posters that with 6GB ram machine it is worth giving the VMs 2GB ram, and at least two of the cpu cores; I give mine all 4 cores and, incidentally, using Intel HD4000 graphics in the host I have no problem running unity desktop, along with all the default compiz plugins that it needs.  It updates and downloads anything just as fast as the host machine does (20Mb/s), so I feel that there issomething very wrong with either your setup of VB or your VMs.

PS:
Which version of VB do you use?  I am using version 4.3.12 from Oracle's  VirtualBox repository, along with the guest additions which are downloaded direct from there as well.
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

