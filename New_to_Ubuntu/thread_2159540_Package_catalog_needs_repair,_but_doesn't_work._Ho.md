---
title: "Package catalog needs repair, but doesn't work. How can I fix this?"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by Punkinhead on 2013-07-03
I cannot install or uninstall anything because the package catalog needs repair, according to SoftwareManager. When I click the repair button I get this error message:

```
   wine1.6-i386:i386 depends on wine1.6:any (= 1.6~rc2-0ubuntu1~ppa4); however:  Package wine1.6 is not configured yet.
dpkg: error processing wine1.6-i386:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-i386:i386:
 wine1.5-i386:i386 depends on wine1.6-i386; however:
  Package wine1.6-i386:i386 is not confiNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
gured yet.
dpkg: error processing wine1.5-i386:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.6
 wine1.6-amd64
 wine
 wine1.6-i386:i386
 wine1.5-i386:i386
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa4); however:
  Version of wine1.6-amd64 on system is 1.6~rc4-0ubuntu1.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1.6~rc4-0ubuntu1); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa4.
dpkg: error processing wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-i386:i386:
 wine1.6-i386:i386 depends on wine1.6:any (= 1.6~rc2-0ubuntu1~ppa4); however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine1.6-i386:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-i386:i386:
 wine1.5-i386:i386 depends on wine1.6-i386; however:
  Package wine1.6-i386:i386 is not configured yet.
dpkg: error processing wine1.5-i386:i386 (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by wildmanne39 on 2013-07-03
Please use code tags.

---

### Post by Punkinhead on 2013-07-03
> [COLOR=#000000]Please use code tags.[/COLOR]

Gotcha. Sorry about that.

---

### Post by Punkinhead on 2013-07-03
I think that I need to reinstall Wine, but I don't know how with this package catalog problem. Originally, I installed Ubuntu 9.04 and upgraded until I got to 12.04. This was all about a month ago and I had to perform some amateur repository meddling to get the old Ubuntu releases installed. I think somewhere along the line my installed packages got messed up. At this point, it is all over my head. And when did Ubuntu become such a resource hog? I used 9.04 a few years ago and it performed better than WinXP! My games had better framerates, booting was faster, etc. Now I feel like Ubuntu has lost that edge to Windows 8. I abhor Windows 8, but I need it if I'm to get decent performance out of this PC of mine.

---

### Post by aktiwers on 2013-07-03
Remove Wine completely and update the repos
```

sudo apt-get purge wine1* 
sudo apt-get purge wine
sudo apt-get autoremove
sudo apt-get install -f
sudo apt-get update

