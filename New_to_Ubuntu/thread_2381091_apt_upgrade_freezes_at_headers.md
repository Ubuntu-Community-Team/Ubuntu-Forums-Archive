---
title: "apt upgrade freezes at headers"
date: 2017-12-26
forum: New to Ubuntu
---

### Post by micahpage on 2017-12-26
I can not update, and it sits at waiting for headers forever

```
metulburr ~ $ sudo apt-get updateHit http://security.ubuntu.com trusty-security InRelease
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://mirrors.digitalocean.com trusty InRelease           
Hit http://mirrors.digitalocean.com trusty-updates InRelease
Hit http://mirrors.digitalocean.com trusty Release.gpg                 
Hit http://mirrors.digitalocean.com trusty-updates/main Sources
Hit http://mirrors.digitalocean.com trusty-updates/universe Sources
Hit http://mirrors.digitalocean.com trusty-updates/main amd64 Packages
Hit https://repos.sonar.digitalocean.com main InRelease
Hit https://repos.sonar.digitalocean.com main/main amd64 Packages      
Hit https://repos.sonar.digitalocean.com main/main i386 Packages
Get:1 https://repos.sonar.digitalocean.com main/main Translation-en_US
Hit http://mirrors.digitalocean.com trusty-updates/universe amd64 Packages
Get:2 https://repos.sonar.digitalocean.com main/main Translation-en
Get:3 https://repos.sonar.digitalocean.com main/main Translation-en_US 
Hit http://mirrors.digitalocean.com trusty-updates/main i386 Packages     
Get:4 https://repos.sonar.digitalocean.com main/main Translation-en
Get:5 https://repos.sonar.digitalocean.com main/main Translation-en_US 
Hit http://mirrors.digitalocean.com trusty-updates/universe i386 Packages 
Get:6 https://repos.sonar.digitalocean.com main/main Translation-en
Get:7 https://repos.sonar.digitalocean.com main/main Translation-en_US
Hit http://mirrors.digitalocean.com trusty-updates/main Translation-en    
Get:8 https://repos.sonar.digitalocean.com main/main Translation-en
Get:9 https://repos.sonar.digitalocean.com main/main Translation-en_US 
Ign https://repos.sonar.digitalocean.com main/main Translation-en_US           
Hit http://mirrors.digitalocean.com trusty-updates/universe Translation-en     
Get:10 https://repos.sonar.digitalocean.com main/main Translation-en
Ign https://repos.sonar.digitalocean.com main/main Translation-en             
Hit http://mirrors.digitalocean.com trusty Release                            
Hit http://mirrors.digitalocean.com trusty/main Sources
Get:11 http://mirrors.digitalocean.com trusty/universe Sources [6,399 kB]
100% [Waiting for headers]                                               
```
and will just sit there.

I checked to see if i had a bad PPA added, but i dont.
```
metulburr ~ $ cat  /etc/apt/sources.list## Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
#


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirrors.digitalocean.com/ubuntu trusty main
deb-src http://mirrors.digitalocean.com/ubuntu trusty main


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.digitalocean.com/ubuntu trusty-updates main
deb-src http://mirrors.digitalocean.com/ubuntu trusty-updates main


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.digitalocean.com/ubuntu trusty universe
deb-src http://mirrors.digitalocean.com/ubuntu trusty universe
deb http://mirrors.digitalocean.com/ubuntu trusty-updates universe
deb-src http://mirrors.digitalocean.com/ubuntu trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://mirrors.digitalocean.com/ubuntu trusty multiverse
# deb-src http://mirrors.digitalocean.com/ubuntu trusty multiverse
# deb http://mirrors.digitalocean.com/ubuntu trusty-updates multiverse
# deb-src http://mirrors.digitalocean.com/ubuntu trusty-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mirrors.digitalocean.com/ubuntu trusty-backports main restricted universe multiverse
# deb-src http://mirrors.digitalocean.com/ubuntu trusty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


deb http://security.ubuntu.com/ubuntu trusty-security main
deb-src http://security.ubuntu.com/ubuntu trusty-security main
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
# deb http://security.ubuntu.com/ubuntu trusty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse



```

