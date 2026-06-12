---
title: "Wifi. Possible to reinstall only drivers from CD?"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by MyTinFoilHat on 2013-02-17
When I installed Ubuntu, everything simply worked: wired connection, wifi, display, keyboard, etc. - it all worked.

Currently, I'm having issues with my wifi driver. I can't see or gain access to wifi. I know the card works. It worked until 2 days ago. I've explained this issue in another post in the appropriate forum. Here: [http://ubuntuforums.org/showthread.php?p=12512965#post12512965](http://ubuntuforums.org/showthread.php?p=12512965#post12512965)

I've checked out several posts similar to mine (before posting my question), but can't seem to get things to work right. Either I'm misunderstanding something, missing a step, or am simply not "getting it". I'm feeling quite stupid right now, actually and my frustration may also be getting in the way of understanding the problem and the solution. In any case, the problem still persists and I'm wondering if someone, anyone can help me out.

My thought is this: Since I know that the wifi will work when Ubuntu is installed, perhaps I could reinstall Ubuntu to get back those drivers, settings, etc that did work. Problem is, I don't want to lose everything currently on my laptop. So, now I have a question about reinstalling Ubuntu or only those drivers I need that I know work.

How do I reinstall Ubuntu (specifically those "default" settings, drivers WITHOUT overwriting or removing any of the apps and customization I've taken great pains to setup on my laptop? I merely want those "default" drivers (that worked) to be reinstalled. Is there a way?

Thank you!

---

### Post by Bashing-om on 2013-02-17
MyTinFoilHat;

Wireless issues are not in my sphere of knowledge, however in response to your query:
Drivers are replaceable in ubuntu. Might I suggest not to be too hasty in blaming a driver  (often the case, updates can break a "proprietary" driver). Take a deep breath, relax for a moment, and start all over from the beginning in the process to isolate the fault . Have a read in the tutorial, follow the guidance, and let us all see where you are at then. Sound good ?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)
[INDENT]will'n to help

[/INDENT]

---

### Post by DuckHook on 2013-02-17
There has been an outbreak of recent threads dealing with suddenly broken WIFI. I suspect that a bad recent update may be the cause. If so, then a reinstall won't help because it will get you working only until you update, which most will want to do almost immediately.

