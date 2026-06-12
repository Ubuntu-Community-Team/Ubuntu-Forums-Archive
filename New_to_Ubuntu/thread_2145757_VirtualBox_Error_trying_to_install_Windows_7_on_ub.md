---
title: "VirtualBox Error trying to install Windows 7 on ubuntu 13.04"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by Rekhillbill on 2013-05-16
Hello,

I used Ubuntu Software Center to download the VirtualBox.

Synaptic Package Manager was used to install the following:

Dynamic Kernel Module Support Framework
Version 2.2.0.3-1.1ubuntu2

I then deleted the Windows 7 box and ran through the process of creating a "New" virtual box again.

The following error msg appeared again:


[ATTACH=CONFIG]242646[/ATTACH]

Before I try to do anything as "root" I wanted to get a more experienced opinion of what to do next?

If I need to do something as "root", Please know that I am very inexperienced and have never tried to inter any commands as "root".

I did a search for the virtualbox.exe file and could not find it?

Any help would be appreciated.

I installed the VirtualBox on my wife's Toshiba running 13.04 and had no problems at all.

This is, also, a Toshiba laptop running 13.04.

Both laptop have had all software updates current through today.

Thanks,

---

### Post by ptn107 on 2013-05-16
This happens if you don't have dkms installed beforehand.  Make sure it's installed now:
```
sudo apt-get install dkms
```
and just run this from a terminal to clear the error:
```
sudo /etc/init.d/vboxdrv setup
```
You will never have to run this command again if dkms is present.  It makes upgrading to newer versions of Virtualbox easier by handling all the kernel stuff automatically.

---

### Post by Rekhillbill on 2013-05-16
> **ptn107 said:**
> This happens if you don't have dkms installed beforehand.  Make sure it's installed now:
```
sudo apt-get install dkms
```
and just run this from a terminal to clear the error:
```
sudo /etc/init.d/vboxdrv setup
```
You will never have to run this command again if dkms is present.  It makes upgrading to newer versions of Virtualbox easier by handling all the kernel stuff automatically.

PTN107

I ran the "first" sudo command and it executed OK.

I get the following "msg" tring to run the "second" sudo command to get rid of the Virtualbox error msg:

"...command not found..."

Also, trying to install Windows 7 again in Virtualbox brings up the two error msgs in the photo above.

Please help?

Thanks

---

### Post by Rekhillbill on 2013-05-17
OK, here's the answer for my particular Toshiba.
 

 First, it's important to say that my 13.04 is an upgrade from 12.10.  
 

 My wife's Toshiba, without the issue, was a &#8220;fresh&#8221; install of 13.04.
 

 Also, it is important to do the following before executing the sudo commands below:
 

 I  used Ubuntu Software Center to remove the Virtualbox I had previously installed.
 

 I went to the Home folder and moved the VirtualBox Vms folder to Trash.
 

 I checked &#8220;show hidden files&#8221; and moved the .VirtualBox folder to Trash.
 

 I had previously not done this and when I tried to install and create a &#8220;new&#8221; virtual box the program would not continue because it found a virtual box with the same name in the previous folders
 

 After doing the above house cleaning and executing the following three sudo commands I was able to re-install VirtualBox and continue with the installation of Windows 7 (64-bit) with out further problems.

                        
[http://xchamitha.blogspot.co.uk/2012/11/fixing-virtualbox-on-ubuntu-1210.html](http://xchamitha.blogspot.co.uk/2012/11/fixing-virtualbox-on-ubuntu-1210.html)
 

 The above is the link to the following three Terminal commands:
 

 ```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```
 

 I had already looked at my wife's packages via Synaptic Packager Manager and installed several linux-headers that were not previously installed via the upgrade, for example:
 

 linux-headers-3.8.0-21-generic  
 

 So, the terminal output shows that this &#8220;...is already the newest version. ..&#8221;
  
                        
Terminal output follows:
 

 ```
bill@bill-Satellite-L500D:~$ sudo apt-get install linux-headers-$(uname -r) 
 [sudo] password for bill:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 linux-headers-3.8.0-21-generic is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 bill@bill-Satellite-L500D:~$ sudo apt-get remove virtualbox-dkms 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package 'virtualbox-dkms' is not installed, so not removed 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 bill@bill-Satellite-L500D:~$ sudo apt-get install virtualbox-dkms 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following NEW packages will be installed: 
   virtualbox-dkms 

 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
                           
Need to get 0 B/514 kB of archives. 
 After this operation, 4,134 kB of additional disk space will be used. 
 Selecting previously unselected package virtualbox-dkms. 
 (Reading database ... 217950 files and directories currently installed.) 
 Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.2.10-dfsg-0ubuntu2_all.deb) ... 
 Setting up virtualbox-dkms (4.2.10-dfsg-0ubuntu2) ... 
 Loading new virtualbox-4.2.10 DKMS files... 
 First Installation: checking all kernels... 
 Building only for 3.8.0-21-generic 
 Building initial module for 3.8.0-21-generic 

 Done. 
                           
vboxdrv: 
 Running module version sanity check. 
  - Original module 
    - No original module exists within this kernel 
  - Installation 
    - Installing to /lib/modules/3.8.0-21-generic/updates/dkms/ 
  
 vboxnetadp.ko: 
 Running module version sanity check. 
  - Original module 
    - No original module exists within this kernel 
  - Installation 
    - Installing to /lib/modules/3.8.0-21-generic/updates/dkms/ 
                           
vboxnetflt.ko: 
 Running module version sanity check. 
  - Original module 
    - No original module exists within this kernel 
  - Installation 
    - Installing to /lib/modules/3.8.0-21-generic/updates/dkms/ 
  
 vboxpci.ko: 
 Running module version sanity check. 
  - Original module 
    - No original module exists within this kernel 
  - Installation 
    - Installing to /lib/modules/3.8.0-21-generic/updates/dkms/ 
  
                        
depmod......... 
  
 DKMS: install completed. 
  * Stopping VirtualBox kernel modules                                    [ OK ]  
  * Starting VirtualBox kernel modules                                    [ OK ]  
 bill@bill-Satellite-L500D:~$  
```
 

 I hope this helps anyone else with the same problem with VirtualBox.

Thanks,
Best,
BIll

---

### Post by gwm on 2013-05-17
You are a star! :KS:KS:KS:KS:KS
(five of them)
I installed the latest updates which changed the kernel and virtualbox broke.
I would have thought that the headers would be part of the update but an install was required to get things working again.
Thank you
:guitar:

---

### Post by Rekhillbill on 2013-05-18
Hello,

I am trying to mark this thread as "solved" but I am not finding any option to do this?

Other than edit the thread title?

Thanks,
Bill

---

### Post by ibjsb4 on 2013-05-18
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Rekhillbill on 2013-05-22
> **ibjsb4 said:**
> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

ibjs4

Thank you.

Bill

---

### Post by Rekhillbill on 2013-05-22
Also, I wanted to give an update on the Ubuntu Software Center version of VirtualBox.

I could not find a way to get the USB to work in Windows 7.

So, I removed the VirtualBox  [ with the Ubuntu Software Center's help ] and installed Version 4.2.12 r84980 from the Oracle website.

The following thread describes the issues encountered and solutions found & solutions provided with the help of others.

[http://ubuntuforums.org/showthread.php?t=2147097](http://ubuntuforums.org/showthread.php?t=2147097)

The Oracle version is working OK, including the USB.

Best,
Bill

---

