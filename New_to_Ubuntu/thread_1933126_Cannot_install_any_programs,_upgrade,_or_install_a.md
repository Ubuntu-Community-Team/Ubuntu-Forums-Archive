---
title: "Cannot install any programs, upgrade, or install any Ubuntu updates."
date: 2012-02-28
forum: New to Ubuntu
---

### Post by TheGoodCaptain on 2012-02-28
So this has been happening since I installed Ubuntu on this system.

The Hard Drive, a 500GB SATA, has had a multitude of various tests ran on it, and diagnostics declare the hardware to be in great health.  I install Ubuntu 11.10 on this system and it will not upgrade, install updates, or any other program I try to install, like Chrome or Mudlet.  Here is an example.  I will list, below, in this order:

sudo apt-get update
sudo apt-get upgrade

And the results of me trying to install Mudlet through the Ubuntu Software Center.

```
phantom@ocelot-NV53A:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                 
Ign http://extras.ubuntu.com oneiric InRelease                               
Hit http://us.archive.ubuntu.com oneiric Release.gpg                         
Ign http://security.ubuntu.com oneiric-security InRelease            
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg        
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://extras.ubuntu.com oneiric/main Sources                     
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric-updates Release             
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports Release           
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric/universe Sources            
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://security.ubuntu.com oneiric-security/main Translation-en  
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done

```


Then ....

```
phantom@ocelot-NV53A:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gedit-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/160 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? yes
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libcupsdriver1': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


And finally, program installation:

```
installArchives() failed: Selecting previously deselected package liblua5.1-rex-pcre0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'libcupsdriver1': Input/output error 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 

```


C'mon guys, lol.  I mean, the install was a LiveUSB made, as directed by the official site, with the download provided by Ubuntu.com.  Surely this is something simple, I am just too novice to understand it, currently.

---

### Post by TeoBigusGeekus on 2012-02-28
Perhaps [this thread and post]("http://ubuntuforums.org/showthread.php?p=8468629#post8468629")?

---

