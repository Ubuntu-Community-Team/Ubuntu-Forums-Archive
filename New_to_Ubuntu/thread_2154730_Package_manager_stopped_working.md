---
title: "Package manager stopped working"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by tinyafair on 2013-06-15
When I downloaded Ubuntu, and installed it. I did an update that changed everything to Edubuntu. After that, my package manager stopped working. I don't know why, or how. Its annoying because I wish to play games on my laptop, when I'm unable to get internet through Wifi.
This is the errors that I get when I try to do Sudo apt-get update
```

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed Release.gpg [198 B]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [80.2 kB]       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed Release [49.6 kB]          
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages                    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [25.9 kB]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,383 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex           
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [290 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [396 kB]      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [75.5 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,182 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [306 kB] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [78.2 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,367 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_CA           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [396 kB]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources [90.6 kB] 
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources [6,571 B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main amd64 Packages [637 kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe amd64 Packages [206 kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [657 kB]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [209 kB]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted amd64 Packages [14 B]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main amd64 Packages [73.4 kB]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main amd64 Packages [73.4 kB]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse amd64 Packages [2,055 B]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe amd64 Packages [18.0 kB]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted i386 Packages [14 B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main i386 Packages [81.3 kB]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [2,054 B]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe i386 Packages [20.5 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe TranslationIndex    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main Translation-en_CA       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe Translation-en      
Fetched 3,407 kB in 3min 15s (17.5 kB/s)                                       
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
 This is the list for ksudo gedit /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-proposed restricted main multiverse universe

```
I am new to Edubuntu, so I'm unable to fix this on my own. If possible, if you could do baby steps that would be great.

---

### Post by Frogs Hair on 2013-06-15
> [COLOR=#000000]When I downloaded Ubuntu, and installed it. I did an update that changed everything to Edubuntu.  Can you give some details ? Did you install the Edubuntu Desktop ? [/COLOR]


I also see a duplicate sources warning . 

```
[COLOR=#000000]W: Duplicate sources.list entry [/COLOR][http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/)[COLOR=#000000] precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-amd64_Packages)[/COLOR]
[COLOR=#000000]W: Duplicate sources.list entry [/COLOR][http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/)[COLOR=#000000] precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-i386_Packages)[/COLOR]
[COLOR=#000000]W: You may want to run apt-get update to correct these problems[/COLOR]
[COLOR=#000000]This is the list for ksudo gedit /etc/apt/sources.list[/COLOR]
```

[http://askubuntu.com/questions/183007/how-to-fix-duplicate-sources-list-entry-warning](http://askubuntu.com/questions/183007/how-to-fix-duplicate-sources-list-entry-warning)
[http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry](http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry)
[http://askubuntu.com/questions/156227/duplicate-sources-list-entry-but-cannot-find-the-duplicates](http://askubuntu.com/questions/156227/duplicate-sources-list-entry-but-cannot-find-the-duplicates)

---

### Post by tinyafair on 2013-06-15
The only thing i did was download the packages that needed to be downloaded. Perhaps there was an error that gave me the Edubuntu desktop, i dont know.

---

