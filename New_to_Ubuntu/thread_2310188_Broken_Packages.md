---
title: "Broken Packages"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by Spencer_Thompson on 2016-01-16
Hello! I recently had a scheduled update from the package manager and when it was about to finish updating, the updater quit responding. I waited for it to start responding again until it recommended I force closed it. Now whenever I try to update, an error message pops up saying "Package dependencies cannot be resolved. This error could could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time." Also, whenever I try to upgrade from the terminal, it says that 4 packages are being held back: gcc-4.9-base, gcc-4.9-base:i386, libgcc1, and libgcc1:i386. I think these packages are causing the error but I don't know how to fix these broken packages.

---

### Post by ian-weisser on 2016-01-16
Which release of Ubuntu are you running? 12.04? 14.04? 15.10?

Please copy-and-paste the complete output of a terminal session here.
Please use ```
 tags to preserve the formatting.
[code]sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Spencer_Thompson on 2016-01-17
I am running Ubuntu 14.04.

```
~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://repository.spotify.com stable InRelease                             
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [248 kB]        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:3 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B] 
Get:4 http://us.archive.ubuntu.com trusty-updates/universe Sources [147 kB]    
Hit http://ppa.launchpad.net trusty/main Sources                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,161 B] 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:6 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [683 kB] 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:7 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [334 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Translation-en                       
Hit http://ppa.launchpad.net trusty/main Sources                               
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [659 kB] 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                      
Hit http://ppa.launchpad.net trusty/main Translation-en                     
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                      
Hit http://ppa.launchpad.net trusty/main Translation-en                     
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [336 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2,539 kB in 8s (288 kB/s)                                              
Reading package lists... Done
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 libgcc1 libgcc1:i386
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

---

### Post by ian-weisser on 2016-01-17
Not seeing any dependency problems.
Not seeing any broken packages.

Seeing four kept-back packages. Try:
```
sudo apt-get dist-upgrade
```

---

### Post by Spencer_Thompson on 2016-01-17
I tried the command and came up with this.

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.20.3-0ubuntu1.2)
        Depends: gvfs-daemons (< 1.20.3-0ubuntu1.2.1~)
 indicator-network : Depends: unity8 (>= 7.82) but it is not going to be installed
 libdbus-cpp2 : Depends: libprocess-cpp1 (>= 1.0.0+14.04.20140326.2) but it is not going to be installed
 libqt5gui5 : Depends: libegl1-mesa (>= 7.8.1) or
                       libegl1-x11
              Depends: libgbm1 (>= 8.1~0) but it is not going to be installed
 libstdc++6 : Depends: gcc-4.9-base (= 4.9.2-0ubuntu1~14.04) but 4.9.3-0ubuntu4 is to be installed
 libubuntu-application-api-mirserver1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140408.1) but it is not going to be installed
                                        Depends: libubuntu-location-service0 but it is not going to be installed
 libubuntu-application-api1 : Depends: libubuntu-location-service0 but it is not going to be installed
 libunity-mir1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140411) but it is not going to be installed
                 Depends: libprocess-cpp1 (>= 1.0.0+14.04.20140326.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Internal error, Upgrade broke stuff
```

---

### Post by ian-weisser on 2016-01-17
I see your system trying to install two different versions of libmirserver18.
Perhaps you are getting Unity 8 from multiple sources?

If so, uninstall all Unity 8 packages, disable the PPA, clear your local package cache, then reinstall Unity 8.

---

### Post by Spencer_Thompson on 2016-01-17
I'm still fairly new to Ubuntu. Would you care to tell me the commands to type into the terminal to uninstall all Unity 8 packages?

---

### Post by ian-weisser on 2016-01-17
Try:
```
sudo apt remove unity8
sudo apt-get autoremove
```

That should remove a bunch of packages. If it doesn't, then stop and post the output here.

If it works, run the command 'sudo apt-get clean' to clear your local package  cache of all stored packages, including those pesky  unity8-and-dependencies, so conflicting versions dont get reinstalled  erroneously.

Then, the next step is to edit your software sources, and disable whatever PPA you added to try Unity 8.

Then, rebuild your packgage database using the new sources, so you don't re-download conflicting packages from that source.

Finally, try another 'sudo apt-get dist-upgrade' to see if the problem is fixed...or if something else needs to be removed. If there are still errors, post the output here.


PPAs and non-Ubuntu sources are great ways to test new software...but it means you're a tester, and cutting-edge software occasionally causes testers to bleed.
PPAs are not stable, supported software. They cause conflicts. They have bugs. You need to know how to troubleshoot and file useful bugs, and how to resolve simple package conflicts. Not ideal for beginners.

---

### Post by Spencer_Thompson on 2016-01-18
Without waiting for a response, I checked to see if Unity 8 was installed in the software center and it wasn't. So I installed it and attempted to upgrade the packages with "sudo apt-get dist-install" and it asked me for confirmation of upgrading them. But I noticed it wanted to remove 500 packages. I confirmed the upgrade anyway and noticed all my programs were being removed. I waited it out, thinking it was just refreshing and reinstalling them. But I came to a black screen, like a terminal, but I couldn't do anything. I restarted and came to an endless loading screen of Ubuntu. I had to reinstall Ubuntu from disk and lost all my files. I luckily had the important files stored on a flashdrive, but I regret trying to upgrade them without asking for help. Thank you for attempting to help me but in the end, I took a risk and lost. Have a nice day!

---

