---
title: "Requires installation of untrusted packages"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by swissflamdrag on 2012-03-21
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

libjack-jackd2-0:i386



help please!

---

### Post by oldos2er on 2012-03-21
Post moved to its own thread.

---

### Post by cortman on 2012-03-21
Hi, please run

```
sudo apt-get update
```

And post the results.

---

### Post by swissflamdrag on 2012-03-22
> **cortman said:**
> Hi, please run

```
sudo apt-get update
```And post the results.
Didnt really do anything, at one point it closed update manager but other than that no changes.

---

### Post by jerome1232 on 2012-03-22
> **swissflamdrag said:**
> Didnt really do anything, at one point it closed update manager but other than that no changes.

Open a terminal (ctrl+alt+t)

copy and paste that command (ctrl+alt+v to paste into terminal)

```
sudo apt-get update
```

Highlight all of the output in terminal, press ctrl+alt+c to copy

Paste it into a reply here on this thread (ctrl+v to paste)
Click go advanced if you are not already in advanced mode, highlight all the output you just copied, press the # symbol.

---

### Post by swissflamdrag on 2012-03-22
> **jerome1232 said:**
> Open a terminal (ctrl+alt+t)

copy and paste that command (ctrl+alt+v to paste into terminal)

```
sudo apt-get update
```Highlight all of the output in terminal, press ctrl+alt+c to copy

Paste it into a reply here on this thread (ctrl+v to paste)
Click go advanced if you are not already in advanced mode, highlight all the output you just copied, press the # symbol.
```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:2 http://dl.google.com stable Release [1,351 B]                            
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com maverick InRelease                            
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://security.ubuntu.com oneiric-security InRelease                      
Get:3 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Get:4 http://dl.google.com stable/main amd64 Packages [1,258 B]                
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release                                   
Get:5 http://dl.google.com stable/main i386 Packages [1,254 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://archive.canonical.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com maverick Release                              
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://us.archive.ubuntu.com oneiric InRelease             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com maverick-backports InRelease
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Get:6 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]
Get:7 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg
Hit http://us.archive.ubuntu.com oneiric-proposed Release.gpg
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://us.archive.ubuntu.com oneiric Release
Ign http://us.archive.ubuntu.com oneiric Release
Get:8 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]
Hit http://us.archive.ubuntu.com maverick-backports Release                    
Hit http://us.archive.ubuntu.com oneiric-proposed Release                      
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Ign http://us.archive.ubuntu.com oneiric/restricted Sources/DiffIndex          
Ign http://us.archive.ubuntu.com oneiric/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com oneiric/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com oneiric/main amd64 Packages/DiffIndex         
Ign http://us.archive.ubuntu.com oneiric/restricted amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com oneiric/universe amd64 Packages/DiffIndex     
Ign http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:9 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:10 http://us.archive.ubuntu.com oneiric-updates/main Sources [131 kB]      
Get:11 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]
Get:12 http://us.archive.ubuntu.com oneiric-updates/universe Sources [48.7 kB] 
Get:13 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [305 kB]
Get:14 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:15 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [104 kB]
Get:16 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:17 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [305 kB]
Get:18 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:19 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [105 kB]
Get:20 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]
Get:21 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:22 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:23 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:24 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com maverick-backports/main Sources               
Hit http://us.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://us.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://us.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Sources           
Hit http://us.archive.ubuntu.com oneiric-proposed/main Sources                 
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Sources           
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Sources             
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com oneiric-proposed/main amd64 Packages          
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com oneiric-proposed/universe amd64 Packages      
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted i386 Packages     
Hit http://us.archive.ubuntu.com oneiric-proposed/main i386 Packages           
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com oneiric-proposed/universe i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex        
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex    
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Get:25 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [142 kB]
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Get:26 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [62.9 kB]
Hit http://us.archive.ubuntu.com oneiric-proposed/main Translation-en          
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en      
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 1,273 kB in 11s (109 kB/s)                                             
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

```

---

### Post by cortman on 2012-03-22
Hi, looks like a GPG error. You can try the instructions given [here.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")

---

### Post by oldos2er on 2012-03-22
Your sources.list is a mess. Are you using 11.10 (Oneiric)? You need to remove all the references to maverick by either deleting those lines or putting a comment mark # in front of them. ```
gksu gedit /etc/apt/sources.list
``` After you've edited it, run ```
sudo apt-get update
``` again.

---

### Post by ionospheric on 2012-10-22
> **cortman said:**
> Hi, looks like a GPG error. You can try the instructions given [here.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")

This worked for me-thanks

---

### Post by monkeybrain2012 on 2012-10-22
Easy way to fix gpg errors
[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

