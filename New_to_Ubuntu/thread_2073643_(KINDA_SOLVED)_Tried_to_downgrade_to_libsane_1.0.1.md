---
title: "(KINDA SOLVED) Tried to downgrade to libsane 1.0.15-9 FAIL (FIXED BY MYSELF!!!!)"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by mklez on 2012-10-20
Hey guys,

I am new to Ubuntu but used it in the past here and there. I am now looking to make it my primary OS. I have a CanoScan N650U that was making a grinding noise when I was using it. I tried to downgrade to libsane 1.0.15-9. And to be honest; my package manage no longer works.

Im running Ubuntu 12.04 LTS 64bit

Heres what I tried: Please forgive me if some of the codes are redundant.


Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@michael-desktop:~$ sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try using -f.
michael@michael-desktop:~$ sudo apt-get remove libsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsane is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-desktop:~$ sudo apt-get remove sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sane-utils is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-desktop:~$ apt-get remove sane-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-desktop:~$ sudo apt-get remove sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sane-utils is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-desktop:~$ sudo apt-get remove sane-utils -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sane-utils is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-desktop:~$ apt-get remove sane-utilsapt-get remove --purge sane-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-desktop:~$ apt-get remove --purge sane-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-desktop:~$ sudo apt-get remove --purge sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-desktop:~$ sudo su
root@michael-desktop:/home/michael# apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [178 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,395 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [60.2 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,745 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [405 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,215 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [149 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,948 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [410 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,218 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [149 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,930 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [15.8 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [14.5 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [14.5 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
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
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                   
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US    
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Fetched 1,553 kB in 6s (240 kB/s)                                              
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@michael-desktop:/home/michael# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not installed
                Recommends: hotplug:i386 but it is not installable
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
root@michael-desktop:/home/michael# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic gimp-help-common
  gimp-help-en libjpeg62:i386 libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@michael-desktop:/home/michael# sudo apt-get remove sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sane-utils is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@michael-desktop:/home/michael# sudo apt-get install sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
 sane-utils : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@michael-desktop:/home/michael# sudo apt-get -f install sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
 sane-utils : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@michael-desktop:/home/michael# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic gimp-help-common
  gimp-help-en libjpeg62:i386 libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@michael-desktop:/home/michael# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try using -f.
root@michael-desktop:/home/michael# sudo apt-get remove xsane sane-utils sane iscan iscan-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package iscan
E: Unable to locate package iscan-data
root@michael-desktop:/home/michael# sudo apt-get install sane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
 sane : Depends: libgimp2.0 (>= 2.4.0) but it is not going to be installed
        Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@michael-desktop:/home/michael# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic gimp-help-common
  gimp-help-en libjpeg62:i386 libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@michael-desktop:/home/michael# sudo apt-get install sane-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sane-extras
root@michael-desktop:/home/michael# sudo apt-get install sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not going to be installed
                Recommends: hotplug:i386 but it is not installable
 sane-utils : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@michael-desktop:/home/michael# try apt-get -f install
No command 'try' found, did you mean:
 Command 'tty' from package 'coreutils' (main)
 Command 'tr' from package 'coreutils' (main)
 Command 'trn' from package 'trn' (multiverse)
 Command 'trn' from package 'trn4' (multiverse)
 Command 'trs' from package 'konwert' (main)
try: command not found
root@michael-desktop:/home/michael# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic gimp-help-common
  gimp-help-en libjpeg62:i386 libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@michael-desktop:/home/michael# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try using -f.
root@michael-desktop:/home/michael# ^C
root@michael-desktop:/home/michael# ^C
root@michael-desktop:/home/michael# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: sane-utils:i386 (>= 1.0.15-9ubuntu6) but it is not installed
                Recommends: hotplug:i386 but it is not installable
E: Unmet dependencies. Try using -f.
root@michael-desktop:/home/michael# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic gimp-help-common
  gimp-help-en libjpeg62:i386 libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following packages will be upgraded:
  libsane:i386
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 1,253 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on sane-utils (>= 1.0.15-9ubuntu6).
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@michael-desktop:/home/michael#

---

### Post by mklez on 2012-10-20
Fixed on my own!

I went into the terminal sudo gedit /var/lib/dpkg/status and removed some info there.

It took 2 hours to fix but I am damn near proud of myself. Anyone know how to stop the grinding noise? I see a bug is open but some success or none?

---

