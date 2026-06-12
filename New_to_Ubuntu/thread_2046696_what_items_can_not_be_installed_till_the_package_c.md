---
title: "what items can not be installed till the package catalog is repaired"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Balmung4500 on 2012-08-23
what items can not be installed till the package catalog is repaired. how do i fix this?

---

### Post by gandaran on 2012-08-23
> **Balmung4500 said:**
> what items can not be installed till the package catalog is repaired. how do i fix this?
are you getting installs errors? try always to post the errors
or try run in terminal the update code
```
sudo apt-get update
```
if errors show up post the output here so we can see whats wrong

---

### Post by Balmung4500 on 2012-08-23
```
balmung@Evermore-PC:~$ sudo apt-get update
[sudo] password for balmung: 
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://archive.ubuntu.com precise-backports InRelease            
Ign http://archive.canonical.com precise InRelease                   
Ign http://extras.ubuntu.com precise InRelease                       
Ign http://archive.ubuntu.com precise-security InRelease
Hit http://archive.ubuntu.com precise Release.gpg                    
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]  
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://archive.ubuntu.com precise-backports Release.gpg
Hit http://archive.canonical.com precise Release                     
Hit http://extras.ubuntu.com precise Release                          
Get:2 http://archive.ubuntu.com precise-security Release.gpg [198 B]  
Hit http://archive.ubuntu.com precise Release                        
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                    
Get:3 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://archive.canonical.com precise/partner i386 Packages               
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise-backports Release                        
Get:4 http://archive.ubuntu.com precise-security Release [49.6 kB]       
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                 
Hit http://archive.ubuntu.com precise/multiverse Sources                 
Hit http://archive.ubuntu.com precise/universe Sources                   
Hit http://archive.ubuntu.com precise/main i386 Packages                 
Hit http://archive.ubuntu.com precise/restricted i386 Packages           
Hit http://archive.ubuntu.com precise/universe i386 Packages             
Hit http://archive.ubuntu.com precise/multiverse i386 Packages           
Hit http://archive.ubuntu.com precise/main TranslationIndex              
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex        
Hit http://archive.ubuntu.com precise/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise/universe TranslationIndex       
Get:5 http://archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:6 http://archive.ubuntu.com precise-updates/main Sources [158 kB]          
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                   
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Get:7 http://archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:8 http://archive.ubuntu.com precise-updates/universe Sources [50.1 kB]
Get:9 http://archive.ubuntu.com precise-updates/main i386 Packages [378 kB]
Get:10 http://archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:11 http://archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:12 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/main Sources
Hit http://archive.ubuntu.com precise-backports/restricted Sources
Hit http://archive.ubuntu.com precise-backports/universe Sources
Hit http://archive.ubuntu.com precise-backports/multiverse Sources
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Get:13 http://archive.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:14 http://archive.ubuntu.com precise-security/main Sources [40.6 kB]
Get:15 http://archive.ubuntu.com precise-security/multiverse Sources [1,386 B]
Get:16 http://archive.ubuntu.com precise-security/universe Sources [11.7 kB]
Get:17 http://archive.ubuntu.com precise-security/main i386 Packages [161 kB]
Get:18 http://archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:19 http://archive.ubuntu.com precise-security/universe i386 Packages [41.4 kB]
Get:20 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Fetched 1,100 kB in 6s (159 kB/s)                                              
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Bucky Ball on 2012-08-23
Well, your package manager seems to be fine but you have the CD enabled in Software Sources which is throwing the error (it is looking to update from the CD as well as the net).

Open your software sources or go to update manager and click the button 'Settings' in the bottom left hand corner. Click the 'Other Software' tab and untick all the entries for your CD. When you close that will ask you to reload/refresh update manager and you should be good to go. ;)

Issue these two commands when you're done:

```
sudo apt-get update
sudo apt-get upgrade
```

The second command will upgrade all packages and dependencies that need to be upgraded, it *won't* upgrade the release.

---

### Post by gandaran on 2012-08-23
the only thing wrong here is that you have the ubuntu live CD enabled in software sources, try going to software sources and uncheck the CD option or you have to insert the CD when running the update command.
if you still have problem installing software post the errors.

---

### Post by Balmung4500 on 2012-08-23
thx

---

