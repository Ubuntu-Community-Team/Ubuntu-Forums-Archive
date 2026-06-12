---
title: "Unable to locate package supercollider-plugins"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by stephen.genovese on 2013-11-16
Tried a few different methods mentioned in other threads I searched for and haven't had any luck. Trying to search for a solution but if anyone could help me speed things along it would be appreciated.

I'll include some of the information asked for in other threads and what I've done already to speed things up.

I've tried reloading the synaptic package manager

Output of sudo apt-get update
```
Hit http://au.archive.ubuntu.com precise Release.gpg
Hit http://au.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://au.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://au.archive.ubuntu.com precise Release                               
Hit http://au.archive.ubuntu.com precise-updates Release                       
Hit http://au.archive.ubuntu.com precise-backports Release                     
Hit http://au.archive.ubuntu.com precise/main Sources                          
Hit http://au.archive.ubuntu.com precise/restricted Sources                    
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://au.archive.ubuntu.com precise/universe Sources                      
Hit http://au.archive.ubuntu.com precise/multiverse Sources
Hit http://au.archive.ubuntu.com precise/main i386 Packages
Hit http://au.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://au.archive.ubuntu.com precise/universe i386 Packages      
Hit http://au.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com precise/main TranslationIndex       
Hit http://au.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://au.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://au.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/main Sources        
Hit http://au.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://au.archive.ubuntu.com precise-updates/universe Sources    
Hit http://au.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://au.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://au.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://au.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://au.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://au.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://au.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://au.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://au.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://au.archive.ubuntu.com precise-backports/main Sources      
Hit http://au.archive.ubuntu.com precise-backports/restricted Sources
Hit http://au.archive.ubuntu.com precise-backports/universe Sources  
Hit http://au.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://au.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://au.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://ppa.launchpad.net precise Release.gpg                     
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]  
Hit http://au.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://au.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise/main Translation-en_AU                
Hit http://au.archive.ubuntu.com precise/main Translation-en                   
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://au.archive.ubuntu.com precise/restricted Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/restricted Translation-en             
Hit http://au.archive.ubuntu.com precise/universe Translation-en               
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en_AU        
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://au.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources         
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Get:3 http://security.ubuntu.com precise-security/main Sources [93.6 kB]
Get:4 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:5 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [1,797 B]
Get:7 http://security.ubuntu.com precise-security/main i386 Packages [359 kB]
Get:8 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:9 http://security.ubuntu.com precise-security/universe i386 Packages [88.9 kB]
Get:10 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,635 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Ign http://ppa.launchpad.net precise/main Translation-en_AU
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 633 kB in 6s (94.9 kB/s)                                               
Reading package lists... Done
```


Outpot of cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu-Studio 12.04.3 _Precise Pangolin_ - Release i386 (20130820)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

Cheers,

fordferde

---

### Post by ibjsb4 on 2013-11-17
How did you download and install the plugins?  I ask because all I find is the source packages (src) for this plugin.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+source+package&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+source+package&sa=Search&cof=FORID:9)

---