Have looked at your recent thread (don't be surprised if Forum Admins admonish you for double posting). In addition to that info, please post output of the following:```
ifconfig
iwconfig
lsmod | egrep -i 'wl|ssb|b43|brcm|bcma'
cat /etc/modules
grep blacklist /etc/modprobe.d/blacklist.conf
```In your case, bluetooth tethering may be the cause or it may be coincidental. To cover off this possibility, go to Network Manager and see if WIFI is on. If so, what does Connection Information show?

Will know more once requested output is posted.

---

### Post by MyTinFoilHat on 2013-02-17
> **Bashing-om said:**
> MyTinFoilHat;

Wireless issues are not in my sphere of knowledge, however in response to your query:
Drivers are replaceable in ubuntu. Might I suggest not to be too hasty in blaming a driver  (often the case, updates can break a "proprietary" driver). Take a deep breath, relax for a moment, and start all over from the beginning in the process to isolate the fault . Have a read in the tutorial, follow the guidance, and let us all see where you are at then. Sound good ?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)
[INDENT]will'n to help

[/INDENT]

Thank you very much. I appreciate your time. I'm going to read that momentarily and will post back here.

---

### Post by MyTinFoilHat on 2013-02-17
> **DuckHook said:**
> There has been an outbreak of recent threads dealing with suddenly broken WIFI. I suspect that a bad recent update may be the cause. If so, then a reinstall won't help because it will get you working only until you update, which most will want to do almost immediately.

Have looked at your recent thread (don't be surprised if Forum Admins admonish you for double posting). In addition to that info, please post output of the following:```
ifconfig
iwconfig
lsmod | egrep -i 'wl|ssb|b43|brcm|bcma'
cat /etc/modules
grep blacklist /etc/modprobe.d/blacklist.conf
```In your case, bluetooth tethering may be the cause or it may be coincidental. To cover off this possibility, go to Network Manager and see if WIFI is on. If so, what does Connection Information show?

Will know more once requested output is posted.

Thank you. Yes, hopefully the bluetooth thing was coincidence, but I won't be taking tinkering with that again anytime soon.

I've checked the Network and Network Connections. I'm wired on Auto Ethernet via Interface: Ethernet (eth0), Driver: sky2, Speed: 100Mb/s

As for the other stuff, here's what I see:
> 
ifconfig


```

eth0      Link encap:Ethernet  HWaddr: [[REDACTED by OP]  
          inet addr:[REDACTED by OP]  Bcast:[REDACTED by OP] Mask:255.255.255.0
          inet6 addr: [REDACTED by OP] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4005296 (4.0 MB)  TX bytes:546379 (546.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17941 (17.9 KB)  TX bytes:17941 (17.9 KB)

```

> 
iwconfig


```

eth0      no wireless extensions.

lo        no wireless extensions.

```

> 
lsmod | egrep -i 'wl|ssb|b43|brcm|bcma'

Was this supposed to have a human readable output for me to share?


> 
cat /etc/modules


```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

```

> 
grep blacklist /etc/modprobe.d/blacklist.conf


```

blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

```

I see that entry blacklist bcm43xx. I'm guessing that's something to do with it...

ADDITIONAL:

I've also popped into the Software Sources/Additional Drivers and can see that I have 

> 
Broadcom Corporation: BCM4321 802.11a/b/g/n. This device is using an alternative driver. Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)


---

### Post by DuckHook on 2013-02-17
Something seems to have nuked your wireless driver. Don't know if it was bluetooth episode or update. This is actually rather good news. Would much rather deal with missing driver than a balky driver installed but not cooperating.

To answer your questions:

1. *lsmod* would not return anything because you have no module loaded.

2. blacklisting *bcm43xx* is okay provided that another module takes its place. You don't want two modules competing for the same WIFI chip. When the original working module was loaded, *bcm43xx* was blacklisted, which is expected behaviour.

Okay. Let's try fixing it. Please follow instructions [here]("http://ubuntuforums.org/showthread.php?p=12497923#post12497923"). Solution was provided to same problem a few days ago, so no point posting twice.

Post back to let us know how it goes.

---

### Post by MyTinFoilHat on 2013-02-17
> **DuckHook said:**
> Something seems to have nuked your wireless driver. Don't know if it was bluetooth episode or update. This is actually rather good news. Would much rather deal with missing driver than a balky driver installed but not cooperating.

To answer your questions:

1. *lsmod* would not return anything because you have no module loaded.

2. blacklisting *bcm43xx* is okay provided that another module takes its place. You don't want two modules competing for the same WIFI chip. When the original working module was loaded, *bcm43xx* was blacklisted, which is expected behaviour.

Okay. Let's try fixing it. Please follow instructions [here]("http://ubuntuforums.org/showthread.php?p=12497923#post12497923"). Solution was provided to same problem a few days ago, so no point posting twice.

Post back to let us know how it goes.


Thank you very much! I appreciate your letting me know about lsmod. It helps me to understand better.

I've started the steps you outlined in the other post and am concerned I may have hit a small bump in the road. 

I made it as far as Step 7...
> 

Code:

sudo apt-get install bcmwl-kernel-source

to install the proper driver.


This is how that went...

```

user1@compooter:~$ lsmod | egrep -i 'b43|ssb|wl|bcrm|bcma'
user1@compooter:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for user1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  module-assistant
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 3,609 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 161996 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

```

I believe the module-assistant mentioned at the beginning may have been the result of a previous attempt to fix...

So, I got the new bcmwl-kernel-source, but the build (as you can see) was skipped. Is that the "bad thing" I'm guessing it to be?
There is, of course, all the ERROR messages, too. 

I even went ahead and did the modprobe wl - which gave me a ```
 FATAL: Module wl not found. 
```

I'm not sure what to do next. I'm also trying to think - and to see what you see to help me understand. So, if I'm understanding this process so far, we've removed the bcmwl-kernel-source and rebooted. We reinstalled it, but there are problems - specifically with modules in /proc/modules... things missing... and wl is nowhere to be found (on my machine). Have I got that right?

Thanks for your help and patience. I deeply appreciate it.

---

### Post by DuckHook on 2013-02-17
You instincts are good. It's just a small bump. You are missing the Linux headers that system needs in order to do the build. Do:```
sudo apt-get update
``````
sudo apt-get install linux-headers-generic
```Then do the prior process and you should be able to build and install.

BTW, this missing critical stuff makes me think that the culprit was initially a bad update.

---

### Post by DuckHook on 2013-02-17
To answer your larger questions:

The process involves unloading all modules from memory, completely deleting all previous module packages in case either they or their config files are corrupted, downloading the newest module package from the repositories, building and installing it. Some commands were checks to make sure that we had in fact squished all of the little buggers.

The module package is called *bcmwl-kernel-source*, but this is not what the module itself is called. The package builds the actual module, and in your case, the module you want is simply called *wl*. The others can be ignored. Ubuntu needs to know what build resources to use in building the module, and it does this by referencing *linux-headers-generic*. If your *linux-headers-generic* is missing or is mismatched to your kernel, then it won't know what resources to use, and *bcmwl-kernel-source* can't build the module. However, the script for building the module will continue to run merrily along, ignoring the fact that no module was built, until the end, where it suddenly realizes that it has no module to attach to the kernel. This is the "Fatal: Module wl not found".

The broadcom chipset family is an infamous one in all Linux distros. Its drivers must use proprietary blobs and therefore cannot be included into the kernel. The solution that distro developers came up with was to append it to the kernel as a driver module. This way, the base kernel remains untainted. This is why every broadcom WIFI chipset requires some extraneous driver. In some of my older laptops, it's *b43* and *b43legacy*, which require an even more convoluted installation routine that involves extracting firmware out of the chipset itself and building it into the blob. Thank your stars that you have a newer chip that doesn't require such additional nonsense.

If this doesn't work then I've misread the situation and will have to try other things. Let us know how it goes.

---

### Post by MyTinFoilHat on 2013-02-17
> **DuckHook said:**
> You instincts are good. It's just a small bump. You are missing the Linux headers that system needs in order to do the build. Do:```
sudo apt-get update
``````
sudo apt-get install linux-headers-generic
```Then do the prior process and you should be able to build and install.

BTW, this missing critical stuff makes me think that the culprit was initially a bad update.

Thanks. I'm honestly trying to get a full grip on how this system works, so I'm motivated to understand and not just follow cli instructions.

You've just provided me with yet another bridge to understanding, as it relates to the problem.

This just got interesting as you'll see below:

While processing this:

> 
sudo apt-get update


I got this:
```

[sudo] password for user1: 
Ign http://extras.ubuntu.com quantal InRelease
Ign http://ppa.launchpad.net quantal InRelease
Ign http://archive.ubuntu.com quantal InRelease
Hit http://extras.ubuntu.com quantal Release.gpg
Hit http://ppa.launchpad.net quantal Release.gpg
Hit http://extras.ubuntu.com quantal Release   
Ign http://archive.ubuntu.com quantal-updates InRelease
Hit http://ppa.launchpad.net quantal Release                          
Ign http://archive.ubuntu.com quantal-backports InRelease             
Hit http://extras.ubuntu.com quantal/main Sources                     
Ign http://archive.ubuntu.com quantal-security InRelease
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://extras.ubuntu.com quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal Release.gpg
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://extras.ubuntu.com quantal/main i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates Release.gpg
Get:1 http://archive.ubuntu.com quantal-backports Release.gpg [933 B]
Hit http://archive.ubuntu.com quantal-security Release.gpg                     
Hit http://archive.ubuntu.com quantal Release                        
Hit http://archive.ubuntu.com quantal-updates Release                          
Get:2 http://archive.ubuntu.com quantal-backports Release [49.6 kB]            
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US              
Hit http://archive.ubuntu.com quantal-security Release
Ign http://ppa.launchpad.net quantal/main Translation-en               
Hit http://archive.ubuntu.com quantal/main Sources
Hit http://archive.ubuntu.com quantal/restricted Sources
Hit http://archive.ubuntu.com quantal/universe Sources
Hit http://archive.ubuntu.com quantal/multiverse Sources
Hit http://archive.ubuntu.com quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal/universe amd64 Packages
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal/restricted i386 Packages
Hit http://archive.ubuntu.com quantal/universe i386 Packages
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal/main Translation-en
Hit http://archive.ubuntu.com quantal/multiverse Translation-en
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-en
Hit http://archive.ubuntu.com quantal-updates/main Sources
Hit http://archive.ubuntu.com quantal-updates/restricted Sources
Hit http://archive.ubuntu.com quantal-updates/universe Sources
Hit http://archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-updates/universe i386 Packages           
Hit http://archive.ubuntu.com quantal-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com quantal-updates/main Translation-en              
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en        
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en          
Get:3 http://archive.ubuntu.com quantal-backports/main Sources [14 B]          
Get:4 http://archive.ubuntu.com quantal-backports/restricted Sources [14 B]    
Get:5 http://archive.ubuntu.com quantal-backports/universe Sources [6,783 B]   
Get:6 http://archive.ubuntu.com quantal-backports/multiverse Sources [781 B]   
Get:7 http://archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]   
Get:8 http://archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:9 http://archive.ubuntu.com quantal-backports/universe amd64 Packages [7,393 B]
Get:10 http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages [1,118 B]
Get:11 http://archive.ubuntu.com quantal-backports/main i386 Packages [14 B]   
Get:12 http://archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Get:13 http://archive.ubuntu.com quantal-backports/universe i386 Packages [8,141 B]
Get:14 http://archive.ubuntu.com quantal-backports/multiverse i386 Packages [1,118 B]
Hit http://archive.ubuntu.com quantal-backports/main Translation-en            
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en      
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en        
Hit http://archive.ubuntu.com quantal-security/main Sources                    
Hit http://archive.ubuntu.com quantal-security/restricted Sources              
Hit http://archive.ubuntu.com quantal-security/universe Sources                
Hit http://archive.ubuntu.com quantal-security/multiverse Sources              
Hit http://archive.ubuntu.com quantal-security/main amd64 Packages             
Hit http://archive.ubuntu.com quantal-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com quantal-security/universe amd64 Packages         
Hit http://archive.ubuntu.com quantal-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com quantal-security/main i386 Packages              
Hit http://archive.ubuntu.com quantal-security/restricted i386 Packages        
Hit http://archive.ubuntu.com quantal-security/universe i386 Packages          
Hit http://archive.ubuntu.com quantal-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com quantal-security/main Translation-en             
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en       
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en       
Hit http://archive.ubuntu.com quantal-security/universe Translation-en         
Ign http://archive.ubuntu.com quantal/main Translation-en_US                   
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US             
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal/universe Translation-en_US               
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US
Fetched 76.0 kB in 19s (3,948 B/s)
Reading package lists... Done

```

Update doesn't seem to out of the ordinary with what I've seen before...

> 
sudo apt-get install linux-headers-generic


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  module-assistant
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.1 MB of archives.
After this operation, 70.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ quantal-updates/main linux-headers-3.5.0-23 all 3.5.0-23.35 [12.1 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ quantal-updates/main linux-headers-3.5.0-23-generic amd64 3.5.0-23.35 [963 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ quantal-updates/main linux-headers-generic amd64 3.5.0.23.29 [2,508 B]
Fetched 13.1 MB in 7s (1,684 kB/s)                                             
Selecting previously unselected package linux-headers-3.5.0-23.
(Reading database ... 162051 files and directories currently installed.)
Unpacking linux-headers-3.5.0-23 (from .../linux-headers-3.5.0-23_3.5.0-23.35_all.deb) ...
Selecting previously unselected package linux-headers-3.5.0-23-generic.

```

Should I go ahead and autoremove that module-assistant?
And, as I pondered this thought...

BAM!

> 
Crash report
Sorry, but a problem occurred while installing software.
Package: broadcom-sta-dkms

Details:
Package > broadcom-sta-dkms 5.100.82.112-7
ProblemType > Package
Title > broadcom-sta-dkms 5.100.82.112-7:broadcom-sta kernel module failed to build
ApportVersion > 2.6.1-0ubuntu10
Architecture > amd64
DKMSBuildLog > ##long entry here. can't copy & paste. if you want to see, I can transcribe, but it will take time.
DKMSKernelVersion > 3.5.0-23-generic
Date > ##date and time processed
Dependencies > ##massive list of dependencies with version numbers... again, can transcribe if need be, but will take time.
DistroRelease > Ubuntu 12.10
DuplicateSignature > ##extensive text here. DKMS make.log for broadcom-sta...
InstallationDate > Installed on 2013-02-16 (2 days ago)
InstallationMedia > Ubuntu 12.10 "Quantal Quetzal" - Release amd64 (20121017.5)
MarkForUpload > True
PackageArchitecture > all
PackageVersion > 5.100.82.112-7
ProcVersionSignature > Ubuntu 3.5.0-23.35-generic 3.5.7.2
SourcePackage > broadcom-sta
Tags > quantal
Uname > Linux 3.5.0-23-generic x86_64
UpgradeStatus > No upgrade log present (probably fresh install)


Trying to understand this... In short, there's something about the package. Missing dependencies? I see the Crash Report also mentions my LiveCD... (at least it looks like it). Should I remove this from the resources and (maybe) try all this again?

---

### Post by DuckHook on 2013-02-17
...hhhmmm. Seems to be more issues here than I first assumed. You mentioned that you tried previous fix attempts. Please describe in as much detail as you can remember. Also, using your mouse, it is possible to select output of terminal and paste into gedit. Not quite sure why you need to transcribe. Since we are dealing with missing dependencies, what those dependencies actually are now factor into equation. Would not want to put you to the task of transcribing though. However, don't see why that would be necessary. If transcribing is the only option, then it may be better to open your dpkg.log and look it through. Since all activity is dated, you can select and copy starting from the end. dpkg.log can be massive, so I have not asked you to attach it. Will have to rely on your judgment. Can be found at /var/log/dpkg.log and can be viewed either with your log viewer from dash, or:```
gedit /var/log/dpkg.log
```As for module-assistant, this is a developer's helper tool to build modules and is not needed with bcmwl-kernel-source unless we try to build from the dpkg itself. No need to get rid of it yet, because it is doing no harm. We may need it later. It does raise the question of why you initially installed it and what other changes you made to your system though.

This will likely not hurt you, but on the even remote chance that things get hairy, now would be a good time to back up all critical data and then check your backup for integrity.

btw, broadcom-sta-dkms is the actual binary which builds wl, so its blowing up is significant.

Am tempted to apt-get headers with -f, but don't do that yet. Let's see what dpkg.log reveals first.

<edit>
forgot most important question of all... did linux-headers-generic finish installing?
</edit>

---

### Post by MyTinFoilHat on 2013-02-18
> **DuckHook said:**
> To answer your larger questions:

The process involves unloading all modules from memory, completely deleting all previous module packages in case either they or their config files are corrupted, downloading the newest module package from the repositories, building and installing it. Some commands were checks to make sure that we had in fact squished all of the little buggers.

The module package is called *bcmwl-kernel-source*, but this is not what the module itself is called. The package builds the actual module, and in your case, the module you want is simply called *wl*. The others can be ignored. ...

With the way you've explained this, the whole thing makes more sense. If I'm understanding, we effectively need to get wl and attach it to the kernel so that it can properly build the right (driver?) for my hw? (Am I close?) LOL

I see you've posted some additional questions and steps in another post. I will have to check it out and respond after work. I don't mind playing tag if you don't. 

I'll be sure to post whatever I can that can help you to help me get this resolved. I remember following quite a few posts related to making changes in Synaptic and installing/removing firmware-b43-?? and a few other things (forgive. again, not home, can't check and see)... The bits about offering to transcribe were in reference to the Crash dialogue box (I didn't have an option to click, select, copy, paste so I was willing to type it all for you if need be). -And, yes, I believe linux-headers-generic did finish, sans wl of course...

Again, I really appreciate everything so far. I can feel we're not too far from a happy ending to this story.  ;)

---

### Post by DuckHook on 2013-02-18
Ahh...

You've been led astray by my geek-speak. Let me try to clarify because it is not as complicated as you think:

A "module" *is* a driver. In Linux-space, they are synonymous terms. So, the command *lsmod*="list modules"="list drivers", *rmmod*="remove module"="remove driver", *insmod*="insert module"="insert driver", and so forth. There are times when guys like me muddy the waters by speaking of a "driver module" but this is just loose terminology that is indulging in a redundancy. The word "driver" can be substituted for "module" on practically all occasions.

A further simplifying principle: Unlike Windows, most drivers are already compiled into the Linux kernel itself. If you buy or assemble a completely Linux-compatible box (which is not that hard to do), you don't need to install any further drivers beyond the kernel that comes with Ubuntu. It will recognize every component automagically and without further fiddling. Some of these drivers were contributed to the community by the component manufacturers, but most were reverse-engineered by the Linux community. The important thing about all of them is that they are licensed under the GPL or acceptable variants. Linus and gang are rather picky about making it so (as they should be) and will not accept any code that hazards even a remote possibility of "tainting" the kernel.

For various reasons, some broadcom chips need proprietary binary code ("blobs") in their drivers. So Linus and gang have basically washed their hands of the whole family of broadcom chips. In response, some enterprising sorts have developed usable drivers independently of the kernel and which can be appended to it using the module subsystem in the Linux OS. Since such drivers/modules act as kernel extensions, they do taint the kernel, so it becomes a user's choice whether they wish to use these drivers. This policy preserves the integrity of the base kernel, and downloads the decision over tainting the kernel to each user (again, as it should be). The driver you are trying to build is called *wl*.

In your case, *bcmwl-kernel-source* is not a driver, but a package. A package is a sort of script which lists what applications are needed to build a driver or an app, and relies on *apt* to track those applications already present in your system, those that are not, and to pull down from the repositories those additional missing dependent apps/packages needed for a successful build. When you consider the complexity that is being resolved silently and in the background, it's really rather amazing how well it works.

Building a driver from scratch without the help of *apt* is possible, but is not for the faint of heart and definitely not for new users. Your earlier attempt to use *module-assistant* was part of a set of instructions for building a driver from scratch. There is no other use for *module-assistant*. That is why I wanted to know what instructions you followed. Sometimes, those instructions monkey around with already installed packages and break dependencies.

As mentioned, *apt* is a high-level uber-app that is dependency-aware. It makes use of a lower-level app called *dpkg* that is not dependency-aware. If you use *dpkg*, you must take care to meet all dependencies beforehand. This is why practically everyone, even power-users, prefer *apt* over *dpkg*. However, there are times when the dependency database is so broken that *apt* can't resolve it. In such cases, there are a number of possible repair tactics: some involve forcing *apt* to resolve dependencies, others involve using *dpkg*. Broken dependencies appear to be what is wrong with your install attempt.

Hope this long-winded explanation clarifies things further. It doesn't help you build the driver, but at least you have a better understanding of what we are trying to do.

---

### Post by MyTinFoilHat on 2013-02-18
Finally got home, so I'll respond as much as I can.


> **DuckHook said:**
> ...hhhmmm. Seems to be more issues here than I first assumed. You mentioned that you tried previous fix attempts. Please describe in as much detail as you can remember. 

Here's what I remember, although not going to be complete. I read many posts, followed suggestions and instructions including how to identify the proper card (lshw -C network) in addition to following suggestions about going into Synaptic as installing firmware-b43-installer at one point, firmware-b43-lpphy-installer at another, uninstalling then reinstalling b43-fwcutter. I'm pretty sure I even tried firmware-b43legacy-installer. A lot of desperate fumbling, to be sure. 

If I go into Synaptic and filter for "firmware-b43" (as I definitely recall being an action to be taken, here's what I see:

[x] firmware-b43-installer
[ ] firmware-b43-lpphy-installer
[x] b43-fwcutter
[ ] firmware-b43legacy-installer

I just took another look at Synaptic. This time filtering for "broadcom". Here's what I see:

[ ] broadcom-sta-common
[x] bcmwl-kernel-source
[ ] broadcom-sta-source
[x] broadcom-sta-dkms
[x] b43-fwcutter
[ ] libcrystalhd-dev
[x] libcrystalhd3
[ ] gstreamer0.10-crystalhd
[ ] crystalhd-dkms

> **DuckHook said:**
> Also, using your mouse, it is possible to select output of terminal and paste into gedit.Not quite sure why you need to transcribe. 


What I was offering to transcribe was not in terminal, but seen in a Crash Report window. I apologize if I didn't make that clear. After we had taken the previous action, there was a system error and a crash report window opened. In looking back at my previous reply, this may not have been clear at all. 

>  Since we are dealing with missing dependencies, what those dependencies actually are now factor into equation. ...then it may be better to open your dpkg.log and look it through. Since all activity is dated, you can select and copy starting from the end. dpkg.log can be massive, so I have not asked you to attach it. Will have to rely on your judgment. Can be found at /var/log/dpkg.log and can be viewed either with your log viewer from dash, or:```
gedit /var/log/dpkg.log
```


Wow! You weren't even slightly exaggerating to say that the dpkg.log is "massive". Sheesh. Although, as you point out, it's dated, so that's a good thing. I'll see what I can find that may be relevant and will post below. For the sake of everyone's sanity, I'll start with the most-recent entries in the log - which appear to be around the time that we started working this problem together. If you need anything prior to it please let me know:

```

2013-02-17 20:11:11 startup packages purge
2013-02-17 20:11:11 status installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:12 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-02-17 20:11:12 status half-configured bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:12 status half-installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:12 status triggers-pending initramfs-tools:all 0.103ubuntu0.2
2013-02-17 20:11:12 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:12 purge bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-02-17 20:11:12 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:13 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:13 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:13 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:13 status config-files bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:11:13 status not-installed bcmwl-kernel-source:amd64 <none>
2013-02-17 20:11:13 trigproc initramfs-tools:all 0.103ubuntu0.2 <none>
2013-02-17 20:11:13 status half-configured initramfs-tools:all 0.103ubuntu0.2
2013-02-17 20:11:30 status installed initramfs-tools:all 0.103ubuntu0.2
2013-02-17 20:19:59 startup archives unpack
2013-02-17 20:20:03 install bcmwl-kernel-source:amd64 <none> 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:03 status half-installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:04 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:04 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:05 startup packages configure
2013-02-17 20:20:05 configure bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-02-17 20:20:05 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:05 status half-configured bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:05 status installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-02-17 20:20:06 status triggers-pending initramfs-tools:all 0.103ubuntu0.2
2013-02-17 20:20:06 trigproc initramfs-tools:all 0.103ubuntu0.2 <none>
2013-02-17 20:20:06 status half-configured initramfs-tools:all 0.103ubuntu0.2
2013-02-17 20:20:32 status installed initramfs-tools:all 0.103ubuntu0.2
2013-02-17 21:18:16 startup archives unpack
2013-02-17 21:18:19 install linux-headers-3.5.0-23:all <none> 3.5.0-23.35
2013-02-17 21:18:19 status half-installed linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:26 status unpacked linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:26 status unpacked linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:28 install linux-headers-3.5.0-23-generic:amd64 <none> 3.5.0-23.35
2013-02-17 21:18:28 status half-installed linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:18:31 status unpacked linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:18:31 status unpacked linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:18:31 install linux-headers-generic:amd64 <none> 3.5.0.23.29
2013-02-17 21:18:31 status half-installed linux-headers-generic:amd64 3.5.0.23.29
2013-02-17 21:18:31 status unpacked linux-headers-generic:amd64 3.5.0.23.29
2013-02-17 21:18:31 status unpacked linux-headers-generic:amd64 3.5.0.23.29
2013-02-17 21:18:32 startup packages configure
2013-02-17 21:18:32 configure linux-headers-3.5.0-23:all 3.5.0-23.35 <none>
2013-02-17 21:18:32 status unpacked linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:32 status half-configured linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:33 status installed linux-headers-3.5.0-23:all 3.5.0-23.35
2013-02-17 21:18:33 configure linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35 <none>
2013-02-17 21:18:33 status unpacked linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:18:33 status half-configured linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:19:08 status installed linux-headers-3.5.0-23-generic:amd64 3.5.0-23.35
2013-02-17 21:19:08 configure linux-headers-generic:amd64 3.5.0.23.29 <none>
2013-02-17 21:19:08 status unpacked linux-headers-generic:amd64 3.5.0.23.29
2013-02-17 21:19:08 status half-configured linux-headers-generic:amd64 3.5.0.23.29
2013-02-17 21:19:08 status installed linux-headers-generic:amd64 3.5.0.23.29

```

> 
As for module-assistant, this is a developer's helper tool to build modules and is not needed with bcmwl-kernel-source unless we try to build from the dpkg itself. No need to get rid of it yet, because it is doing no harm. We may need it later. It does raise the question of why you initially installed it and what other changes you made to your system though.


I honestly don't remember why it's there or what may have led me to put it there (I mean, clearly I did it, but I can't remember what I may have been following at the time. 

> 
This will likely not hurt you, but on the even remote chance that things get hairy, now would be a good time to back up all critical data and then check your backup for integrity.


After posting this response, I'm going to back-up.

> 
btw, broadcom-sta-dkms is the actual binary which builds wl, so its blowing up is significant.


Eek.

> 
Am tempted to apt-get headers with -f, but don't do that yet. Let's see what dpkg.log reveals first.


Just let me know when to do that. I won't attempt anything right now.

>  <edit>
forgot most important question of all... did linux-headers-generic finish installing?
</edit>

Not sure if I already responded to this, but yes, it appears to have finished.

---

### Post by MyTinFoilHat on 2013-02-18
> **DuckHook said:**
> Ahh...
You've been led astray by my geek-speak. Let me try to clarify because it is not as complicated as you think:

A "module" *is* a driver. In Linux-space, they are synonymous terms. So, the command *lsmod*="list modules"="list drivers", *rmmod*="remove module"="remove driver", *insmod*="insert module"="insert driver", and so forth. There are times when guys like me muddy the waters by speaking of a "driver module" but this is just loose terminology that is indulging in a redundancy. The word "driver" can be substituted for "module" on practically all occasions...


First and foremost, do not apologize for any perceived "muddying of waters". I learned many, many things from just that reply - and have an even greater appreciation for the unseen elegance of the "wizard behind the curtain" and have a deeper appreciation for how these things work. In fact, I'm copying it and saving it to my local drive (if you don't mind) as a quick personal reference - until I know all this for myself.  ;)

Now, back to the issue at hand. Since you mention the module-assistant (and wonderfully explained what it's for), it may very well be that I started following instructions to build, but would never have continued. I've never compiled anything myself and have purposely reserved learnig that for a later time, after I've learned as much of the "basics" as is necessary to move onto the next step. As a complete newbie, it's easy to want to dive-in and do things, but even I am humble enough to know that there are things I shouldn't tinker with - simply because I acknowledge that there are things I do not know - and can't know - right now.

BTW, total sidebar, but your response reminded me of two people from my past and I wanted to start my reply with JP? Chris? LOL.

Onward and upward...

---

### Post by DuckHook on 2013-02-19
Good detective work. Unless someone else jumps in I have to entertain guests tonight, so please sit tight. Tomorrow will also be tight, so I will respond when I can.

---

### Post by MyTinFoilHat on 2013-02-19
> **DuckHook said:**
> Good detective work. Unless someone else jumps in I have to entertain guests tonight, so please sit tight. Tomorrow will also be tight, so I will respond when I can.

No worries. I at least have a wired connection. Don't worry, I've learned a thing or two about patience. Have a great time.
Besides, according to the latest report from the brain and body, it's time to get some sleep.

Be well.

---

### Post by fdrake on 2013-02-19
Your problem is right here: Your adapter is not even listed (if it was a module issue it woul say unlocated or something else)
[QUOTE=MyTinFoilHat;12515548

```

eth0      Link encap:Ethernet  HWaddr 00:1e:c2:1c:5f:ca  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c2ff:fe1c:5fca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4005296 (4.0 MB)  TX bytes:546379 (546.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17941 (17.9 KB)  TX bytes:17941 (17.9 KB)

```
[/QUOTE]
You should have an entry for wlan0/1..that shows your wireless adapter  
Give me the output of 
```

sudo rfkill list all

```
also check that you did not disable the wireless with a swicher or a function key - by mistake (check also the bios and see if there is an option to enable/disbale wireless)

what laptop do you have? (brand and model please : be as specific as possible)

---

### Post by MyTinFoilHat on 2013-02-19
Hi, fdrake. Thanks for the response. I'm not at home so I can't check this out yet, but I wanted to let you know I got your response. I also want to potentially respond to any of your questions that don't require my being in front of my laptop.

> **fdrake said:**
> Your problem is right here: Your adapter is not even listed (if it was a module issue it woul say unlocated or something else)

You should have an entry for wlan0/1..that shows your wireless adapter  


Aaah! I see! So, one is to control the wired connection and another (the missing one) is what controls the wifi connection. Have I got that right?

> 
Give me the output of 
```

sudo rfkill list all

```


This I will have to do from home. I will check this out as soon as I can. The command seems familiar to me (perhaps in my jumping around to find a solution). Regardless, I'll shoot a quick reply as soon as I can do this from home.

> 
also check that you did not disable the wireless with a swicher or a function key - by mistake (check also the bios and see if there is an option to enable/disbale wireless)


The only times I've knowingly and intentionally been able to disable the wifi is through the network connection pull-down in the gui (upper, right). Right now, I'm unaware of any function/hot keys that enable or disable the wifi. It could be that one exists and that I did accidentally hit that key(s), but I'm unaware of its existence.

As for bios, unless there is a a cli or gui method for altering the bios (or unless the potential to change the bios exists by way of installing/uninstalling modules, I have never knowingly gone into (or changed) the bios. (I don't dual boot this device - if you're thinking that may have something to do with it also?) I'm also readily willing to negate any other previously-attempted distro installs because, as I mentioned, Ubuntu installed and everything was working well. Now, it could be (as was previously suggested) that a kernel change may have also had some impact (or perhaps it was just coincidence). Then again, you're way more likely to know more about that than I, so I will just shut up and listen.  ;)

As I described in the alternate post (mentioned in my first entry here), I had just reinstalled Ubuntu (long story) and while getting myself re-situated, I merely enabled bluetooth to transfer a file from my smartphone, then the wifi stopped working. This initial problem was likely compounded by my attempts to follow solutions others found here in the forums.

FWIW, I find that I constantly have to turn off bluetooth during restarts. It (for whatever reason) doesn't seem to be capable of remembering its previous ON/OFF state. This is certainly no big deal (it's just a click away, after all), but I'm wondering if that may be a related or separate issue. While I'm mentioning settings not remembering their previous states (on/off), the same thing happens during startup with keyboard and display. I constantly have to manually turn-down/off the backlit keyboard and turn down the brightness of the display. Perhaps these three things (bluetooth, keyboard backlighting, display brightness) are simply compromises I accept in trade for a nice system - or, perhaps, these are limitations to the customization (or availability of) these features, or perhaps they are issues to be explored separately. Again, I don't know.

> 
what laptop do you have? (brand and model please : be as specific as possible)

It is a 17" Macbook Pro 4,1 (I believe). I'm guessing you'll need this information expanded; in which case, I'll have to get back to you.

---

### Post by MyTinFoilHat on 2013-02-19
Here's a strange, new twist:

I just got home, started up the laptop, and (out of curiosity) clicked on my connection (upper-right) which has been wired/auto ethernet since this problem started and BAM - just like that - I can suddenly see all the wifi connections available in my area.

Now, I'm not about to start spitting in good fortune's face, so I'm not going to tinker with anything - including the new update that Software Updater is telling me about - until I can get someone else's opinion on what I can do to be sure this is stable. ...And, no, in the future I won't be using the bluetooth, but I'm not about to go turning it off. I don't want to upset the gremlins...

Right now, as I write this, I'm connected to my home wifi. I'm happy, but cautious.

I'm going to reboot and see what happens next. I'll check back in a few moments wirelessly or otherwise...

> 
EDIT: Well, I'm back. Still connected to wifi. Hmmm... tempted to run lshw -C network to take a peek, but (blutly) I'm a little gun shy right now... I'm going to do a back up...


---

### Post by fdrake on 2013-02-19
are you dual booting or just ubuntu in the macbook?

sometimes a clean shutdown helps to reset the adapter to its default state.


if you are able to connect please mark this thread as "SOLVED".

---

### Post by ALinuxWindowsBalance on 2013-02-19
If you have your manufacturer's driver reinstall disc, DuckDuckGo the driver name and see if you can find a better driver. I have an old D610 laptop that the WiFi cuts out after a while(An hour) and I traced it back to a bad driver, So I called Dell, and I got a driver replace disk. I used Ndiswrapper to bind the driver, and presto! It worked!

---

### Post by MyTinFoilHat on 2013-02-19
> **fdrake said:**
> are you dual booting or just ubuntu in the macbook?

sometimes a clean shutdown helps to reset the adapter to its default state.


if you are able to connect please mark this thread as "SOLVED".

Just straight-up Ubuntu here.

---

### Post by MyTinFoilHat on 2013-02-19
> **ALinuxWindowsBalance said:**
> If you have your manufacturer's driver reinstall disc, DuckDuckGo the driver name and see if you can find a better driver. I have an old D610 laptop that the WiFi cuts out after a while(An hour) and I traced it back to a bad driver, So I called Dell, and I got a driver replace disk. I used Ndiswrapper to bind the driver, and presto! It worked!

Interesting... While I didn't use it in solving this problem, I at least know that I can grab the driver elsewhere-
HA! I just got that. I love the fact that you mentioned DuckDuckGo-ing the driver name. Personally I ixquick or startpage all my queries.  ;)

---

### Post by MyTinFoilHat on 2013-02-19
If anyone has any suggestions for verifying this wifi solution will stick, I'm happy to flag this solved.


Thank you to everyone that responded.

---

### Post by Bashing-om on 2013-02-19
MyTinFoilHat;

Just for your info: I had not abandoned you, have continued to monitor this thread. I had nothing to add to what was advised, so said nothing(in accordance to forum policy).

At this time I still have little of value to offer. If all your log files do not indicate a problem, I would say you are home free. - Glad you are up on wireless -

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

---

### Post by MyTinFoilHat on 2013-02-19
> **Bashing-om said:**
> MyTinFoilHat;

Just for your info: I had not abandoned you, have continued to monitor this thread. I had nothing to add to what was advised, so said nothing(in accordance to forum policy).

At this time I still have little of value to offer. If all your log files do not indicate a problem, I would say you are home free. - Glad you are up on wireless -

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

No worries. I hadn't thought that at all. I realize that people here volunteer their time and I'm deeply grateful for any help that I can get, as it's available. What's more, apart from earning a living, I don't have anywhere in particular to go. I can always read other things and learn while I wait.  :)

As a related side-bar to this, I had another new development:

I finished doing my back up, restarted, and had a brief moment of "UH-OH!" when I clicked on the updates - which, promptly went through their routines. I did notice a few errors coming up during the process (and got crash reports which I submitted)... I want to say that it was related to the linux-sta-dkms (?) I wish I remembered exactly, but I think panic took over - which is why I am having issues remembering the exact module that was freaking out.

Simultaneously, I suddenly remembered that I hadn't followed-up on fdrake's suggestion to run 

```

sudo rfkill list all

```

Should I do that now?
rfkill enables/disables wireless devices, so I'm thinking 'no'... at least not now that the wifi is working.

I know there's a way to trek back through the logs to review these messages at my leisure. I just don't know the process yet.

At any rate, wifi is still working. I'm just wondering if there might be some "post-resolution" steps to clean up any peripheral things that may cause issues (or illicit more kernel messages about modules that don't belong).

---

### Post by DuckHook on 2013-02-19
There is something to be said for leaving well enough alone, but IMO it is still important that you fix all those competing drivers.

Synaptic is a high-level package manager just like apt. If you prefer its GUI interface over apt, then it is also a good choice.

The first order of business is still to delete all competing drivers and their packages. In particular, this includes b43, b43-fwcutter and broadcom-sta-dkms. The b43 packages install a driver for older broadcom chips and simply cannot work on your chip. It will just foul up your WIFI. The sta driver is not part of bcmwl-kernel-source and I suspect that you downloaded all of these packages as part of your previous attempts to fix. None of them are good to have around.

1. In synaptic search first for broadcom again, then followed by b43.

2. We wish to not only uncheck the following packages, but to do so by choosing the option "mark for complete removal". This is Synaptic's version of the --purge option in apt. We must get to a clean slate.
a. bcmwl-kernel-source
b. broadcom-sta-dkms
c. b43-fwcutter
d. firmware-b43-installer
After checkmarking all boxes for complete removal, apply.

3. To keep to the GUI tools, exit Synaptic and open Update Manager. You must exit Synaptic completely before opening Update Manager, or the next step will fail.

4. In Update Manager, click the "check" button. This has the same effect as sudo apt-get update. If anything needs to be updated click "install updates". Close Update Manager.

5. Reboot.

6. Open Synaptic and search for broadcom again.

7. Check only bcmwl-kernel-source and nothing else. Apply.

8. Reboot.

You should now have only the wl driver loaded in kernel space. To check, do:```
lsmod | grep wl
```***Repeat: this is optional at this time. You may simply want to print these instructions and not implement until WIFI goes MIA again.***

---

### Post by fdrake on 2013-02-19
> **MyTinFoilHat said:**
> No worries. I hadn't thought that at all. I realize that people here volunteer their time and I'm deeply grateful for any help that I can get, as it's available. What's more, apart from earning a living, I don't have anywhere in particular to go. I can always read other things and learn while I wait.  :)

As a related side-bar to this, I had another new development:

I finished doing my back up, restarted, and had a brief moment of "UH-OH!" when I clicked on the updates - which, promptly went through their routines. I did notice a few errors coming up during the process (and got crash reports which I submitted)... I want to say that it was related to the linux-sta-dkms (?) I wish I remembered exactly, but I think panic took over - which is why I am having issues remembering the exact module that was freaking out.

Simultaneously, I suddenly remembered that I hadn't followed-up on fdrake's suggestion to run 

```

sudo rfkill list all

```

Should I do that now?
rfkill enables/disables wireless devices, so I'm thinking 'no'... at least not now that the wifi is working.

I know there's a way to trek back through the logs to review these messages at my leisure. I just don't know the process yet.

At any rate, wifi is still working. I'm just wondering if there might be some "post-resolution" steps to clean up any peripheral things that may cause issues (or illicit more kernel messages about modules that don't belong).

my commands only lists the status of your adapters it tells you why they don't show up; if they have been disabled by a physical switch(or in the bios) or by a software. it's a way to check things before installin and moving stuff around.

---

### Post by MyTinFoilHat on 2013-02-19
> **DuckHook said:**
> There is something to be said for leaving well enough alone, but IMO it is still important that you fix all those competing drivers.

Synaptic is a high-level package manager just like apt. If you prefer its GUI interface over apt, then it is also a good choice.

The first order of business is still to delete all competing drivers and their packages. In particular, this includes b43, b43-fwcutter and broadcom-sta-dkms. The b43 packages install a driver for older broadcom chips and simply cannot work on your chip. It will just foul up your WIFI. The sta driver is not part of bcmwl-kernel-source and I suspect that you downloaded all of these packages as part of your previous attempts to fix. None of them are good to have around.

1. In synaptic search first for broadcom again, then followed by b43.

2. We wish to not only uncheck the following packages, but to do so by choosing the option "mark for complete removal". This is Synaptic's version of the --purge option in apt. We must get to a clean slate.
a. bcmwl-kernel-source
b. broadcom-sta-dkms
c. b43-fwcutter
d. firmware-b43-installer
After checkmarking all boxes for complete removal, apply.

3. To keep to the GUI tools, exit Synaptic and open Update Manager. You must exit Synaptic completely before opening Update Manager, or the next step will fail.

4. In Update Manager, click the "check" button. This has the same effect as sudo apt-get update. If anything needs to be updated click "install updates". Close Update Manager.

5. Reboot.

6. Open Synaptic and search for broadcom again.

7. Check only bcmwl-kernel-source and nothing else. Apply.

8. Reboot.

You should now have only the wl driver loaded in kernel space. To check, do:```
lsmod | grep wl
```***Repeat: this is optional at this time. You may simply want to print these instructions and not implement until WIFI goes MIA again.***

On step 5 right now. I've made sure I read, reread, and re-reread the instructions (and nicely written explanations!)... I'll be back in a moment or so to proceed.

(THANK YOU!!!)

---

### Post by MyTinFoilHat on 2013-02-19
All is well in the Universe once again - and would not be so without the skills and knowledge of DuckHook.

I'm happy to report that not only is my issue resolved and [SOLVED], but that I have developed a good amount of faith in the skills, knowledge, understanding, and patience of DuckHook. DuckHook, I am very grateful for your tenacity and willingness to see this solution through to a complete end.

I am deeply, deeply grateful to everyone that viewed and responded to help out a stranger. I have learned much - basic things that, perhaps, many might take for granted due to their years of experience. I've also learned that I should also proceed with a little more caution and little less daring until I am more secured in my knowledge. More importantly, I've learned that I have a lot more to learn but with patience, these things will come to pass.

I would also like to thank fdrake and Bashing-om for checking-in. It's always good to know that there are always extra eyes helping us all look out for one another - either directly or by way of advocating for others.

```

user1@compooter:~$ lsmod | grep wl
wl                   2573608  0 
lib80211               14382  2 lib80211_crypt_tkip,wl

```

---

### Post by fdrake on 2013-02-19
you are welcome!

---

### Post by DuckHook on 2013-02-19
> **MyTinFoilHat said:**
> All is well in the Universe once again...I am very grateful for your tenacity and willingness to see this solution through to a complete end.

Your kind appreciation is more than enough reward.

Good luck and Happy Ubuntuing!

---

### Post by Bashing-om on 2013-02-19
it's all a learning experience. That is one of the wonders of this operating system.

---

