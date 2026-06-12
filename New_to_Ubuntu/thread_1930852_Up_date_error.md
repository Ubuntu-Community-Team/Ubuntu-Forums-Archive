---
title: "Up date error"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by bob brazie on 2012-02-24
11.10

What does this mean & why can't I install it?

Do I need it?

Thanks in advance. Bob.

---

### Post by oldos2er on 2012-02-24
Can you run ```
sudo apt-get update
``` in a terminal (Ctrl-Alt-t) and post the output here?

---

### Post by bob brazie on 2012-02-24
bob@bob-HP:~$ sudo apt-get update
[sudo] password for bob: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,349 B]                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,254 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Get:7 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 5,189 B in 5s (922 B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
bob@bob-HP:~$

---

### Post by oldos2er on 2012-02-24
To get the key run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A9653F936FD5529
``` then ```
sudo apt-get update
``` and the warning should be gone.

---

### Post by bob brazie on 2012-02-24
Thanks, but............. <g>

Why did I not already have the key if I was an official Ubuntu update?

---

### Post by roelforg on 2012-02-24
> **bob brazie said:**
> Thanks, but............. <g>

Why did I not already have the key if I was an official Ubuntu update?
Keys change; they keep us safe that way.

---

### Post by bob brazie on 2012-02-24
And I need all the help I can get! <g>

---

### Post by oldos2er on 2012-02-24
> **bob brazie said:**
> Thanks, but............. <g>

Why did I not already have the key if I was an official Ubuntu update?

Not sure what you mean. 'sudo apt-get update' works on all repositories in your /etc/apt/sources.list file, plus any *.list files in /etc/apt/sources.list.d/, whether they are 'official' or not. PPAs aren't official in that sense. Depending on how you install a PPA, you might not have registered its key.

---

### Post by roelforg on 2012-02-24
> **oldos2er said:**
> Not sure what you mean. 'sudo apt-get update' works on all repositories in your /etc/apt/sources.list file, plus any *.list files in /etc/apt/sources.list./, whether they are 'official' or not. PPAs aren't official in that sense. Depending on how you install a PPA, you might not have registered its key.
My private repo changes key everytime i add something.

---

### Post by bob brazie on 2012-02-24
I just would think that any thing "keyring"  would have been included in a fresh install of 11.10.

---

### Post by oldos2er on 2012-02-24
Keys for the default repositories should be added on install. Any repos you add later may or may not have their key installed depending on how you add them.

---

