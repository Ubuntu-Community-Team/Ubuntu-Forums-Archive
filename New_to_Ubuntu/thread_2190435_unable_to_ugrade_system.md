---
title: "unable to ugrade system"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by micahpage on 2013-11-27
I am not sure what the output of this means, but i am unable to moe past update on to upgrade because of it?

```
sondra@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/main/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) dists/precise/restricted/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1) precise/restricted Translation-en
Hit http://mirrors.gigenet.com precise Release.gpg                             
Hit http://mirrors.gigenet.com precise-updates Release.gpg                     
Hit http://mirrors.gigenet.com precise-backports Release.gpg                   
Hit http://mirrors.gigenet.com precise-security Release.gpg                    
Hit http://mirrors.gigenet.com precise Release                                 
Hit http://mirrors.gigenet.com precise-updates Release                         
Hit http://mirrors.gigenet.com precise-backports Release                       
Hit http://mirrors.gigenet.com precise-security Release                        
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirrors.gigenet.com precise/main Sources                            
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirrors.gigenet.com precise/restricted Sources                      
Hit http://mirrors.gigenet.com precise/universe Sources                        
Hit http://mirrors.gigenet.com precise/multiverse Sources                      
Hit http://mirrors.gigenet.com precise/main amd64 Packages                     
Hit http://mirrors.gigenet.com precise/restricted amd64 Packages               
Hit http://mirrors.gigenet.com precise/universe amd64 Packages                 
Hit http://mirrors.gigenet.com precise/multiverse amd64 Packages               
Hit http://mirrors.gigenet.com precise/main i386 Packages                      
Hit http://mirrors.gigenet.com precise/restricted i386 Packages                
Hit http://mirrors.gigenet.com precise/universe i386 Packages        
Hit http://mirrors.gigenet.com precise/multiverse i386 Packages      
Hit http://mirrors.gigenet.com precise/main TranslationIndex         
Hit http://mirrors.gigenet.com precise/multiverse TranslationIndex             
Hit http://mirrors.gigenet.com precise/restricted TranslationIndex             
Hit http://dl.google.com stable Release                                        
Hit http://mirrors.gigenet.com precise/universe TranslationIndex               
Hit http://mirrors.gigenet.com precise-updates/main Sources                    
Hit http://mirrors.gigenet.com precise-updates/restricted Sources              
Hit http://mirrors.gigenet.com precise-updates/universe Sources                
Hit http://mirrors.gigenet.com precise-updates/multiverse Sources    
Hit http://mirrors.gigenet.com precise-updates/main amd64 Packages   
Hit http://mirrors.gigenet.com precise-updates/restricted amd64 Packages       
Hit http://mirrors.gigenet.com precise-updates/universe amd64 Packages         
Hit http://mirrors.gigenet.com precise-updates/multiverse amd64 Packages       
Hit http://mirrors.gigenet.com precise-updates/main i386 Packages              
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://dl.google.com stable Release                                        
Hit http://mirrors.gigenet.com precise-updates/restricted i386 Packages        
Hit http://mirrors.gigenet.com precise-updates/universe i386 Packages          
Hit http://mirrors.gigenet.com precise-updates/multiverse i386 Packages        
Hit http://mirrors.gigenet.com precise-updates/main TranslationIndex           
Hit http://mirrors.gigenet.com precise-updates/multiverse TranslationIndex     
Hit http://mirrors.gigenet.com precise-updates/restricted TranslationIndex     
Hit http://mirrors.gigenet.com precise-updates/universe TranslationIndex       
Hit http://mirrors.gigenet.com precise-backports/main Sources                  
Hit http://mirrors.gigenet.com precise-backports/restricted Sources            
Hit http://mirrors.gigenet.com precise-backports/universe Sources              
Hit http://mirrors.gigenet.com precise-backports/multiverse Sources            
Hit http://mirrors.gigenet.com precise-backports/main amd64 Packages           
Hit http://liveusb.info all Release.gpg                                        
Hit http://mirrors.gigenet.com precise-backports/restricted amd64 Packages     
Hit http://dl.google.com stable/main amd64 Packages                  
Hit http://mirrors.gigenet.com precise-backports/universe amd64 Packages       
Hit http://mirrors.gigenet.com precise-backports/multiverse amd64 Packages     
Hit http://mirrors.gigenet.com precise-backports/main i386 Packages            
Hit http://mirrors.gigenet.com precise-backports/restricted i386 Packages      
Hit http://mirrors.gigenet.com precise-backports/universe i386 Packages        
Hit http://mirrors.gigenet.com precise-backports/multiverse i386 Packages      
Hit http://mirrors.gigenet.com precise-backports/main TranslationIndex         
Hit http://mirrors.gigenet.com precise-backports/multiverse TranslationIndex   
Hit http://mirrors.gigenet.com precise-backports/restricted TranslationIndex   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://mirrors.gigenet.com precise-backports/universe TranslationIndex     
Hit http://mirrors.gigenet.com precise-security/main Sources                   
Hit http://mirrors.gigenet.com precise-security/restricted Sources             
Hit http://mirrors.gigenet.com precise-security/universe Sources               
Hit http://mirrors.gigenet.com precise-security/multiverse Sources             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://mirrors.gigenet.com precise-security/main amd64 Packages            
Hit http://mirrors.gigenet.com precise-security/restricted amd64 Packages      
Hit http://mirrors.gigenet.com precise-security/universe amd64 Packages        
Hit http://extras.ubuntu.com precise Release                                   
Hit http://mirrors.gigenet.com precise-security/multiverse amd64 Packages      
Hit http://mirrors.gigenet.com precise-security/main i386 Packages             
Hit http://mirrors.gigenet.com precise-security/restricted i386 Packages       
Hit http://mirrors.gigenet.com precise-security/universe i386 Packages         
Hit http://mirrors.gigenet.com precise-security/multiverse i386 Packages       
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirrors.gigenet.com precise-security/main TranslationIndex          
Hit http://mirrors.gigenet.com precise-security/multiverse TranslationIndex    
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://mirrors.gigenet.com precise-security/restricted TranslationIndex    
Hit http://mirrors.gigenet.com precise-security/universe TranslationIndex      
Hit http://mirrors.gigenet.com precise/main Translation-en           
Hit http://mirrors.gigenet.com precise/multiverse Translation-en     
Hit http://mirrors.gigenet.com precise/restricted Translation-en     
Hit http://mirrors.gigenet.com precise/universe Translation-en                 
Hit http://mirrors.gigenet.com precise-updates/main Translation-en             
Hit http://mirrors.gigenet.com precise-updates/multiverse Translation-en       
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://liveusb.info all Release                                            
Hit http://mirrors.gigenet.com precise-updates/restricted Translation-en       
Hit http://mirrors.gigenet.com precise-updates/universe Translation-en         
Hit http://mirrors.gigenet.com precise-backports/main Translation-en           
Hit http://mirrors.gigenet.com precise-backports/multiverse Translation-en     
Hit http://mirrors.gigenet.com precise-backports/restricted Translation-en     
Hit http://mirrors.gigenet.com precise-backports/universe Translation-en       
Hit http://mirrors.gigenet.com precise-security/main Translation-en            
Hit http://mirrors.gigenet.com precise-security/multiverse Translation-en      
Hit http://mirrors.gigenet.com precise-security/restricted Translation-en      
Hit http://mirrors.gigenet.com precise-security/universe Translation-en        
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://liveusb.info all/main amd64 Packages                      
Hit http://extras.ubuntu.com precise/main amd64 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages              
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://liveusb.info all/main i386 Packages                       
Ign http://liveusb.info all/main TranslationIndex                    
Ign http://dl.google.com stable/main Translation-en_US               
Ign http://dl.google.com stable/main Translation-en                  
Ign http://dl.google.com stable/main Translation-en_US               
Ign http://dl.google.com stable/main Translation-en                  
Ign http://extras.ubuntu.com precise/main Translation-en_US          
Ign http://liveusb.info all/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://liveusb.info all/main Translation-en
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.3%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130820.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.3%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130820.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn hplip hplip-data libgrip0 libhpmud0 libsane-hpaio libunity-2d-private0
  libunity-core-5.0-5 linux-generic linux-headers-generic linux-image-generic
  printer-driver-hpcups printer-driver-hpijs unity unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-common unity-services
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
sondra@ubuntu:~$
```