```

Did that fix it?

---

### Post by Punkinhead on 2013-07-04
Thank for the help, aktiwers! I tried the code you gave me and here's what I got. After all of this in the terminal, I opened software center and it's still having the same problem. 

```
isaac@isaac-laptop:~$ sudo apt-get purge wine1*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'wine1.6-amd64' for regex 'wine1*'
Note, selecting 'arc-wine' for regex 'wine1*'
Note, selecting 'winefish' for regex 'wine1*'
Note, selecting 'wine1.3-gecko' for regex 'wine1*'
Note, selecting 'wine1.4-amd64' for regex 'wine1*'
Note, selecting 'wine-gecko' for regex 'wine1*'
Note, selecting 'wine1.5-i386' for regex 'wine1*'
Note, selecting 'wine1.0' for regex 'wine1*'
Note, selecting 'wine1.2' for regex 'wine1*'
Note, selecting 'wine1.3' for regex 'wine1*'
Note, selecting 'wine1.4' for regex 'wine1*'
Note, selecting 'wine1.5' for regex 'wine1*'
Note, selecting 'wine1.6' for regex 'wine1*'
Note, selecting 'wine1.6-dbg' for regex 'wine1*'
Note, selecting 'wine1.6-dev' for regex 'wine1*'
Note, selecting 'q4wine-unstable' for regex 'wine1*'
Note, selecting 'wine-mono0.0.4' for regex 'wine1*'
Note, selecting 'wine-mono0.0.8' for regex 'wine1*'
Note, selecting 'libkwineffects1abi3' for regex 'wine1*'
Note, selecting 'gnome-wine-icon-theme' for regex 'wine1*'
Note, selecting 'wine1.4:any' for regex 'wine1*'
Note, selecting 'wine-i386' for regex 'wine1*'
Note, selecting 'wine1.4-common' for regex 'wine1*'
Note, selecting 'wine-gecko2.21' for regex 'wine1*'
Note, selecting 'wine-gecko1.4' for regex 'wine1*'
Note, selecting 'wine-gecko1.5' for regex 'wine1*'
Note, selecting 'wine-gecko1.6' for regex 'wine1*'
Note, selecting 'wine-gecko1.7' for regex 'wine1*'
Note, selecting 'wine-gecko1.8' for regex 'wine1*'
Note, selecting 'wine-gecko1.9' for regex 'wine1*'
Note, selecting 'winetricks' for regex 'wine1*'
Note, selecting 'wine-mono' for regex 'wine1*'
Note, selecting 'wine-bin' for regex 'wine1*'
Note, selecting 'wine1.5-amd64' for regex 'wine1*'
Note, selecting 'wine-dev' for regex 'wine1*'
Note, selecting 'wine-bin-unstable' for regex 'wine1*'
Note, selecting 'wine1.4-dbg' for regex 'wine1*'
Note, selecting 'wine1.4-dev' for regex 'wine1*'
Note, selecting 'q4wine' for regex 'wine1*'
Note, selecting 'wine1.2-gecko' for regex 'wine1*'
Note, selecting 'wine' for regex 'wine1*'
Note, selecting 'wine1.6-i386' for regex 'wine1*'
Note, selecting 'wine-amd64' for regex 'wine1*'
Note, selecting 'wine1.5:any' for regex 'wine1*'
Note, selecting 'wine1.4-i386' for regex 'wine1*'
Note, selecting 'wine-unstable' for regex 'wine1*'
Note, selecting 'wine1.5-dbg' for regex 'wine1*'
Note, selecting 'wine1.5-dev' for regex 'wine1*'
Note, selecting 'shiki-wine-theme' for regex 'wine1*'
Note, selecting 'ttf-symbol-replacement-wine1.3' for regex 'wine1*'
Note, selecting 'wine1.6:any' for regex 'wine1*'
Note, selecting 'wine1.4' instead of 'wine1.4:any'
Note, selecting 'wine1.5' instead of 'wine1.5:any'
Note, selecting 'wine1.6-i386:i386' instead of 'wine1.6-i386'
Note, selecting 'wine1.6' instead of 'wine1.6:any'
Package gnome-wine-icon-theme is not installed, so not removed
Package q4wine is not installed, so not removed
Package shiki-wine-theme is not installed, so not removed
Package winefish is not installed, so not removed
Package libkwineffects1abi3 is not installed, so not removed
Package wine1.2 is not installed, so not removed
Package wine1.3 is not installed, so not removed
Package wine1.4-dev is not installed, so not removed
Package wine1.4-dbg is not installed, so not removed
Package wine1.4-common is not installed, so not removed
Package wine1.5-dev is not installed, so not removed
Package wine1.5-dbg is not installed, so not removed
Package wine-gecko1.5 is not installed, so not removed
Package wine-gecko1.6 is not installed, so not removed
Package wine-gecko1.7 is not installed, so not removed
Package wine-mono0.0.4 is not installed, so not removed
Package wine-gecko1.8 is not installed, so not removed
Package wine1.6-dev is not installed, so not removed
Package wine1.6-dbg is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
 wine1.6-i386:i386 : Depends: wine1.6:any:i386 (= 1.6~rc2-0ubuntu1~ppa4)
                     Recommends: wine-mono0.0.8:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
