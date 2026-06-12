---
title: "sudo apt-file update doesn't work"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Cap'n Redbeard on 2008-05-02
Hi Folks,

When i try to get the list of available files, this happens:

> redbeard@Redbeard-desktop:~$ sudo apt-file update
[sudo] password for redbeard: 
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz) (404)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz) (404)
redbeard@Redbeard-desktop:~$ 


Having looked through the forums, i still don't know what to do.

Possible solutions:

1. Proxy settings - None are set up on this machine.
2. Development - During the development of Hardy *.gz files were not accepted. Is this relevant ?

Other than that i haven't the foggiest idea why the apt-file update won't work, or how to cure it. :confused:

Any ideas ?

---

### Post by encompass on 2008-05-02
It seems that they don't exist... at least if I try to go to them with the browser.  SO they don't exist.  Must be some reason.  Just not sure.

---

### Post by kerry_s on 2008-05-02
try-> **sudo apt-get update**

---

### Post by Nepherte on 2008-05-02
404 error = file not found. Maybe you should try another mirror. Can you post the output of cat /etc/apt/sources.list

---

### Post by Cap'n Redbeard on 2008-05-02
sudo apt-get update works - look:

> redbeard@Redbeard-desktop:~$ sudo apt-get update
[sudo] password for redbeard: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Reading package lists... Done
redbeard@Redbeard-desktop:~$ 


Yes, and when i look for the URL's sudo apt-file update is looking for on another system, they're not there.

Strange...

It's been like that since midnight on Wednesday. Any ideas ?

---

### Post by Cap'n Redbeard on 2008-05-02
> redbeard@Redbeard-desktop:/etc/apt$ cat sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
redbeard@Redbeard-desktop:/etc/apt$ 


Any help ?

---

### Post by Cap'n Redbeard on 2008-05-02
Aah,

The web directories

> sudo apt-file update

looks for are there, but the files "Contents-i386.gz" don't exist.

> Icon  Name                    Last modified      Size  [DIR] Parent Directory                             -   
[   ] Release                 02-May-2008 17:44   36K  
[   ] Release.gpg             02-May-2008 17:45  191   
[DIR] main/                   18-Oct-2007 17:18    -   
[DIR] multiverse/             18-Oct-2007 17:18    -   
[DIR] restricted/             18-Oct-2007 17:18    -   
[DIR] universe/               18-Oct-2007 17:18    -   


Could it be that the "contents" files have not been updated, or another system for listing the contents for various platforms is in place ?

Several other folks in these forums have had difficulty obtaining updates with Gutsy and Hardy. I wonder if this is the problem ?

Any thoughts ?

---

### Post by Oldsoldier2003 on 2008-05-02
> **Cap'n Redbeard said:**
> Aah,

The web directories



looks for are there, but the files "Contents-i386.gz" don't exist.



Could it be that the "contents" files have not been updated, or another system for listing the contents for various platforms is in place ?

Several other folks in these forums have had difficulty obtaining updates with Gutsy and Hardy. I wonder if this is the problem ?

Any thoughts ?

I don't think that they have implemented any new system it's probably an oversight. Not that I would have any specific knowledge if they were implementing a new system.It's just I haven't heard any news and I think that removing apt-file would have made at least some ripples in the community

---

### Post by Cap'n Redbeard on 2008-05-02
Thanks for your response OldSoldier,

Some folk have mentioned a problem:

>    	
[ubuntu] Can't install softwares. (Multi-page thread 1 2)
manojks
[ubuntu] No Hardy updates (Multi-page thread 1 2)
urvaksh 

Also some stuff in "The Beginners Team has started".

From reading these, they may be related to the same thing ?

O'course, if we users don't get software updates how would we know if a different contents listing system is being used ? There are two header files at the URL but i've no idea to what they relate.

There's an answer out there somewhere - let's find it :)

---

