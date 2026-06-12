---
title: "errors caused by bad/old packages, HELP!!"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by TooRight on 2012-08-21
I'm having issues installing programs because of package errors I have been getting, it seems to boil down to these being the offending entries...please tell me what to type in terminal to get rid of these errors!!

```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by NikTh on 2012-08-21
Hi , 
please open a terminal and give the results of these commands 

```
cat /etc/lsb-release && uname -r 
cat /etc/apt/sources.list 
ls /etc/apt/sources.list.d/
```
also post full output of 
```
sudo apt-get update
```
Thanks

---

### Post by critin on 2012-08-21
Canonical has archived Jaunty Binaries to a new area,

[http://www.newit.co.uk/forum/index.php?topic=2329.0](http://www.newit.co.uk/forum/index.php?topic=2329.0)

Instructions are on the page.

---

### Post by TooRight on 2012-08-21
Thank you so much for your quick response!, here are the outputs:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
3.2.0-29-generic

```

and

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ precise restricted main
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates restricted main
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://security.ubuntu.com/ubuntu precise-security restricted main
deb-src http://security.ubuntu.com/ubuntu precise-security restricted multiverse universe main #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
# deb http://extras.ubuntu.com/ubuntu precise main #Third party developers repository
deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports restricted multiverse universe main
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports restricted multiverse universe main #Added by software-properties
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ precise universe
deb-src http://ubuntu.mirror.cambrium.nl/ubuntu/ precise universe #Added by software-properties
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ precise universe
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-proposed restricted multiverse universe main
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-proposed restricted multiverse universe main #Added by software-properties

```

and

```
ferramroberto-java-natty.list              google-talkplugin.list.save
ferramroberto-java-natty.list.distUpgrade  medibuntu.list
ferramroberto-java-natty.list.save         medibuntu.list.distUpgrade
google-chrome.list                         medibuntu.list.save
google-chrome.list.distUpgrade             natty-partner.list
google-chrome.list.save                    natty-partner.list.distUpgrade
google-talkplugin.list                     natty-partner.list.save
google-talkplugin.list.distUpgrade

