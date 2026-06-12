---
title: "Software Center Freezes in Xubuntu"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2012-09-18
The Software Centre freezes in Xubuntu. Synaptic still works, so it's not really a big issue, I just hate it when things are broken.

Running software-centre from a console shows: 

> software-center
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-LP8gd4/pkcs11: No such file or directory
2012-09-19 02:56:20,135 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-09-19 02:56:20,140 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-09-19 02:56:20,206 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2012-09-19 02:56:20,688 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-09-19 02:56:20,784 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-09-19 02:56:20,786 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Killed

Any ideas? I've tried a reboot and reinstalling control-center. No better. It still freezes, necessitating a KILL.

---

### Post by Toz on 2012-09-18
Try deleting your software-center cache in ~/.cache and trying again.

---

### Post by SpongeBob SquarePants on 2012-09-19
Thanks for the response. Tried that and it's no better. It still runs, the GUI appears, but there's no text inside.

> **Toz said:**
> Try deleting your software-center cache in ~/.cache and trying again.

---

### Post by Toz on 2012-09-19
Try running the following at the command prompt and post back any error messages you may get:
```
sudo apt-get update
```

---

### Post by SpongeBob SquarePants on 2012-09-19
All looks fine apart from the missing key: 

> sudo apt-get update
[sudo] password: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                 
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:12 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,250 B]                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [43.5 kB]      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [13.5 kB]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [166 kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex             
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [167 kB]      
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [44.2 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [11.3 kB]                 
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [17.9 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [738 B]                   
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,055 B]           
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [52.2 kB] 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,324 B]                 
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [2,189 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,335 B]                 
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [2,073 B]           
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [389 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [132 kB]
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,673 B]
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 1,242 kB in 4s (280 kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

---

### Post by newb85 on 2012-09-19
> **SpongeBob SquarePants said:**
> All looks fine apart from the missing key:

Try
```
sudo apt-key update
```

Edit:
Oops, should have read the OP a little more closely.
Provide the output of
```
ls /tmp/keyring*
```

---

### Post by SpongeBob SquarePants on 2012-09-19
No change.

> sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

---

### Post by SpongeBob SquarePants on 2012-09-19
> **newb85 said:**
> Edit:
Oops, should have read the OP a little more closely.
Provide the output of
```
ls /tmp/keyring*
```

ls /tmp/keyring*
control

---

### Post by newb85 on 2012-09-19
> **SpongeBob SquarePants said:**
> ls /tmp/keyring*
control

I'm not familiar with Xubuntu specifically, but there should be a few more directories there.  In Ubuntu, I also have gpg, pkcs11, and ssh.  Specifically, your error message is about pkcs11 missing.

I don't know if you could fix it by simply adding those directories, or if it's more involved than that.  Hopefully someone with more experience will weigh in.

---

### Post by SpongeBob SquarePants on 2012-09-19
Okay, thanks for trying, buddy. I appreciate it. O:)

---

### Post by Linux_junkie on 2012-09-19
I think its your PPA thats causing the problem.  If you can de-select the PPA in your sources list then perform the update, it may fix the problem.

---

### Post by SpongeBob SquarePants on 2012-09-19
Thanks for the suggestion. I disabled all the ppa's (most of them are official... I think I only added two), updated apt, but software-centre still crashes:

> software-center
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-D7A2Cs/pkcs11: No such file or directory
2012-09-19 12:38:11,103 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-09-19 12:38:11,128 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-09-19 12:38:11,210 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2012-09-19 12:38:11,834 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-09-19 12:38:12,047 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.

---

### Post by SpongeBob SquarePants on 2012-09-19
Oh wait! Toz is right. Deleting the cache *does* work. I only deleted the download-cache, however, if you delete the whole software-center folder, the problem seems to go away.

For future reference, this is the ticket...

> rm -r ~/.cache/software-center

Thanks, Toz, and sorry for not understanding your instructions correctly  the first time.

---

