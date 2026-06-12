---
title: "error broken count 0"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Cammigirl on 2012-06-05
I'm getting the same error message.  When I do "sudo apt-get update" in the terminal, I get the following:

[sudo] password for camil: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]       
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [14.9 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [4,935 B]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [49.4 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [7,786 B]                 
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [4,852 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [11.6 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [97.8 kB]     
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [19.6 kB] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,053 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [234 kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [57.9 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,046 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [700 B]     
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [6,109 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [559 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [5,227 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
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
Fetched 13.1 MB in 24s (537 kB/s)                                              
Reading package lists... Done
camil@camil-Asterope:~$ 

Advise please

---

### Post by oldos2er on 2012-06-06
Post moved to its own thread.

---

### Post by ptn107 on 2012-06-06
Clear your lists and try again (you will need to prefix each line with sudo):

```
rm -r /var/lib/apt/lists/*
mkdir /var/lib/apt/lists/partial
apt-get update
```

---

