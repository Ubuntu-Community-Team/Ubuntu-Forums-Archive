---
title: "Software manager not working"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-07-12
I can see what I want to install, but cannot tick add ons and when I press 'install,' nothing happens. What should I do?:confused::confused::confused:J

---

### Post by plucky on 2012-07-12
> **Jackalyn said:**
> I can see what I want to install, but cannot tick add ons and when I press 'install,' nothing happens. What should I do?:confused::confused::confused:J

Do you mean Ubuntu Software Centre?

Or Synaptic Package Manager?

Or Software Updater?

Open a terminal (Ctrl+Atl+t) and run ```
sudo apt-get update
``` and post back the output to the forum.

Good Luck

---

### Post by Jackalyn on 2012-07-12
> **plucky said:**
> Do you mean Ubuntu Software Centre?

Or Synaptic Package Manager?

Or Software Updater?

Open a terminal (Ctrl+Atl+t) and run ```
sudo apt-get update
``` and post back the output to the forum.

Good Luck

Ubuntu Software manager. Come to think of it it worked till I went to the left hand upper corner and tried to update. That just seemed to go round in circles.......hmm Still waiting for the terminal...Is that updating things?

jacky@jacky-Aspire-6930G:~$ sudo apt-get update
[sudo] password for jacky: 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release [49.6 kB]                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [24.8 kB]       
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,832 B]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [75.5 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [19.7 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources [934 kB]              
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [70 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [38.4 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [13.3 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:25 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg [316 B]           
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:28 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg [316 B]           
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex             
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [127 kB]      
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [33.0 kB] 
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [321 kB]
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [88.6 kB]
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,047 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [74 B]
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [71 B]
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [73 B]
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources [1,845 B]   
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources [11.9 kB]
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages [1,271 B]
Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:52 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages [10.2 kB]
Get:53 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Get:54 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB [96.4 kB]   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                   
Get:55 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB [79.8 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en             
Get:56 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB [2,406 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en             
Get:57 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en               
Get:58 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [150 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_GB           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_GB           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Fetched 13.6 MB in 5min 57s (38.2 kB/s)                                        
Reading package lists... Done
jacky@jacky-Aspire-6930G:~$

---

### Post by plucky on 2012-07-12
That looks ok.To actually install the updates you have to run ```
sudo apt-get upgrade
```

Post back if there are any errors.

Good Luck

---

### Post by Jackalyn on 2012-07-12
> **plucky said:**
> That looks ok.To actually install the updates you have to run ```
sudo apt-get upgrade
```Post back if there are any errors.

Good Luck

I did that and it did, but the Ubuntu software manager is stil broken.....:confused:J

---

### Post by richpri on 2012-07-12
Do you mean that the "Ubuntu Software Center" is broken or that the "Synaptic Package Manager" is broken?

Please explain "but cannot tick add ons" in more detail.

---

### Post by Jackalyn on 2012-07-12
> **richpri said:**
> Do you mean that the &quot;Ubuntu Software Center&quot; is broken or that the &quot;Synaptic Package Manager&quot; is broken?

Please explain &quot;but cannot tick add ons&quot; in more detail.

The thing on  the left hand side that looks like a shopping bag. It is orange and is called 'Ubuntu Software Manager.' It installs with Ubuntu 12.4 as part of the package. It is NOT the synaptic manager. That is downloaded, but not what I am talking about. I downloaded it with the Ubuntu Software manager.

If you see the software you could download in Ubuntu Software Manager then often if you scroll down you find add ons that you could install as well by ticking them.

What happens is that where the button is that says 'install,' is well...nothing happens any more. It was working fine till yesterday.

I just realised I can go to the top and go to the file menu and press install. That is a relif but why do the 'install' buttons not work and of course I still cannot get the add ons.

OOH I just tried it and it has fixed itself! I am not sure how to mark this thread lol..Is it fixed or is it not given something happened and I still don't know what!

Anyway thanks all!

---

