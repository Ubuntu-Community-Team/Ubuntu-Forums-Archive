---
title: "Myriad problems with partial Cinnamon install"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by connor.ruebusch on 2014-05-19
Okay, so this has plagued me in several ways. When I first got my Ubuntu computer I didn't know what I was doing, and partially installed Cinnamon on my system. Since then I haven't been able to completely resolve the issue. 

At the moment, I cannot get software center to open, nor will the Update Manager run. I receive the following error message when I try to run the Update Manager: 

```
binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
```

Now I thought I had resolved this problem a little while back, using this old fix offered to me by a helpful forum member. 

```

sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```





Now, however, the problem has cropped up again, and upon trying to run that fix, I run into a speed bump at the third step. Entering "sudo mv lists lists.old" into a terminal, I get the following:

```
mv: cannot move `lists' to `lists.old/lists': Directory not empty
```

What do I do! These frequent problems are pretty frustrating. Can someone help me out, please?

---

### Post by J_Me on 2014-05-20
'sudo mv lists lists2.old'
Think of mv(move) as renaming a file.

---

### Post by connor.ruebusch on 2014-05-20
```
J_Me;13028365]'sudo mv lists lists2.old'
Think of mv(move) as renaming a file.
```

Thanks J_Me, that seems to have solved the immediate problem. 

Here's what I get back from that final update command. 

```
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                      
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Get:8 [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan Release.gpg [287 B]      
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:14 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,210 B]               
Get:15 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                      
Get:16 [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan Release [4,240 B]       
Get:17 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,201 B]                
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:19 [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Sources [1,261 B]
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8,130 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:21 [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public amd64 Packages [1,114 B]
Get:22 [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public i386 Packages [1,114 B]
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public TranslationIndex    
Get:23 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [10.8 kB]          
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [104 kB]       
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [2,320 B]                  
Get:26 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10.8 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,767 B]                 
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [4,827 B]          
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [4,548 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,794 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]  
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [385 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [155 kB]           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5,019 kB]           
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [770 B]                   
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [667 B]            
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Translation-en_US   
Get:40 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Translation-en      
Get:41 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,453 B]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [93.1 kB]
Get:45 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [659 B]             
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [414 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [2,320 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
E: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2


```

Can you tell me what the meaning of this GPG error is? It was popping up before, as well. 

Also, does anyone care to explain what I'm actually doing by using the fix above? What is "lists" and why am I moving it to another file location? Thanks!

---

### Post by connor.ruebusch on 2014-06-07
Anyone have any suggestions as to how I can fix this for good? It'd be nice to not have to continually run that fix every time Software Center stops working, or updates won't install. Thanks!

---

### Post by Frogs Hair on 2014-06-07
Please add the method used to install Cinnamon if possible because it will affect a possible solution .  Post the output of the following command and use the # symbol to wrap with code tags. ```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by connor.ruebusch on 2014-06-08
I wish I could remember better how that partial install happened, but I'll try to give you as much detail as I can. I had just gotten the computer and, being a lifelong Windows user, had no idea how Ubuntu worked, but wanted to give Cinnamon a whirl. So I believe I went and downloaded the file and tried to run an install wizard like I would for a Windows program. Nothing happened as far as I could tell, other than a Cinnamon file getting added to my downloads, but I do believe that partial install has caused this error. 

Here's the output from that command:

```
#/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted multiverse
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list:## repository.
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb-src [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb-src [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) precise main
/etc/apt/sources.list.d/fossfreedom-byzanz-precise.list:deb [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu) precise main
/etc/apt/sources.list.d/fossfreedom-byzanz-precise.list:deb-src [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu) precise main
/etc/apt/sources.list.d/fossfreedom-byzanz-precise.list.save:deb [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu) precise main
/etc/apt/sources.list.d/fossfreedom-byzanz-precise.list.save:deb-src [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu) precise main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list:deb [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list:deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list.save:deb [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
/etc/apt/sources.list.d/precise-annan.list:deb [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public
/etc/apt/sources.list.d/precise-annan.list:deb-src [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public
/etc/apt/sources.list.d/precise-annan.list.save:deb [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public
/etc/apt/sources.list.d/precise-annan.list.save:deb-src [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public#
```

---

### Post by connor.ruebusch on 2014-06-08
Whoops. Looks like I didn't get what you meant with those code tags. My apologies! And thanks for the help.

---

### Post by Frogs Hair on 2014-06-09
I see a Cinnamon PPA in the list .
```
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list:deb [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu]("http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu") precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list:deb-src [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu]("http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu") precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list.save:deb [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu]("http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu") precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev_cinnamon-stable-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu]("http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu") precise main

``` Try the following commands.

```
sudo apt-get remove cinnamon
``` ```
sudo apt-get autoremove
``` ```
sudo apt-get install --reinstall ubuntu-desktop
```
Open software sources-other software and remove the the PPA source. The picture may be different because I am using 14.04.

---

### Post by connor.ruebusch on 2014-06-09
Okay, here are the outputs from those lines of code. 

sudo apt-get remove cinnamon gives me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cinnamon
```

sudo apt-get autoremove gives me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  archdetect-deb btrfs-tools dmraid gir1.2-json-1.0 gir1.2-timezonemap-1.0
  gir1.2-ubuntuoneui-3.0 gir1.2-xkl-1.0 kde-l10n-engb language-pack-kde-en
  language-pack-kde-en-base libdebconfclient0 libdebian-installer4
  libdmraid1.0.0.rc16 libio-pty-perl libipc-run-perl libubuntuoneui-3.0-1
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic localechooser-data
  moreutils python-pyicu rdate realpath user-setup
0 upgraded, 0 newly installed, 24 to remove and 7 not upgraded.
After this operation, 78.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 260671 files and directories currently installed.)
Removing archdetect-deb ...
Removing btrfs-tools ...
Removing dmraid ...
update-initramfs: deferring update (trigger activated)
Removing gir1.2-timezonemap-1.0 ...
Removing gir1.2-json-1.0 ...
Removing gir1.2-ubuntuoneui-3.0 ...
Removing gir1.2-xkl-1.0 ...
Removing kde-l10n-engb ...
Removing libdebconfclient0 ...
Removing libdebian-installer4 ...
Removing libdmraid1.0.0.rc16 ...
Removing moreutils ...
Removing libipc-run-perl ...
Removing libio-pty-perl ...
Removing libubuntuoneui-3.0-1 ...
Removing linux-headers-3.2.0-32-generic ...
Removing linux-headers-3.2.0-32 ...
Removing localechooser-data ...
Removing python-pyicu ...
Removing rdate ...
Removing realpath ...
Removing user-setup ...
Removing language-pack-kde-en-base ...
Removing language-pack-kde-en ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-63-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
```

And then sudo apt-get install --reinstall ubuntu-desktop doesn't seem to work at all. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of ubuntu-desktop is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

Where can I find Software Sources? It doesn't turn up in a Unity Search for me.

---

### Post by Frogs Hair on 2014-06-09
For code tags highlight the text as if you were copying and use the # symbol on the reply tools next to quote.

---

### Post by Frogs Hair on 2014-06-09
Try ```
sudo apt-get-remove cinnamon-desktop 
``` ```
sudo apt-get update && sudo apt-get upgrade   


```

Curious why  a kde language pack was removed. Have there been other desktops installed besides Cinnamon ?  
```
language-pack-kde-en-base
```

To display current desktop .```
 echo $XDG_CURRENT_DESKTOP
```

---

