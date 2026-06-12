---
title: "authentication failure"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by skrizwanali on 2011-11-12
i recently switched to kubuntu desktop environment from the unity in ubuntu 11.10...now when m going to update or install softwares from synaptic package manager its ok..but when it is done through ubuntu softwares sources i can't..same thing happens when i use kpackage kit from system tools..
what may b the problem ???
any kind of help will be highly appreciated..:confused:

---

### Post by bioterror on 2011-11-13
> **skrizwanali said:**
> i recently switched to kubuntu desktop environment from the unity in ubuntu 11.10...now when m going to update or install softwares from synaptic package manager its ok..but when it is done through ubuntu softwares sources i can't..same thing happens when i use kpackage kit from system tools..
what may b the problem ???
any kind of help will be highly appreciated..:confused:

what if you open terminal and you type next line:
*sudo apt-get update && sudo apt-get dist-upgrade*

Does it prompt any errors?

---

### Post by skrizwanali on 2011-11-13
> **bioterror said:**
> what if you open terminal and you type next line:
*sudo apt-get update && sudo apt-get dist-upgrade*

Does it prompt any errors?

no it works....but wats the problem with kpackage kit & ubuntu software centre...why it is showing authentication failure?

---

### Post by bioterror on 2011-11-13
> **skrizwanali said:**
> no it works....but wats the problem with kpackage kit & ubuntu software centre...why it is showing authentication failure?

can you provide a screenshot or something else more accurate information about this problem? We cant say without seeing.

---

### Post by skrizwanali on 2011-11-13
> **bioterror said:**
> can you provide a screenshot or something else more accurate information about this problem? We cant say without seeing.

nothing is happenening when i press the install button in ubuntu software centre...so how can i provide screen shot?
and if i use other software manager it shows like:-
the thumbnail given
even though it does'nt ask for any passwords for authentication......

---

### Post by bioterror on 2011-11-13
> **skrizwanali said:**
> nothing is happenening when i press the install button in ubuntu software centre...so how can i provide screen shot?
and if i use other software manager it shows like:-
the thumbnail given
even though it does'nt ask for any passwords for authentication......

What does that "Details" say?

---

### Post by skrizwanali on 2011-11-13
> **bioterror said:**
> What does that "Details" say?

it says 'failed to obtain authentication'.

---

### Post by JayKay3OOO on 2011-11-13
Did you install kubuntu-desktop from the package manager (software centre) while in Ubuntu Unity rather than a fresh install via the Kbuntu ISO?

If so I had the same problem that Kubuntu would not ask for a password when installing software and automatically gave authentication failure.

A fresh install will fix this using the Kubuntu ISO, but if I'm correct then this explains your problem so that people can help with that. I never bothered looking for a fix myself as I wanted to do a fresh install anyway after I'd made sure Kubuntu worked on my hardware.

---

### Post by oldos2er on 2011-11-13
> **skrizwanali said:**
> it says 'failed to obtain authentication'.

Can you run ```
sudo apt-get update
``` in a terminal, and post the full output here?

---

### Post by skrizwanali on 2011-11-14
> **JayKay3OOO said:**
> Did you install kubuntu-desktop from the package manager (software centre) while in Ubuntu Unity rather than a fresh install via the Kbuntu ISO?

If so I had the same problem that Kubuntu would not ask for a password when installing software and automatically gave authentication failure.

A fresh install will fix this using the Kubuntu ISO, but if I'm correct then this explains your problem so that people can help with that. I never bothered looking for a fix myself as I wanted to do a fresh install anyway after I'd made sure Kubuntu worked on my hardware.

yes i did it from software centre...not a fresh install..but dont want to make a fresh install...how can this problem b fixed???

---

### Post by skrizwanali on 2011-11-14
> **oldos2er said:**
> Can you run ```
sudo apt-get update
``` in a terminal, and post the full output here?

riz@riz-Inspiron-1420:~$ sudo apt-get update
[sudo] password for riz: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security InRelease                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release [24.3 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources [743 B]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B] 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources [2,580 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B] 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages [649 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages [3,383 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex [71 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [72 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main TranslationIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Translation-en      
Fetched 32.3 kB in 28s (1,124 B/s)                                             
Reading package lists... Done

---

### Post by oldos2er on 2011-11-14
There's nothing more after "Reading package lists... Done" ? If you run kpackagekit do you see any more errors?

---

