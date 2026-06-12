---
title: "apt-get is always unable to find packages"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by thecjkid on 2013-07-19
I am running Ubuntu 12.04 and every time i try to download an app using apt-get terminal is unable to locate the packages. I have updated several times to no avail. When I try to retrieve the programs from the software center i am told that they are not installed and can find no option to install them.

---

### Post by ibjsb4 on 2013-07-19
Please post the output of:

```
cat /etc/apt/sources.list
```

And give us a couple of examples of what your trying to download.

---

### Post by deadflowr on 2013-07-19
You can also post the output for 
```
sudo apt-get update
```

For both the cat command in post#2 and this, please paste them into the Code tags.
(Code tags are the # symbol in the reply box toolbar)

---

### Post by ibjsb4 on 2013-07-20
Code tags :)

[ATTACH=CONFIG]244916[/ATTACH]

---

### Post by thecjkid on 2013-07-20
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
carmen@carmen-HP-Pavilion-g7-Notebook-PC:~$ 
```








```
carmen@carmen-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get update
[sudo] password for carmen: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [400 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [92.0 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [650 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [209 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [671 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [213 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,935 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [32.0 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [4,872 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,378 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [31.4 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [4,852 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,390 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [31.2 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [4,829 B]
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
Fetched 2,511 kB in 4s (608 kB/s)
Reading package lists... Done
carmen@carmen-HP-Pavilion-g7-Notebook-PC:~$
```

---

### Post by mc4man on 2013-07-20
> **thecjkid said:**
> I am running Ubuntu 12.04 and every time i try to download an app using apt-get terminal is unable to locate the packages. 
What is one of the  apps that you wanted to install?

---

### Post by ibjsb4 on 2013-07-20
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
carmen@carmen-HP-Pavilion-g7-Notebook-PC:~$ 








carmen@carmen-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get update
[sudo] password for carmen: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [400 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [92.0 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [650 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [209 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [671 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [213 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,935 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [32.0 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [4,872 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,378 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [31.4 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [4,852 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,390 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [31.2 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [4,829 B]
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
```

Looks good, the only thing you didn't include is:

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

---

### Post by snowpine on 2013-07-20
Don't you think we could help you better if you told us the name of the mystery application(s) you are trying to install? :)

---

