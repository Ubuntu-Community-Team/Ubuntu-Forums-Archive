---
title: "System Update - Package Information"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by Segofam on 2012-01-28
Hi,

My Update Manager says "Your system is uptodate" which is great :)

But then under that it says "The Package Information was last updated 406 days ago" :-/

Is that normal?

---

### Post by sudodus on 2012-01-28
Are you running Lucid? Then I would say, no, it is not normal. I received some updates today ... What happens if you run apt-get from a terminal window?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by lechien73 on 2012-01-28
When was the last time you received updates on your system?

---

### Post by Segofam on 2012-01-28
I get...

scott@scott-laptop:~$ sudo apt-get update
[sudo] password for scott: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/ oneiric/main Translation-en_AU
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/ oneiric/restricted Translation-en_AU
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_AU       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/aubuntu/wine/ubuntu/](http://ppa.launchpad.net/aubuntu/wine/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU             
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) lucid/main Translation-en_AU 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_AU   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                           
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                           
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,222B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources      
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [759B]               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Fetched 5,071B in 3s (1,523B/s)
W: Failed to fetch [http://ppa.launchpad.net/aubuntu/wine/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/aubuntu/wine/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
scott@scott-laptop:~$

---

### Post by Segofam on 2012-01-28
I got updates this morning when I turned my laptop on

---

### Post by Frogs Hair on 2012-01-28
You may want to open the update manager enter settings and see the when check for updates menu . I sure you missed out some improvements in 406 days . :P

---

### Post by Segofam on 2012-01-28
Prereleased and Unsupportred are the only ones unchecked!

Gotta go out for a few hours...bbl...I appreciate the help guys :)

---

### Post by mcduck on 2012-01-28
```
Err http://ppa.launchpad.net lucid/main Packages
404 Not Found
Fetched 5,071B in 3s (1,523B/s)
W: Failed to fetch http://ppa.launchpad.net/aubuntu/win...86/Packages.gz 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

This is the problem. The Update Manager doesn't consider your system fully updated if there's any error with any repository. So even though you have installed all the available updates, as long as you have a non-functioning repository you are going to get the same message.

It's not dangerous, but since that repository clearly hasn't worked for a long time you might want to remove it from your software sources.

---

### Post by lechien73 on 2012-01-28
The [http://ppa.launchpad.net/aubuntu/wine/](http://ppa.launchpad.net/aubuntu/wine/) repository has been completely removed from launchpad, so the best thing to do would be to go into **System &#8594; Administration &#8594; Software Sources**, click the **Other Software** tab, uncheck this repository and then click **Close** to allow the repositories to update.

---

### Post by Segofam on 2012-01-29
I unchecked the boxes next to the Wine *stuff and my package  information is uptodate :-) 
Thanks lechian73 and folks, you are greatly appreciated :-)

---

