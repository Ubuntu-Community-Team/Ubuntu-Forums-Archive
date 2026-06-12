---
title: "Problem installing BURG with SBM amd through the terminal"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by C95 on 2013-08-23
Hello,

This is the first time I have used Ubuntu Forums and straight out I would like to say that I am a total noob when it comes to Ubuntu and Linux in general:

My problem is that I am having a heck of time installing BURG onto my computer. I have used various methods and that I have found online, and all have ended in failure. Now I am not even sure if BURG is totally off my machine or what I even need to do. My last attempt has led me to a problem that prevents me from even reaching any multi-boot menu on my computer. When I power on my machine, it straightway gives me an error and a command line with grub> or grub rescue>. Can anybody help? My main purpose is to fix the whole MBR/Grub deal and just set up BURG on my machine.

Thanks :)

---

### Post by deadflowr on 2013-08-24
Read through this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

you'll probably need to find your installation disk for Ubuntu, it can run as a live session aka liveCD.
Use that method and follow the guidance of the boot- repair page.

---

### Post by C95 on 2013-08-24
> **deadflowr said:**
> Read through this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

you'll probably need to find your installation disk for Ubuntu, it can run as a live session aka liveCD.
Use that method and follow the guidance of the boot- repair page.

Thanks a bunch! I have already done this with a Linux Mint Live CD. I ran boot-repair and now when I turn on the machine, it shows that BURG is the OS chooser, but it looks exactly like GRUB, only it says BURG at the top. I have tried installing graphical themes through SBM, but when I click 'burg-emu', it still shows a text based interface. Any suggestions?

Thanks.

---

### Post by C95 on 2013-08-25
Sorry, new update:

I have been fiddling around with SBM and by trying to install BURG I have had several PPA errors and whatnot. My console output looks like this:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
W: Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

What do I do to fix this error?

Thanks in advance. :)

---

### Post by C95 on 2013-08-25
(This is through SBM by the way)

---

### Post by deadflowr on 2013-08-25
Don't know what SBM stands for.

But to fix the error message in the updates, open the update manager and go to settings, in the bottom left corner, then click it.
Then go to 'other software' when the software sources window pops up.
Then find the entries for the bean123ch, or burg ppa's and uncheck them, or remove them completely.
Then close out and in the update manager select 'check' and run an update.

As far as Burg themes go, I can't be of much help there.

---

### Post by C95 on 2013-08-25
> **deadflowr said:**
> Don't know what SBM stands for...

Super-Boot-Manager

---

### Post by deadflowr on 2013-08-25
Cool.
I'm horrible with acronyms.
But I did look at the launchpad page for that ppa and noticed there is no packages for precise, so you should just remove the ppa instead of just disabling it.
[https://launchpad.net/~bean123ch/+archive/burg](https://launchpad.net/~bean123ch/+archive/burg)

---

### Post by C95 on 2013-08-25
Thanks, now my only problem is that BURG looks exactly like GRUB, but it just says BURG. Any ideas how to install themes or make it graphical?

---

### Post by C95 on 2013-08-25
Hi. Thanks for all your help. The way I solved the last issue was through going to the terminal and typing in:

sudo editor /etc/default/burg

then I just added

GRUB_THEME=lightness 

to the file and saved it. When I rebooted the computer, BURG was up to its Graphical interface.

Thanks :)

---

