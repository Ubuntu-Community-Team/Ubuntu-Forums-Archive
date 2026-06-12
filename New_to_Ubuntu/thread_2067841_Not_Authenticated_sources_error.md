---
title: "Not Authenticated sources error"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by sonofabiscuit on 2012-10-07
I found the error posted several times, but nothing I'm doing repairs this. This occurs while attempting to download unrestricted extras from ubuntu software center. posting the sudo apt-get update result hoping someone can help.

```
bonzai@ubuntu:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease [7,096 B]                
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources/DiffIndex               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [49.6 kB]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources/DiffIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages/DiffIndex        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages/DiffIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [49.1 kB]    
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources [14.5 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [172 kB]      
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [58.0 kB] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [397 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [6,755 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [143 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,681 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [403 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [143 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,673 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Sources [2,761 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Sources [42.2 kB]    
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Sources [14 B] 
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Sources [6,135 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted amd64 Packages [5,001 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main amd64 Packages [86.0 kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse amd64 Packages [14 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe amd64 Packages [11.9 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted i386 Packages [4,935 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [87.7 kB]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [14 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [11.8 kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex [3,564 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex [2,605 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted TranslationIndex [2,461 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex [2,850 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [13.7 kB]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [13.7 kB]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [196 kB]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [5,414 B]
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [1,484 B]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [83.8 kB]
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en [34.0 kB]
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en [14 B]
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en [1,540 B]
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en [8,131 B]
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en [1,244 B]
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en [1,476 B]
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [9,880 B]
Fetched 25.0 MB in 3min 21s (124 kB/s)                                         
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
bonzai@ubuntu:~$
```

---

### Post by sonofabiscuit on 2012-10-07
should mention I attempted to fix GPG errors using Y PPA

---

### Post by cipherboy_loc on 2012-10-07
Check the tutorial they have, did you run the second command (apt-get install medibuntu-keyring)?
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)


Thanks,
Cipherboy

---

### Post by Gone fishing on 2012-10-07
```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```[/CODE]

Will add the keyring.

---

### Post by sonofabiscuit on 2012-10-07
thanks that did it

---

### Post by Gone fishing on 2012-10-08
Cheers but please mark as solved (makes it easy when other are searching for solutions)

---

