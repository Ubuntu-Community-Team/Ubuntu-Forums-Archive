---
title: "Package dependencies cannot be resolved/broken packages"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by techtakular on 2012-06-25
Why are package dependencies broken after failed upgrade to 12.04? 

it started out as 9.10, I updated to 10.04(but then at the same time  it updated to 12.04(which doesn't work and I don't know how to fix that,  its a graphics error or something))
  but I'm just trying to get vlc media player in 10.4, or the  restricted codecs to work but I can not because either in the terminal  or USC it says broken packages/ Package dependencies cannot be resolved  I've updated as much as I can yet this still persists what gives? what  can I do?

---

### Post by oldos2er on 2012-06-25
Can you post your sources.list? ```
cat /etc/apt/sources.list
``` and also the output from this command ```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by techtakular on 2012-06-25
desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)]/ lucid main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic restricted universe multiverse
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic universe karmic [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) deb-src #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic-updates restricted universe multiverse
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic-updates restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic-security restricted universe multiverse
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic-security restricted universe #Added by software-properties
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) karmic deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe multiverse

and 

 	Code:
 	sudo apt-get update && sudo apt-get install vlc 


Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/restricted Sources    
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/universe Sources      
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/main Sources                   
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/restricted Sources             
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/restricted Packages            
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/universe Packages              
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/multiverse Packages            
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/universe Sources               
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/karmic Sources                 
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/http://old-releases.ubuntu.com/ubuntu/ Sources
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/deb-src Sources                
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/deb-src Packages               
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/http://old-releases.ubuntu.com/ubuntu/ Packages
  404  Not Found
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/karmic Packages                
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic/main Packages                
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-updates/restricted Packages  
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-updates/universe Packages    
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-updates/multiverse Packages  
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-updates/restricted Sources   
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-updates/universe Sources     
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/restricted Packages 
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/universe Packages     
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/multiverse Packages   
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/restricted Sources    
  404  Not Found
Err [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) karmic-security/universe Sources      
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources              
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
  404  Not Found
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [180kB]              
Fetched 5,685kB in 11s (501kB/s)                                               
W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz](http://us.old-releases.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/main/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/restricted/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/universe/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/karmic/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/karmic/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/http://old-releases.ubuntu.com/ubuntu//source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/http://old-releases.ubuntu.com/ubuntu//source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/deb-src/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/deb-src/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/deb-src/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/deb-src/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/http://old-releases.ubuntu.com/ubuntu//binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/http://old-releases.ubuntu.com/ubuntu//binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/karmic/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/karmic/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by NikTh on 2012-06-25
Hi , 
give the result of 
```
uname -a
```

---

### Post by techtakular on 2012-06-25
desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by NikTh on 2012-06-25
Give these commands in terminal one at time , and give results of the last. 

```
sudo rm /etc/apt/sources.list.d/*.list
sudo wget "http://pastebin.com/raw.php?i=tjNrr3dF" -O /etc/apt/sources.list
sudo apt-get update
```

---

### Post by techtakular on 2012-06-25
-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [57.3kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [417kB]       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages [2,855B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [131kB]   
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages [5,370B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [124kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources [1,259B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [40.8kB]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources [2,316B] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [617kB]        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B] 
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [270kB]    
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [223kB]         
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]  
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [101kB]     
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,818B]  
Fetched 13.1MB in 9s (1,344kB/s)                                               
Reading package lists... Done

---

### Post by NikTh on 2012-06-25
give results of this command
```
sudo apt-get install -f
```

---

### Post by techtakular on 2012-06-25
-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by NikTh on 2012-06-25
```
sudo apt-get upgrade
``` and i think your problem with packages and updates Solved.

**Info:**
If you want to change server for updates , go to Update manager > settings > ubuntu software and Download From : change it with your country . 
I gave you us (united states) server.

---

### Post by techtakular on 2012-06-25
thanks so much! Btw I'm at the Configuring ttf-mscorefonts-installer and I can not click ok or  enter to go forward :/

---

### Post by NikTh on 2012-06-25
> **techtakular said:**
> thanks so much! Btw I'm at the Configuring ttf-mscorefonts-installer and I can not click ok or  enter to go forward :/

Use Tab button and Enter. 

Also check the** info** in my previous post.

**And mark thread as Solved (from thread tools) **
Thanks

---

