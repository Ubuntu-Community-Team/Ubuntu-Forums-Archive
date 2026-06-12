---
title: "can't uninstall or install anything ?"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by mj360 on 2011-09-22
hey i'm having a problem uninstalling a app called xvidcap screen capture. i installed it but it's not showing you in the sound & video part, but in ubuntu solfware center it say it's install but i can't remove it, i tried even removing it in synapic package manager and it still won't uninstall. it keep saying package operation failed. any idea what's going and how to fix it ?

oh and i'm on ubuntu 11.04

---

### Post by wolfen69 on 2011-09-22
```
sudo apt-get remove --purge xvidcap
```
Have you tried that? If not, do so and report back what happens.

---

### Post by mj360 on 2011-09-22
thanks for replying but i did the sudo apt-get remove --purge xvidcapit's still showing up in ubuntu solfware center and i still can't remove it ?

---

### Post by Krytarik on 2011-09-22
Try to reinstall it, and if that worked, and you still want to remove it, try that again:
```
sudo apt-get install --reinstall xvidcap
sudo apt-get purge xvidcap
```Hope it works!

---

### Post by mj360 on 2011-09-22
i tried the 
sudo apt-get install --reinstall
xvidcap sudo apt-get purge xvidcap

it still not working. it say 

files list file for package xvidcap contains empty filename
E: sub-process /usr/bin/dpkg returned an error code (2)

also i can't update in the update manager

---

### Post by Frogs Hair on 2011-09-22
Try these commands and copy and paste any terminal output in code tags using the # symbol on the reply tool bar .     
```
sudo apt-get autoclean
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```

---

### Post by mj360 on 2011-09-23
i tried the sudo apt-get autoclean but it still say package operation failed i still can't install or uninstall anything ?

---

### Post by oldos2er on 2011-09-23
Can you please copy and paste all the terminal output from those commands here?

---

### Post by mj360 on 2011-09-23
mj@ubuntu:~$ sudo apt-get autoclean
[sudo] password for mj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mj@ubuntu:~$ sudo dpkg --configure -a
mj@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed InRelease            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release.gpg [198 B]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release [30.0 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en        
Fetched 31.4 kB in 17s (1,764 B/s)                                             
Reading package lists... Done
mj@ubuntu:~$

---

### Post by mj360 on 2011-09-23
mj@ubuntu:~$ sudo apt-get install --reinstall xvidcap
[sudo] password for mj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 27 not upgraded.
Need to get 0 B/1,175 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously deselected package xvidcap.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xvidcap' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
mj@ubuntu:~$ sudo apt-get purge xvidcap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xvidcap*
0 upgraded, 0 newly installed, 1 to remove and 27 not upgraded.
After this operation, 2,875 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xvidcap' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