Sometimes i will run it and will get errors, sometimes i dont.
```
metulburr ~ $ sudo apt-get updateHit http://security.ubuntu.com trusty-security InRelease
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://mirrors.digitalocean.com trusty InRelease                           
Hit http://mirrors.digitalocean.com trusty-updates InRelease                   
Hit http://mirrors.digitalocean.com trusty Release.gpg              
Hit http://mirrors.digitalocean.com trusty-updates/main Sources
Hit http://mirrors.digitalocean.com trusty-updates/universe Sources
Hit http://mirrors.digitalocean.com trusty-updates/main amd64 Packages
Hit http://mirrors.digitalocean.com trusty-updates/universe amd64 Packages
Hit http://mirrors.digitalocean.com trusty-updates/main i386 Packages
Hit http://mirrors.digitalocean.com trusty-updates/universe i386 Packages
Hit http://mirrors.digitalocean.com trusty-updates/main Translation-en
Hit https://repos.sonar.digitalocean.com main InRelease
Hit http://mirrors.digitalocean.com trusty-updates/universe Translation-en
Hit https://repos.sonar.digitalocean.com main/main amd64 Packages      
Hit https://repos.sonar.digitalocean.com main/main i386 Packages
Get:1 https://repos.sonar.digitalocean.com main/main Translation-en_US
Hit http://mirrors.digitalocean.com trusty Release                        
Get:2 https://repos.sonar.digitalocean.com main/main Translation-en
Get:3 https://repos.sonar.digitalocean.com main/main Translation-en_US
Hit http://mirrors.digitalocean.com trusty/main Sources                   
Get:4 https://repos.sonar.digitalocean.com main/main Translation-en
Get:5 https://repos.sonar.digitalocean.com main/main Translation-en_US
Hit http://mirrors.digitalocean.com trusty/universe Sources               
Get:6 https://repos.sonar.digitalocean.com main/main Translation-en
Get:7 https://repos.sonar.digitalocean.com main/main Translation-en_US 
Hit http://mirrors.digitalocean.com trusty/main amd64 Packages                
Get:8 https://repos.sonar.digitalocean.com main/main Translation-en           
Get:9 http://mirrors.digitalocean.com trusty/universe amd64 Packages [5,859 kB]
Get:10 https://repos.sonar.digitalocean.com main/main Translation-en_US        
Ign https://repos.sonar.digitalocean.com main/main Translation-en_US           
Get:11 https://repos.sonar.digitalocean.com main/main Translation-en           
Ign https://repos.sonar.digitalocean.com main/main Translation-en              
Err http://mirrors.digitalocean.com trusty/universe i386 Packages              
  
100% [Waiting for headers] 
```

or 
```
$ sudo updater                         /usr/bin/updater: 1: /usr/bin/updater: /usr/bin/bash: not found
updating packages
Ign http://mirrors.digitalocean.com trusty InRelease
Hit http://mirrors.digitalocean.com trusty-updates InRelease
Get:1 http://mirrors.digitalocean.com trusty Release.gpg [933 B]
Hit http://mirrors.digitalocean.com trusty Release      
Hit http://mirrors.digitalocean.com trusty-updates/main Sources                
Hit http://mirrors.digitalocean.com trusty-updates/universe Sources   
Hit http://mirrors.digitalocean.com trusty-updates/main amd64 Packages
Hit http://mirrors.digitalocean.com trusty-updates/universe amd64 Packages
Hit http://mirrors.digitalocean.com trusty-updates/main i386 Packages
Get:2 http://mirrors.digitalocean.com trusty-updates/universe i386 Packages [435 kB]
Hit http://security.ubuntu.com trusty-security InRelease                  
Err http://mirrors.digitalocean.com trusty-updates/universe Translation-en     
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/main Sources                        
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/universe Sources         
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/main amd64 Packages      
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/universe amd64 Packages  
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/main i386 Packages       
  Bad header line [IP: 192.241.164.26 80]
Err http://mirrors.digitalocean.com trusty/universe i386 Packages   
  Bad header line [IP: 192.241.164.26 80]
Hit http://security.ubuntu.com trusty-security/main Sources         
Hit http://security.ubuntu.com trusty-security/universe Sources     
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en   
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit https://repos.sonar.digitalocean.com main InRelease              
Hit https://repos.sonar.digitalocean.com main/main amd64 Packages              
Hit https://repos.sonar.digitalocean.com main/main i386 Packages     
Get:3 https://repos.sonar.digitalocean.com main/main Translation-en_US
Get:4 https://repos.sonar.digitalocean.com main/main Translation-en            
Get:5 https://repos.sonar.digitalocean.com main/main Translation-en_US         
Get:6 https://repos.sonar.digitalocean.com main/main Translation-en            
Get:7 https://repos.sonar.digitalocean.com main/main Translation-en_US         
Get:8 https://repos.sonar.digitalocean.com main/main Translation-en            
Get:9 https://repos.sonar.digitalocean.com main/main Translation-en_US         
Get:10 https://repos.sonar.digitalocean.com main/main Translation-en           
Get:11 https://repos.sonar.digitalocean.com main/main Translation-en_US        
Ign https://repos.sonar.digitalocean.com main/main Translation-en_US           
Get:12 https://repos.sonar.digitalocean.com main/main Translation-en           
Ign https://repos.sonar.digitalocean.com main/main Translation-en              
100% [Waiting for headers]   
```

---

### Post by oldos2er on 2017-12-26
Have you tried a different mirror?

---

### Post by micahpage on 2017-12-28
How would you switch mirrors?

---

### Post by vasa1 on 2017-12-28
With Synaptic Package Manager or whatever GUI you have on your system? Mine looks like this:

---

