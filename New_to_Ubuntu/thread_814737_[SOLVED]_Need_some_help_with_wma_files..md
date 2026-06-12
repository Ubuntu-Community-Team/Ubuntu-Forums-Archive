---
title: "[SOLVED] Need some help with wma files."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-06-01
I have been working on setting up an ubuntu computer and have everything ready and working except for one thing. I have a lot of music that I imported from my windows computer and some of the files are in wma. I need help either converting them into mp3s or setting up a program with codecs that will play them. I would prefer to use an application that manages your music like windows media player and have found amarok and banshee to be good options. Thanks for any help you can give me. I'm really excited to clear this last hurdle in the installation process.

---

### Post by ad_267 on 2008-06-01
WMA files work fine for me, did you install the ubuntu-restricted-extras package? I'm not sure exactly what package contains the wma codecs but that package contains a lot of useful stuff like flash, mp3 codecs etc.

---

### Post by Bradtek on 2008-06-01
You possibly need to install w32codecs using either synaptic 
or apt-get
```
sudo apt-get install w32codecs
```

---

### Post by sayakb on 2008-06-01
To install w32codecs, you need to add Medibuntu:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update[FONT=monospace]
[/FONT]sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list
sudo apt-get install w32codecs
```Issue these commands in right order into a terminal.

For more information, check [here]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by sithpigeon on 2008-06-01
Thanks, I'll try these ideas and post back. 
did this and got this, then it froze

adam@adam-build:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo: unable to resolve host adam-build
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty Release.gpg                             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Translation-en_US              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [5432B]                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Packages                       
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Sources                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7832B]            
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Packages                           
  302 Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Packages                       
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Sources                            
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Sources                        
  302 Found
99% [Connecting to packages.freecontrib.org (34.52.53.34)]

---

### Post by sithpigeon on 2008-06-01
Okay, I think (no guarantees) I got the win32 codecs installed. Now how do I incorporate them into an application I can use?

---

### Post by roblinux on 2008-06-01
They should automatically be detected....try playing a wma and see if it plays.


> **sithpigeon said:**
> Okay, I think (no guarantees) I got the win32 codecs installed. Now how do I incorporate them into an application I can use?

---

### Post by sithpigeon on 2008-06-01
Okay, I go into my Music folder and double click the wma file. Totem-xine opens up and then says "An error occured, this file is encrypted and cannot be played."

---

### Post by SunnyRabbiera on 2008-06-01
if your repositories froze dont do anything.
It might be best to restart your computer and try sudo apt-get update again as errors might come about.

---

### Post by sithpigeon on 2008-06-01
Okay I restarted my computer (had to mess around a bit to actually get it to load) and did sudo apt-get update again. Still get and encryption error. All I really need to do is convert the wma files into mp3s since mp3 works fine.

---

### Post by HotShotDJ on 2008-06-01
> **sithpigeon said:**
>    
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Packages                       
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/free Sources                            
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hefty/non-free Where did this come from... these are very outdated url's and there was never an Ubuntu distribution called "hefty."   I think you need to clean out your repository list.

---

### Post by HotShotDJ on 2008-06-01
> **sithpigeon said:**
> Still get and encryption error.Where did you get the music files?  They may be DRM'd.  If so, there is nothing in Linux that will play them.  Be sure to send a thank you note to Microsoft, Apple, and the RIAA.

---

### Post by sithpigeon on 2008-06-01
I had actually cleaned out the sources list after I recognized the errors. Thanks though. The wma files were ripped using Windows Media Player a long time ago, so I guess that means I can't play them on ubuntu? Does anyone know of a Windows XP program that could convert the wma files to mp3s or oggs?

---

### Post by cariboo on 2008-06-01
You have run into the dreaded DRM problem. Those files are never going to play in linux because of copy protection. If you legally own the files I would suggest using bittorent to download their mp3 equivalents.

note: this may not be 100% legal but at least you will be able to play your music. Of course if you live in the USA ignore this post.

Jim

---

### Post by sithpigeon on 2008-06-01
Thanks for the help, even if I didn't fix the problem. Will try getting mp3 equivalents on Windows. How do I post a solved thingy in the title?

---

