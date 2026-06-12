---
title: "Requires installation of untrusted packages ,what to do ?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by bobby84 on 2013-03-31
Absolute beginner.
Xubuntu 12.04 in virtualbox on win 7 x64 host.
What to do? i get this message from the update manager , for instance this file: 
"bind9-host dnsutils libbind9-80 libdns81 libisc83 libisccc80 libisccfg82 liblwres80 libssl1.0.0 libxml2 libxml2-utils openssl openvpn python-libxml2"
I do want my openvpn updated , but, this file is "untrusted" ?
With windows, i would not install an "untrusted"file, how do i treat these issues?

```
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Get:2 http://nl.archive.ubuntu.com precise Release.gpg [198 B]                
Get:3 http://nl.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://nl.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise Release                         
Hit http://nl.archive.ubuntu.com precise Release                     
Get:5 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:6 http://nl.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main Sources                              
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://nl.archive.ubuntu.com precise-backports Release                     
Hit http://nl.archive.ubuntu.com precise/main Sources                          
Hit http://nl.archive.ubuntu.com precise/restricted Sources                    
Hit http://nl.archive.ubuntu.com precise/universe Sources                      
Hit http://nl.archive.ubuntu.com precise/multiverse Sources                    
Hit http://nl.archive.ubuntu.com precise/main i386 Packages                    
Hit http://nl.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://nl.archive.ubuntu.com precise/universe i386 Packages                
Hit http://nl.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://nl.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://nl.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://nl.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://nl.archive.ubuntu.com precise/universe TranslationIndex             
Get:8 http://nl.archive.ubuntu.com precise-updates/main Sources [373 kB]       
Get:9 http://security.ubuntu.com precise-security/main Sources [64.7 kB]       
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:10 http://nl.archive.ubuntu.com precise-updates/restricted Sources [5,494 B]
Get:11 http://nl.archive.ubuntu.com precise-updates/universe Sources [82.7 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:12 http://nl.archive.ubuntu.com precise-updates/multiverse Sources [4,746 B]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [22.6 kB]
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [243 kB]
Get:17 http://nl.archive.ubuntu.com precise-updates/main i386 Packages [603 kB]
Get:18 http://nl.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Get:19 http://nl.archive.ubuntu.com precise-updates/universe i386 Packages [192 kB]
Get:20 http://nl.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://nl.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://nl.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://nl.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://nl.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://nl.archive.ubuntu.com precise-backports/main Sources                
Hit http://nl.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://nl.archive.ubuntu.com precise-backports/universe Sources            
Hit http://nl.archive.ubuntu.com precise-backports/multiverse Sources          
Get:21 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:22 http://security.ubuntu.com precise-security/universe i386 Packages [70.5 kB]
Hit http://nl.archive.ubuntu.com precise-backports/main i386 Packages         
Hit http://nl.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://nl.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://nl.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://nl.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://nl.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://nl.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://nl.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://nl.archive.ubuntu.com precise/main Translation-en                   
Hit http://nl.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://nl.archive.ubuntu.com precise/restricted Translation-en             
Hit http://nl.archive.ubuntu.com precise/universe Translation-en               
Hit http://nl.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://nl.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://nl.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://nl.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://nl.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://nl.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://nl.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://nl.archive.ubuntu.com precise-backports/universe Translation-en     
Get:23 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 1,793 kB in 4s (409 kB/s)
Reading package lists... Done

```

---

### Post by schragge on 2013-03-31
As the output you posted looks okey, I presume just rebuilding the package cache would help. For that, open a terminal window (press **Win**+**t**), and run:
```

sudo apt-get clean
sudo rm -fv /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by bobby84 on 2013-03-31
> **schragge said:**
> As the output you posted looks okey, I presume just rebuilding the package cache would help. For that, open a terminal window (press **Win**+**t**), and run:


Thanks i did as you suggested ,
what do i do next ? close and restart update manager?

What actually happened here?
Should i always take this action if i get these messages?

---

### Post by schragge on 2013-03-31
> **bobby84 said:**
> what do i do next ? close and restart update manager? Yes
> **bobby84 said:**
> What actually happened here? Probably, one of */var/lib/apt/lists/*Release.gpg* files got either corrupted or out of sync.
> **bobby84 said:**
> Should i always take this action if i get these messages?As long as you don't have any third party repositories or [PPAs]("https://help.ubuntu.com/community/PPA") enabled, this will be the most common cause of such messages. And the commands outlined above will fix the problem.

---

### Post by bobby84 on 2013-03-31
@schragge
Thank you for helping out.Cheers

---

