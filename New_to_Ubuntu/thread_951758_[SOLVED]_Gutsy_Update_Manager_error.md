---
title: "[SOLVED] Gutsy Update Manager error"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-10-18
I have 4 updates to install with the update manager. When I try they stall in the process. Is there any way to delete them & wait for the next update ?

---

### Post by philinux on 2008-10-18
Open a terminal and use

```
sudo apt-get update && sudo apt-get upgrade
```

Post back with any errors.

---

### Post by CoCoKnots on 2008-10-18
OK, This is what came up. Also, it still hangs up after installing 19 % of the first file :Kaffeine. :confused:

cocoknots@cocoknots-laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for cocoknots:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources  
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
  
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 11.9kB in 5s (2347B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  kaffeine libavcodec1d libavformat1d libpostproc1d
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5255kB of archives.
After unpacking 594kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kaffeine libavcodec1d libavformat1d libpostproc1d
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free kaffeine 0.8.5-0ubuntu1+medibuntu1 [3007kB]
11% [1 kaffeine 581883/3007kB 19%]

---

### Post by philinux on 2008-10-18
Ok lets fix that key first

Use copy and paste this into the terminal. Then run that first command again.

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by CoCoKnots on 2008-10-18
That help a little... This time it loaded 27 %.

...The following packages will be upgraded:
  kaffeine libavcodec1d libavformat1d libpostproc1d
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5255kB of archives.
After unpacking 594kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free kaffeine 0.8.5-0ubuntu1+medibuntu1 [3007kB]
15% [1 kaffeine 836259/3007kB 27%]

---

### Post by philinux on 2008-10-18
Post the out put of this

cat /etc/apt/sources.list

when you do highlight the stuff and click # symbol in the message pane to wrap code tags around it.  Makes it easier to read.

---

### Post by CoCoKnots on 2008-10-18
[B]when you do highlight the stuff and click # symbol in the message pane to wrap code tags around it. Makes it easier to read.
[/B] I'm not sure what you mean by this... When I click on # everything disappears. Sorry...


cocoknots@cocoknots-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
cocoknots@cocoknots-laptop:~$

---

### Post by philinux on 2008-10-18
Ok use this

gksudo gedit /etc/apt/sources.list

Where you see a line starting
# deb 

delete the #

Save the file

Then run the first command again.

---

### Post by CoCoKnots on 2008-10-18
Well... I have no idea what I'm doing here... But this is what I have to this point. It hung again on some unknown file. I hope this makes sense to you.

cocoknots@cocoknots-laptop:~$ gksudo gedit /etc/apt/sources.list
cocoknots@cocoknots-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:6 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release [65.9kB]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Get:12 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [3613B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Get:13 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources [1483B]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [113kB]         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]           
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages [1075kB]               
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5280B]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [22.2kB]         
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [944B]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [83.9kB]    
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [12.5kB]     
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [7188B]   
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [1145B]    
42% [17 Packages 90306/1075kB 8%]

---

### Post by CoCoKnots on 2008-10-18
Opps... I spoke too soon. It's still loading the file... It looked like it had stopped.

---

### Post by CoCoKnots on 2008-10-18
It's taken over an hour... But it finally finished the update download.
Re-booted & it looks to be working fine. Thanks Philinux. I appreciate the help.

---

