---
title: "E: Unable to locate package"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by jasonwolf493 on 2011-10-28
Im trying to install openal as well as snlfile so i can play dwarf fortress with sound.    first I update which seems fine... ```

jason@jason-AO532h:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric/partner i386 Packages
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Hit http://extras.ubuntu.com oneiric Release                         
Ign http://archive.canonical.com oneiric/partner TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric-updates Release              
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Ign http://archive.canonical.com oneiric/partner Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Reading package lists... Done
jason@jason-AO532h:~$ 

```
Then When I try to install openal I get this...  ```
jason@jason-AO532h:~$ sudo apt-get install openal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openal
jason@jason-AO532h:~$ 


```

Same thing for the other package I want. Im not very good with ubuntu.

---

### Post by computerandu on 2011-10-28
what is the output of:

apt-cache search openal

based on the output choose for the missing package...

---