```

and the update results:
```
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release                                      
Get:4 http://dl.google.com stable Release                                      
Get:5 http://dl.google.com stable/main i386 Packages [1,227 B]                 
Ign http://ubuntu.mirror.cambrium.nl precise InRelease                         
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://ca.archive.ubuntu.com precise InRelease                             
Ign http://ca.archive.ubuntu.com precise-updates InRelease                     
Ign http://ca.archive.ubuntu.com jaunty-backports InRelease                    
Ign http://ca.archive.ubuntu.com precise-backports InRelease                   
Ign http://ca.archive.ubuntu.com precise-proposed InRelease                    
Get:6 http://dl.google.com stable/main i386 Packages [770 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ubuntu.mirror.cambrium.nl precise Release.gpg                       
Hit http://archive.canonical.com precise Release.gpg                           
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://ca.archive.ubuntu.com precise Release.gpg                           
Hit http://ubuntu.mirror.cambrium.nl precise Release                           
Hit http://archive.canonical.com precise Release                               
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:9 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://ca.archive.ubuntu.com jaunty-backports Release.gpg                  
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://ubuntu.mirror.cambrium.nl precise/universe Sources                  
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://dl.google.com stable/main Translation-en_CA                         
Get:10 http://ca.archive.ubuntu.com precise-proposed Release.gpg [198 B]       
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ubuntu.mirror.cambrium.nl precise/universe i386 Packages            
Hit http://ubuntu.mirror.cambrium.nl precise/universe TranslationIndex         
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ca.archive.ubuntu.com precise Release                               
Get:11 http://ca.archive.ubuntu.com precise-updates Release [49.6 kB]          
Hit http://ubuntu.mirror.cambrium.nl precise/universe Translation-en_CA        
Hit http://packages.medibuntu.org oneiric InRelease                            
Get:12 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Hit http://ubuntu.mirror.cambrium.nl precise/universe Translation-en           
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [11.1 kB]  
Get:15 http://security.ubuntu.com precise-security/main Sources [40.6 kB]      
Ign http://ca.archive.ubuntu.com jaunty-backports Release                      
Hit http://ca.archive.ubuntu.com precise-backports Release                     
Get:16 http://ca.archive.ubuntu.com precise-proposed Release [49.6 kB]         
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [161 kB] 
Hit http://ca.archive.ubuntu.com precise/restricted Sources                    
Hit http://ca.archive.ubuntu.com precise/multiverse Sources                    
Hit http://ca.archive.ubuntu.com precise/universe Sources                      
Hit http://ca.archive.ubuntu.com precise/main Sources                          
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com precise/main i386 Packages                    
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages                
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://ca.archive.ubuntu.com jaunty-backports/main TranslationIndex        
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse TranslationIndex  
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted TranslationIndex  
Ign http://ca.archive.ubuntu.com jaunty-backports/universe TranslationIndex    
Get:19 http://ca.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:20 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:21 http://ca.archive.ubuntu.com precise-updates/universe Sources [48.5 kB] 
Get:22 http://security.ubuntu.com precise-security/universe i386 Packages [41.0 kB]
Get:23 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:24 http://ca.archive.ubuntu.com precise-updates/main Sources [158 kB]      
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://archive.canonical.com precise/partner Translation-en                
Get:25 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:26 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [377 kB]
Hit http://packages.medibuntu.org oneiric/free Sources                         
Hit http://packages.medibuntu.org oneiric/non-free Sources
Get:27 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [124 kB]
Get:28 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ca.archive.ubuntu.com precise-backports/main Sources                
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:29 http://ca.archive.ubuntu.com precise-proposed/restricted Sources [14 B] 
Get:30 http://ca.archive.ubuntu.com precise-proposed/multiverse Sources [14 B] 
Get:31 http://ca.archive.ubuntu.com precise-proposed/universe Sources [3,703 B]
Get:32 http://ca.archive.ubuntu.com precise-proposed/main Sources [52.7 kB]    
Get:33 http://ca.archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:34 http://ca.archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:35 http://ca.archive.ubuntu.com precise-proposed/universe i386 Packages [8,938 B]
Get:36 http://ca.archive.ubuntu.com precise-proposed/main i386 Packages [130 kB]
Hit http://ca.archive.ubuntu.com precise-proposed/main TranslationIndex        
Hit http://ca.archive.ubuntu.com precise-proposed/multiverse TranslationIndex  
Hit http://ca.archive.ubuntu.com precise-proposed/restricted TranslationIndex  
Hit http://ca.archive.ubuntu.com precise-proposed/universe TranslationIndex    
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com precise/main Translation-en                   
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com precise/universe Translation-en               
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA        
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA    
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://ca.archive.ubuntu.com precise-proposed/main Translation-en_CA       
Hit http://ca.archive.ubuntu.com precise-proposed/main Translation-en          
Hit http://ca.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com precise-proposed/restricted Translation-en    
Hit http://ca.archive.ubuntu.com precise-proposed/universe Translation-en_CA   
Hit http://ca.archive.ubuntu.com precise-proposed/universe Translation-en      
Err http://ca.archive.ubuntu.com jaunty-backports/main i386 Packages           
  404  Not Found [IP: 91.189.92.190 80]
Err http://ca.archive.ubuntu.com jaunty-backports/restricted i386 Packages     
  404  Not Found [IP: 91.189.92.190 80]
Err http://ca.archive.ubuntu.com jaunty-backports/universe i386 Packages       
  404  Not Found [IP: 91.189.92.190 80]
Err http://ca.archive.ubuntu.com jaunty-backports/multiverse i386 Packages     
  404  Not Found [IP: 91.189.92.190 80]
Ign http://ca.archive.ubuntu.com jaunty-backports/main Translation-en_CA       
Ign http://ca.archive.ubuntu.com jaunty-backports/main Translation-en          
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Translation-en_CA 
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Translation-en    
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Translation-en_CA 
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Translation-en    
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Translation-en_CA   
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Translation-en      
Ign http://packages.medibuntu.org precise/free Translation-en_CA               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_CA           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Fetched 1,344 kB in 13s (101 kB/s)                                             
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.190 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by critin on 2012-08-21
umm, I thought you were running Jaunty...

---

### Post by TooRight on 2012-08-21
it's a mess!! :(

---

### Post by oldfred on 2012-08-21
It looks like this is the only referenece to Jaunty.

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR=Red]deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse[/COLOR]
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

```

Delete or comment out that line.
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

---

### Post by NikTh on 2012-08-21
Hi ,
**first of all do as @oldfred said. **
Then , I think apt reads from /etc/apt/sources.list.d/ also.. so delete some lines are reference to natty (Ubuntu 11.04) 
```
sudo rm /etc/apt/sources.list.d/ferramroberto-*
sudo rm /etc/apt/sources.list.d/natty-partner*
``` 

Then do again 
```
sudo apt-get update
``` and see if errors occurs . If not , then I think your problem solved.
Thanks

---

