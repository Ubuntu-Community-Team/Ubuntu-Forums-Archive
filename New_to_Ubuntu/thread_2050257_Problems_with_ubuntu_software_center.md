---
title: "Problems with ubuntu software center"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by sreeajaym on 2012-08-30
[QUOTE=amjjawad;11080009]+1

**_sree@sree-desktop:~$ sudo apt-get install -f_**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libicu-dev
Suggested packages:
  icu-doc
The following NEW packages will be installed:
  libicu-dev
0 upgraded, 1 newly installed, 0 to remove and 399 not upgraded.
3 not fully installed or removed.
Need to get 9,708 kB of archives.
After this operation, 29.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libicu-dev i386 4.8.1.1-3
  403  Forbidden
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu-dev_4.8.1.1-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu-dev_4.8.1.1-3_i386.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


_**sree@sree-desktop:~$ sudo dpkg --configure -a**_


dpkg: dependency problems prevent configuration of libboost-regex1.46-dev:
 libboost-regex1.46-dev depends on libicu-dev; however:
  Package libicu-dev is not installed.
dpkg: error processing libboost-regex1.46-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost1.46-all-dev:
 libboost1.46-all-dev depends on libboost-regex1.46-dev; however:
  Package libboost-regex1.46-dev is not configured yet.
dpkg: error processing libboost1.46-all-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-iostreams1.46-dev:
 libboost-iostreams1.46-dev depends on libboost-regex1.46-dev (= 1.46.1-7ubuntu3); however:
  Package libboost-regex1.46-dev is not configured yet.
dpkg: error processing libboost-iostreams1.46-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libboost-regex1.46-dev
 libboost1.46-all-dev
 libboost-iostreams1.46-dev

[B][COLOR=black][U]
sree@sree-desktop:~$ sudo apt-get update && apt-get upgrade[/U][/COLOR][/B]


Ign [http://files.ettus.com](http://files.ettus.com) precise InRelease                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                 
Ign [http://files.ettus.com](http://files.ettus.com) precise Release.gpg                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                             
Hit [http://files.ettus.com](http://files.ettus.com) precise Release                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                   
Ign [http://files.ettus.com](http://files.ettus.com) precise/main i386 Packages/DiffIndex                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages               
Ign [http://files.ettus.com](http://files.ettus.com) precise/main TranslationIndex                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://files.ettus.com](http://files.ettus.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://files.ettus.com](http://files.ettus.com) precise/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Ign [http://files.ettus.com](http://files.ettus.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?




 thanks

---

### Post by oldos2er on 2012-08-30
Post moved to its own thread.

> E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? You need to run *apt-get upgrade* as root: ```
sudo apt-get upgrade
``` To update and upgrade with one command: ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by NikTh on 2012-08-30
Hi , 
can you post the results of 
```
ls /etc/apt/sources.list.d/
cat -n /etc/apt/sources.list
``` 

Also you can try ```
sudo apt-get update --fix-missing 
sudo apt-get dist-upgrade --fix-broken
```

Put the results between the ```
 brackets . [noparse][code]The Results Here
```[/noparse]

Thanks

---

