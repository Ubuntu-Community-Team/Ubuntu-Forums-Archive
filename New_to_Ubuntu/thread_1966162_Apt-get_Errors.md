---
title: "Apt-get Errors"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by d4m1r on 2012-04-26
Hey guys, I've been getting these errors for a month or two and I finally wanna do something about them. Back then, I was manually editing my sources file to try to fix a PPA but I didn't and seem to have screwed other things up. I am using 11.10 (32 bit) and have 5-6 PPA's added to keep my software up to date. See below for my full sudo apt-get update output:

```
damir@Damir-Ubuntu:~$ sudo apt-get update
[sudo] password for damir: 
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ca.archive.ubuntu.com oneiric InRelease                             
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://ca.archive.ubuntu.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ca.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ca.archive.ubuntu.com oneiric Release                               
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ca.archive.ubuntu.com oneiric-updates Release                       
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ca.archive.ubuntu.com oneiric/main Sources                          
Hit http://ca.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://ca.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ca.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://ca.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://ca.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ca.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ca.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ca.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Sources              
Ign https://private-ppa.launchpad.net oneiric InRelease                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en_CA                
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://ca.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit https://private-ppa.launchpad.net oneiric Release.gpg                      
Hit https://private-ppa.launchpad.net oneiric Release                
Ign http://archive.canonical.com oneiric/partner Translation-en_CA             
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA          
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_CA
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
W: Failed to fetch http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by plucky on 2012-04-27
Open up **Software Sources** and disable all your PPAs.

Then run ```
sudo apt-get update
``` from a terminal and see if you get any errors.

Then go back to Software Sources and enable one PPA and run the update again.

When the 404 error occurs again,it will be the last PPA you enabled.

Post the line in Sources.list that relates to the PPA that is causing the error.

Good Luck

---

### Post by d4m1r on 2012-04-27
> **plucky said:**
> Open up **Software Sources** and disable all your PPAs.

Then run ```
sudo apt-get update
``` from a terminal and see if you get any errors.

Then go back to Software Sources and enable one PPA and run the update again.

When the 404 error occurs again,it will be the last PPA you enabled.

Post the line in Sources.list that relates to the PPA that is causing the error.

Good Luck

Thanks for this! Totally forgot about software sources app...I didn't manually disable each of my PPA's but I as able to manually edit several entries which I could tell were wrong....I've narrowed it down to only 1 error left:


```
Err http://ppa.launchpad.net oneiric/main i386 Packages    
  404  Not Found
```Isn't that an official one? What could be the problem? :confused:

---

### Post by plucky on 2012-04-28
> Code:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages    
  404  Not Found

Isn't that an official one? What could be the problem? 

There is no official PPAs maintained by Canonical.

PPAs are maintained by individuals and groups for you to install upgraded versions of applications for each distribution.

See [PPA Index](http://ppa.launchpad.net/)

Just disable the PPA, as you are getting the 404 error, which means it is not found and maybe is offline or does not exist on the launchpad server.


Good Luck

---