isaac@isaac-laptop:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa4) but 1.6~rc4-0ubuntu1 is to be installed
 wine1.6-amd64 : Depends: wine1.6:any (= 1.6~rc4-0ubuntu1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
isaac@isaac-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa4) but 1.6~rc4-0ubuntu1 is installed
 wine1.6-amd64 : Depends: wine1.6:any (= 1.6~rc4-0ubuntu1)
E: Unmet dependencies. Try using -f.
isaac@isaac-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  wine-gecko1.9:i386 linux-image-3.2.0-44-generic
  linux-backports-modules-cw-3.6-3.2.0-44-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6 wine1.6-i386:i386
Suggested packages:
  dosbox:any
The following packages will be upgraded:
  wine1.6 wine1.6-i386:i386
2 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
5 not fully installed or removed.
Need to get 0 B/25.8 MB of archives.
After this operation, 573 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa4); however:
  Version of wine1.6-amd64 on system is 1.6~rc4-0ubuntu1.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1.6~rc4-0ubuntu1); however:
No apport report written because the error message indicates its a followup error from a previous failure.
                            Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa4.
dpkg: error processing wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-i386:i386:
 wine1.6-i386:i386 depends on wine1.6:any (= 1.6~rc2-0ubuntu1~ppa4); however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine1.6-i386:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of wine1.5-i386:i386:
 wine1.5-i386:i386 depends on wine1.6-i386; however:
  Package wine1.6-i386:i386 is not configured yet.
dpkg: error processing wine1.5-i386:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.6
 wine1.6-amd64
 wine
 wine1.6-i386:i386
 wine1.5-i386:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
isaac@isaac-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://apt.insynchq.com](http://apt.insynchq.com) precise Release.gpg                                
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://apt.insynchq.com](http://apt.insynchq.com) precise Release                            
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [77.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [208 kB]
Hit [http://apt.insynchq.com](http://apt.insynchq.com) precise/non-free amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [295 kB] 
Hit [http://apt.insynchq.com](http://apt.insynchq.com) precise/non-free i386 Packages                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [645 kB]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Ign [http://apt.insynchq.com](http://apt.insynchq.com) precise/non-free TranslationIndex                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,182 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [79.8 kB]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [310 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [211 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [664 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,367 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Ign [http://apt.insynchq.com](http://apt.insynchq.com) precise/non-free Translation-en_US                 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [297 kB]
Ign [http://apt.insynchq.com](http://apt.insynchq.com) precise/non-free Translation-en                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                 
  404  Not Found
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US        
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 2,960 kB in 22s (133 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Sorry it's so much code, but I don't know enough to pick out the relevant bits for you. I really appreciate your time and effort here.

---

### Post by Impavidus on 2013-07-04
> **Punkinhead said:**
> ...
And when did Ubuntu become such a resource hog? I used 9.04 a few years ago and it performed better than WinXP!
...

Since 11.04 I think. The biggest resource hug is the desktop environment. For older machines Xubuntu, with the xfce DE, is more suited. Default Ubuntu is slower than Win XP, which is not surprising given that XP is a decade old. I can't compare to more recent windowses, as I never tried them, but I think they have become slower too.

---

### Post by aktiwers on 2013-07-06
Do  you still use Playonlinux?

To fix this you need to remove everything that has to do with Wine, so:
```
sudo apt-get remove playonlinux
sudo apt-get purge wine1*
sudo apt-get purge wine
sudo apt-get autoremove
sudo apt-get install -f
sudo apt-get update

```

If you want playonlinux back, install it when the repos are fixed again.

Hope it works

---

### Post by Punkinhead on 2013-07-06
Alas...
Do I need to install a dependency before I can uninstall playonlinux?

```
isaac@isaac-laptop:~$ sudo apt-get remove playonlinux
[sudo] password for isaac: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa4) but 1.6~rc4-0ubuntu1 is to be installed
 wine1.6-amd64 : Depends: wine1.6:any (= 1.6~rc4-0ubuntu1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by aktiwers on 2013-07-07
Yes please try it - and try this:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update

```

---

