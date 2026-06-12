---
title: "Update  manager"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Ymurti on 2012-08-20
Please can someone help me?

When I tried using the upadate manager I got this message:

W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by roger_1960 on 2012-08-20
Hi

10.10 is no longer supported which might be the problem.  What exactly were you trying to do? Not sure why cdrom should be referred to in error message.

See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by blade4 on 2012-08-20
Please elaborate . When you say " using update manager" do you mean you get the error on starting the update manager or when you try to click on update ? 

Anyways , try updating from terminal : 

sudo apt-get update 
sudo apt-get upgrade

---

### Post by cortman on 2012-08-20
The actual solution to the problem is to run

```
gksu gedit /etc/apt/sources.list
```

At the top is a line(s) that mention the CDROM. Put a hash mark # at the start of each line. Save it and run apt-get update again.

That CROM line is telling your Ubuntu to check on the installation CD for installable packages. Since you don't have the CD in the drive it can't find that resource and thus gives an error.
Since the installation CD doesn't come with any packages beyond what's included already with the system, it's not useful to you.

But like roger_1960 said; 10.10 is no longer supported- you should upgrade to a different version (12.04).

---

### Post by Ymurti on 2012-08-20
> **blade4 said:**
> Please elaborate . When you say " using update manager" do you mean you get the error on starting the update manager or when you try to click on update ? 

Anyways , try updating from terminal : 

sudo apt-get update 
sudo apt-get upgrade

Dear Blade4, Thank you for your reply. First I would like to tell you that I have Ubuntu 12.04 installed in my laptop. When I try to use the update manager first I get this:


[ATTACH]222925[/ATTACH]

Then I click on Check, then I get this message:

[ATTACH]222926[/ATTACH]

I tried sudo apt-get update and I got this:


Chant and be happy
-- Srila Prabhupada
yajnamurti@yajnamurti-laptop:~$ sudo apt-get update
[sudo] password for yajnamurti: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick InRelease
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main TranslationIndex
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted TranslationIndex
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise InRelease                           
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates InRelease                   
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security InRelease                  
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed InRelease                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise Release.gpg                         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates Release.gpg                 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security Release.gpg                
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed Release.gpg                
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise Release                             
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates Release                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security Release                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed Release                    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted Sources                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main Sources                        
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse Sources                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe Sources                    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main i386 Packages                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted i386 Packages            
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe i386 Packages              
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse i386 Packages            
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main TranslationIndex               
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse TranslationIndex         
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted TranslationIndex         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe TranslationIndex           
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted Sources          
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main Sources                
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse Sources          
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe Sources            
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main i386 Packages          
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted i386 Packages    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe i386 Packages      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse i386 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main TranslationIndex       
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse TranslationIndex 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted TranslationIndex 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe TranslationIndex   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted Sources         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main Sources               
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse Sources         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe Sources           
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main i386 Packages         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted i386 Packages   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe i386 Packages     
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse i386 Packages   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main TranslationIndex      
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse TranslationIndex
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted TranslationIndex
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe TranslationIndex  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/restricted i386 Packages   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/main i386 Packages         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/multiverse i386 Packages   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/universe i386 Packages     
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/main TranslationIndex      
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/multiverse TranslationIndex
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/restricted TranslationIndex
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/universe TranslationIndex  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports Release.gpg                   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main Translation-en                 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse Translation-en           
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted Translation-en           
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe Translation-en             
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main Translation-en         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse Translation-en   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted Translation-en   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe Translation-en     
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main Translation-en        
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse Translation-en  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted Translation-en  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe Translation-en    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/main Translation-en        
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/multiverse Translation-en  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/restricted Translation-en  
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [770 B]                   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-proposed/universe Translation-en    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/main Sources         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/restricted Sources   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/universe Sources     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/multiverse Sources            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Fetched 2,315 B in 3s (704 B/s)
W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
yajnamurti@yajnamurti-laptop:~$ 


If you need more details please let me know. Thank you very much for your help.

---

### Post by Ymurti on 2012-08-20
> **cortman said:**
> The actual solution to the problem is to run

```
gksu gedit /etc/apt/sources.list
```

At the top is a line(s) that mention the CDROM. Put a hash mark # at the start of each line. Save it and run apt-get update again.

That CROM line is telling your Ubuntu to check on the installation CD for installable packages. Since you don't have the CD in the drive it can't find that resource and thus gives an error.
Since the installation CD doesn't come with any packages beyond what's included already with the system, it's not useful to you.

But like roger_1960 said; 10.10 is no longer supported- you should upgrade to a different version (12.04).


Dear Cortman,  Thanks a lot. I did what you said and now everything is ok.  ;)

---

### Post by cortman on 2012-08-20
> **Ymurti said:**
> Dear Cortman,  Thanks a lot. I did what you said and now everything is ok.  ;)

Great; but your sources.list is a mess. I would strongly recommend you go [here]("http://repogen.simplylinux.ch/") and generate a new sources.list for 12.04 Precise. Run these commands:

```
sudo mv /etc/apt/sources.list sources.list.old
sudo touch sources.list
gksu gedit sources.list
```

And copy/paste from the repogen site in there. Save and run

```
sudo apt-get update
```

to make sure you don't get any errors.

---

### Post by Ymurti on 2012-08-22
> **cortman said:**
> Great; but your sources.list is a mess. I would strongly recommend you go [here]("http://repogen.simplylinux.ch/") and generate a new sources.list for 12.04 Precise. Run these commands:

```
sudo mv /etc/apt/sources.list sources.list.old
sudo touch sources.list
gksu gedit sources.list
```

And copy/paste from the repogen site in there. Save and run

```
sudo apt-get update
```

to make sure you don't get any errors.

I did as you instructed me an here it is the result:

yajnamurti@yajnamurti-laptop:~$ sudo mv /etc/apt/sources.list sources.list.old
[sudo] password for yajnamurti: 
yajnamurti@yajnamurti-laptop:~$ sudo touch sources.list
yajnamurti@yajnamurti-laptop:~$ gksu gedit sources.list
yajnamurti@yajnamurti-laptop:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [770 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                       
Fetched 2,829 B in 8s (348 B/s)                                                                                       
Reading package lists... Done
yajnamurti@yajnamurti-laptop:~$ 


Thanks a lot for your help. :D

---

