---
title: "Update Manager crashed"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by webbie180 on 2008-07-22
What should I do?

Tried sudo apt-get update, got this error,
Segmentation faultsts... 0%

Click synatic also crashed.

---

### Post by Happy_Man on 2008-07-22
> **webbie180 said:**
> What should I do?

Tried sudo apt-get update, got this error,
Segmentation faultsts... 0%

Click synatic also crashed.
Can you post the entire output of ```
sudo apt-get update
```?

---

### Post by webbie180 on 2008-07-23
@ubuntu:~$ sudo apt-get update
[sudo] password for : 
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release.gpg                                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]              
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [191B]                 
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Translation-en_SG                             
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_SG            
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release                                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_SG               
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_SG
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources [2429B]                 
Get:6 [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages [1295B]                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_SG        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources [3214B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_SG
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_SG         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_SG       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_SG           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_SG     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_SG       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_SG     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_SG                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_SG               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_SG                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_SG               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release [58.5kB]               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release [44.0kB]              
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]                        
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages [35.1kB]         
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages [6636B]    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages [23.4kB]     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages [3874B]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [282kB]           
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [74.0kB]      
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [16.4kB]    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages [53.0kB]        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages [14B]     
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages [25.7kB]    
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages [5337B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages [1178kB]                  
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages [6986B]             
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages [4297kB]              
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages [179kB]             
Fetched 6438kB in 1min21s (79.0kB/s)                                           
Segmentation faultsts... 0%

---

### Post by Happy_Man on 2008-07-23
Ok. That's... not cool. Apt-get doesn't segfault without a very good reason. Is this a fresh install? How long has this current install been around? Did you upgrade from Gutsy?

---

### Post by webbie180 on 2008-07-24
I upgraded from Gusty since the day Hardy was out.  Was able to update till yday.  The last time I did was installing and uninstalling tor and privoxy.

---

### Post by webbie180 on 2008-07-25
Anyone?  How to get synatic package manager to work again?  Thanks.

---