> ```
W: You may want to run apt-get update to correct these problems
```
running apt-get update just outputs the same response

This is on an Ubuntu 12.04.3

---

### Post by plucky on 2013-11-27
Open your Software Sources and disable the CDrom as a source.

Then run the update again and see if the error occurs.

Good Luck

---

### Post by micahpage on 2013-11-27
I cant even find software sources in gnome-shell search
searching on how to find software sources at :
[http://askubuntu.com/questions/131452/software-sources-not-found-in-unity-dash-search](http://askubuntu.com/questions/131452/software-sources-not-found-in-unity-dash-search)
shows to download package alacarte, but alacarte is not a ubuntu repo?

---

### Post by ian-weisser on 2013-11-27
> **micahpage said:**
> I cant even find software sources in gnome-shell search

Software Sources can be accessed several ways.

The easy way is to open Ubuntu Software Center.
Look in the menus: Edit --> Software Sources

It's also a menu item in the Synaptic application.

It can also be opened directly using the command **software-properties-gtk**
And perhaps a few other ways.

---

### Post by micahpage on 2013-11-27
that did clear the update, but now i still get the problem of:
```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn hplip hplip-data libgrip0 libhpmud0 libsane-hpaio libunity-2d-private0
  libunity-core-5.0-5 linux-generic linux-headers-generic linux-image-generic
  printer-driver-hpcups printer-driver-hpijs unity unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-services
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
sondra@ubuntu:~$ 

```
in which did not exist on the previous successful update maybe a week ago or so.

---

### Post by ian-weisser on 2013-11-27
Progress!

Kernel packages are usually held back from normal upgrades. That is normal (intended) behavior.

Do the command **sudo apt-get dist-upgrade** to update the kernel packages on your system.

---

### Post by micahpage on 2013-11-27
ah ok
thanks very much.

---

### Post by DuckHook on 2013-11-27
Please mark this thread "solved" using thread tools at top of page. Congrats and Happy Ubuntuing!

---

