---
title: "software center problem"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by MaWiSo on 2012-04-30
i was playing with the software sources and i dont know exactly what i changed but it made a problem


i cant download any software
there is no install button

i tried the command
sudo apt-get install geany
it says :
E: Unable to locate package geany

the same with all packages
what shall i do ?

---

### Post by plucky on 2012-04-30
> **MaWiSo said:**
> i was playing with the software sources and i dont know exactly what i changed but it made a problem


i cant download any software
there is no install button

i tried the command
sudo apt-get install geany
it says :
E: Unable to locate package geany

the same with all packages
what shall i do ?

Post the output of your sources.list file ```
cat /etc/apt/sources.list
```

Also the output for ```
sudo apt-get update
``` so we can see what error are occurring.

---

### Post by MaWiSo on 2012-04-30
the first command gives this

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu precise main universe multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main universe multiverse restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu precise-backports main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu precise-security main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main universe multiverse restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```
the second :
```
Ign http://extras.ubuntu.com precise InRelease                            
Hit http://extras.ubuntu.com precise Release.gpg                          
Ign http://archive.ubuntu.com precise InRelease     
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://archive.ubuntu.com precise-backports InRelease
Ign http://archive.ubuntu.com precise-security InRelease
Hit http://extras.ubuntu.com precise Release
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]
Hit http://extras.ubuntu.com precise/main Sources         
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:4 http://archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://extras.ubuntu.com precise/main amd64 Packages  
Hit http://extras.ubuntu.com precise/main i386 Packages
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]
Ign http://extras.ubuntu.com precise/main TranslationIndex
Get:6 http://archive.ubuntu.com precise-updates Release [49.6 kB]                                                                             
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                   
Get:7 http://archive.ubuntu.com precise-updates Release [49.6 kB]                                                                             
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                      
Get:8 http://archive.ubuntu.com precise-backports Release [49.6 kB]                                                                           
Get:9 http://archive.ubuntu.com precise-security Release [49.6 kB]                                                                            
Get:10 http://archive.ubuntu.com precise-security Release [49.6 kB]                                                                           
Get:11 http://archive.ubuntu.com precise/main Sources [934 kB]                                                                                
Get:12 http://archive.ubuntu.com precise/universe Sources [5,019 kB]                                                                          
Get:13 http://archive.ubuntu.com precise/multiverse Sources [155 kB]                                                                           
Get:14 http://archive.ubuntu.com precise/restricted Sources [5,470 B]                                                                          
Get:15 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                                                                        
Get:16 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                                                                    
Get:17 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                                                    
Get:18 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                                                                   
Get:19 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                         
Get:20 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                                     
Get:21 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                     
Get:22 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                    
Get:23 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]                                                                       
Get:24 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                                                                 
Get:25 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                                                                 
Get:26 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                                                                   
Get:27 http://archive.ubuntu.com precise-updates/main Sources [5,093 B]                                                                        
Get:28 http://archive.ubuntu.com precise-updates/universe Sources [1,032 B]                                                                    
Get:29 http://archive.ubuntu.com precise-updates/multiverse Sources [14 B]                                                                     
Get:30 http://archive.ubuntu.com precise-updates/restricted Sources [765 B]                                                                    
Get:31 http://archive.ubuntu.com precise-updates/main amd64 Packages [19.0 kB]                                                                 
Get:32 http://archive.ubuntu.com precise-updates/universe amd64 Packages [2,083 B]                                                             
Get:33 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [14 B]                                                              
Get:34 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [757 B]                                                             
Get:35 http://archive.ubuntu.com precise-updates/main i386 Packages [20.3 kB]                                                                  
Get:36 http://archive.ubuntu.com precise-updates/universe i386 Packages [2,088 B]                                                              
Get:37 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14 B]                                                               
Get:38 http://archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]                                                              
Get:39 http://archive.ubuntu.com precise-updates/main TranslationIndex [72 B]                                                                  
Get:40 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [70 B]                                                            
Get:41 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]                                                            
Get:42 http://archive.ubuntu.com precise-updates/universe TranslationIndex [72 B]                                                              
Get:43 http://archive.ubuntu.com precise-backports/main Sources [700 B]                                                                        
Get:44 http://archive.ubuntu.com precise-backports/universe Sources [14 B]                                                                     
Get:45 http://archive.ubuntu.com precise-backports/multiverse Sources [14 B]                                                                   
Get:46 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                   
Get:47 http://archive.ubuntu.com precise-backports/main amd64 Packages [559 B]                                                                 
Get:48 http://archive.ubuntu.com precise-backports/universe amd64 Packages [14 B]                                                              
Get:49 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]                                                            
Get:50 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                            
Get:51 http://archive.ubuntu.com precise-backports/main i386 Packages [559 B]                                                                  
Get:52 http://archive.ubuntu.com precise-backports/universe i386 Packages [14 B]                                                               
Get:53 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]                                                             
Get:54 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                             
Get:55 http://archive.ubuntu.com precise-backports/main TranslationIndex [71 B]                                                                
Get:56 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [70 B]                                                          
Get:57 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                                                          
Get:58 http://archive.ubuntu.com precise-backports/universe TranslationIndex [70 B]                                                            
Get:59 http://archive.ubuntu.com precise-security/main Sources [1,550 B]                                                                       
Get:60 http://archive.ubuntu.com precise-security/universe Sources [2,143 B]                                                                   
Get:61 http://archive.ubuntu.com precise-security/multiverse Sources [14 B]                                                                    
Get:62 http://archive.ubuntu.com precise-security/restricted Sources [14 B]                                                                    
Get:63 http://archive.ubuntu.com precise-security/main amd64 Packages [12.0 kB]                                                                
Get:64 http://archive.ubuntu.com precise-security/universe amd64 Packages [2,552 B]                                                            
Get:65 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [14 B]                                                             
Get:66 http://archive.ubuntu.com precise-security/restricted amd64 Packages [14 B]                                                             
Get:67 http://archive.ubuntu.com precise-security/main i386 Packages [11.9 kB]                                                                 
Get:68 http://archive.ubuntu.com precise-security/universe i386 Packages [2,571 B]                                                             
Get:69 http://archive.ubuntu.com precise-security/multiverse i386 Packages [14 B]                                                              
Get:70 http://archive.ubuntu.com precise-security/restricted i386 Packages [14 B]                                                              
Get:71 http://archive.ubuntu.com precise-security/main TranslationIndex [72 B]                                                                 
Get:72 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [70 B]                                                           
Get:73 http://archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]                                                           
Get:74 http://archive.ubuntu.com precise-security/universe TranslationIndex [72 B]                                                             
Get:75 http://archive.ubuntu.com precise/main Translation-en [726 kB]                                                                          
Get:76 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                                   
Get:77 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                   
Get:78 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                                    
Get:79 http://archive.ubuntu.com precise-updates/main Translation-en [9,154 B]                                                                 
Get:80 http://archive.ubuntu.com precise-updates/multiverse Translation-en [14 B]                                                              
Get:81 http://archive.ubuntu.com precise-updates/restricted Translation-en [267 B]                                                             
Get:82 http://archive.ubuntu.com precise-updates/universe Translation-en [1,200 B]                                                             
Get:83 http://archive.ubuntu.com precise-backports/main Translation-en [308 B]                                                                 
Get:84 http://archive.ubuntu.com precise-backports/multiverse Translation-en [14 B]                                                            
Get:85 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                                            
Get:86 http://archive.ubuntu.com precise-backports/universe Translation-en [14 B]                                                              
Get:87 http://archive.ubuntu.com precise-security/main Translation-en [3,575 B]                                                                
Get:88 http://archive.ubuntu.com precise-security/multiverse Translation-en [14 B]                                                             
Get:89 http://archive.ubuntu.com precise-security/restricted Translation-en [14 B]                                                             
Get:90 http://archive.ubuntu.com precise-security/universe Translation-en [1,499 B]                                                            
Fetched 23.0 MB in 56min 38s (6,759 B/s)                                                                                                       
Reading package lists... Done
```

---

### Post by cortman on 2012-04-30
This all looks ok- try installing geany again.
Could be you just had to run the update.

---

### Post by MaWiSo on 2012-04-30
it really just needed the update


it is working now
thanks

---

### Post by mörgæs on 2012-04-30
Good, please mark the thread 'solved'.

---

