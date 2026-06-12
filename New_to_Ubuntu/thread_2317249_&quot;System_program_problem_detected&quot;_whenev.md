---
title: "&quot;System program problem detected&quot; whenever I reboot (Ubuntu Mate 14.04)"
date: 2016-03-14
forum: New to Ubuntu
---

### Post by uhuala on 2016-03-14
I have no idea what may be causing this. Whenever I restart my computer this message pops up, asking me if I want to report the problem. Can someone please help me with this? I have only had Ubuntu installed for a couple of weeks now...

---

### Post by Bashing-om on 2016-03-14
uhuala; Hello;

From terminal let's get a better idea of the situation, gives more details:
At the desktop key combo ctt+alt+t  yields a terminal interface:
Here execute:
```

sudo apt update
sudo apt upgrade

```
post these outputs - Between Code Tags - back here .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see 
[INDENT][INDENT]what tale gets told
[/INDENT][/INDENT]

---

### Post by uhuala on 2016-03-14
Hello. here are the outputs.

sudo apt update:

```

Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ca.archive.ubuntu.com trusty InRelease                              
Ign http://download.opensuse.org  InRelease                                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://ca.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:3 http://download.opensuse.org  Release.gpg [481 B]                        
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://download.opensuse.org  Release                                      
Ign http://download.opensuse.org  Release                                      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://security.ubuntu.com trusty-security/main Sources [106 kB]         
Ign http://download.opensuse.org  Packages/DiffIndex                           
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ca.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ca.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]  
Get:6 http://ca.archive.ubuntu.com trusty-updates/main Sources [262 kB]        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:7 http://security.ubuntu.com trusty-security/universe Sources [34.0 kB]    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,750 B]  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [438 kB]  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://extras.ubuntu.com trusty/main Translation-en_CA                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://download.opensuse.org  Packages                                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Ign http://download.opensuse.org  Translation-en_CA                            
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [125 kB]
Get:12 http://ca.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]
Ign http://download.opensuse.org  Translation-en                               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:13 http://ca.archive.ubuntu.com trusty-updates/universe Sources [151 kB]   
Hit http://ppa.launchpad.net trusty Release                                    
Get:14 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,991 B]
Hit http://ppa.launchpad.net trusty Release                                    
Get:15 http://security.ubuntu.com trusty-security/main i386 Packages [411 kB]  
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:16 http://ca.archive.ubuntu.com trusty-updates/multiverse Sources [5,946 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:17 http://ca.archive.ubuntu.com trusty-updates/main amd64 Packages [722 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:18 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:19 http://security.ubuntu.com trusty-security/universe i386 Packages [125 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:20 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,175 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://ppa.launchpad.net trusty/main Translation-en_CA                     
Ign http://ppa.launchpad.net trusty/main Translation-en  
Get:21 http://ca.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:22 http://ca.archive.ubuntu.com trusty-updates/universe amd64 Packages [339 kB]
Get:23 http://ca.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:24 http://ca.archive.ubuntu.com trusty-updates/main i386 Packages [697 kB] 
Get:25 http://ca.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:26 http://ca.archive.ubuntu.com trusty-updates/universe i386 Packages [340 kB]
Get:27 http://ca.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Hit http://ca.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ca.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ca.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ca.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ca.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ca.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://ca.archive.ubuntu.com trusty Release                                
Hit http://ca.archive.ubuntu.com trusty/main Sources                           
Hit http://ca.archive.ubuntu.com trusty/restricted Sources                     
Hit http://ca.archive.ubuntu.com trusty/universe Sources                       
Hit http://ca.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ca.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ca.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ca.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ca.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ca.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ca.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ca.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ca.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ca.archive.ubuntu.com trusty/main Translation-en_CA                 
Hit http://ca.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ca.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ca.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en_CA             
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en                
Ign http://ca.archive.ubuntu.com trusty/multiverse Translation-en_CA           
Ign http://ca.archive.ubuntu.com trusty/restricted Translation-en_CA           
Fetched 3,996 kB in 16s (242 kB/s)                                             
W: GPG error: http://download.opensuse.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

sudo apt upgrade:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-33 linux-headers-3.16.0-33-generic
  linux-image-3.16.0-33-generic linux-image-extra-3.16.0-33-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_14.04/  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_Horst3180_xUbuntu%5f14.04_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by Geoffrey_Arndt on 2016-03-14
Did you change the standard default "sources" in your repositories?   If you want Chrome browser, best just to download the deb file and install it via "gdebi" (a stand-alone, single package installer).   gdebi should either be already installed, or available via your normal package manager (is it Synaptic in Mate? or  maybe still Ubuntu Software Center?).   Remove (delete) the google source . . also, what are you trying to get from OpenSuse repos?

---

### Post by v3.xx on 2016-03-14
> **uhuala said:**
> Whenever I restart my computer this message pops up, asking me if I want to report the problem.
Looks like more than one problem to me.

Your crash message I suspect is apport.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

I think you should reset apport by removing the crash reports.

Open a terminal and enter
```
sudo rm /var/crash/*
```

These crash files can cause apport to hang .  If there is a real problem the crash report will regenerate and then we go from there.  But I think this will solve the one problem.

---

### Post by uhuala on 2016-03-15
> **v3.xx said:**
> 
Open a terminal and enter
```
sudo rm /var/crash/*
```

These crash files can cause apport to hang .  If there is a real problem the crash report will regenerate and then we go from there.  But I think this will solve the one problem.

This seems to have done the trick. Two reboots and no error messages.

---

### Post by uhuala on 2016-03-15
> **Geoffrey_Arndt said:**
> Did you change the standard default "sources" in your repositories?   If you want Chrome browser, best just to download the deb file and install it via "gdebi" (a stand-alone, single package installer).   gdebi should either be already installed, or available via your normal package manager (is it Synaptic in Mate? or  maybe still Ubuntu Software Center?).   Remove (delete) the google source . . also, what are you trying to get from OpenSuse repos?


I didn't intentionally try to change any sources. I may have done this by accident. Are you suggesting I uninstall chrome and reinstall using the method you described?

Mate uses Ubunutu software Center, but I did install a few things using "apt get ..." before I discovered it. I'm not sure what the OpenSuse repos are about...

---

### Post by v3.xx on 2016-03-15
You have a mix of 32/64bit sources, not so sure how you got there.

Anyhow if my guess work is right, this will solve your chrome problem.  Run this in terminal.

```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"

```
That command will put you on 64bit chrome.

Edit
then update again

---

### Post by uhuala on 2016-03-15
Ok, I ran that commanded and then updated. Here's the output:

```

sudo apt update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [108 kB]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://download.opensuse.org](http://download.opensuse.org)  InRelease                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:4 [http://download.opensuse.org](http://download.opensuse.org)  Release.gpg [481 B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Hit [http://download.opensuse.org](http://download.opensuse.org)  Release                                      
Ign [http://download.opensuse.org](http://download.opensuse.org)  Release                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [34.0 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://download.opensuse.org](http://download.opensuse.org)  Packages/DiffIndex                           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease [65.9 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B]  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [444 kB]  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources [264 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [125 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,991 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [416 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]   
Hit [http://download.opensuse.org](http://download.opensuse.org)  Packages                                     
Ign [http://download.opensuse.org](http://download.opensuse.org)  Translation-en_CA                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://download.opensuse.org](http://download.opensuse.org)  Translation-en                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main amd64 Packages [729 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [125 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                      
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe amd64 Packages [339 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages [701 kB] 
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages [340 kB]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources [8,696 B]    
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources [34.0 kB]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main amd64 Packages [9,782 B]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe amd64 Packages [40.9 kB]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages [9,797 B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages [41.0 kB]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Fetched 4,237 kB in 17s (242 kB/s)                                             
Reading package lists... Done
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886
W: Duplicate sources.list entry [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_14.04/](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_14.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_Horst3180_xUbuntu%5f14.04_Packages)

```

Do I need to do the upgrade too?

---

### Post by v3.xx on 2016-03-15
> Do I need to do the upgrade too? 

Nope, not yet :)  Two down one to go, then you can upgrade.

This opensuse entry needs to be disabled.  Open up your software sources

```
software-properties-gtk
```

Go to the second tab (other software) and **UN**check anything that has opensuse in it.  This will disable those packages.  Then close and update.  That should take care of the last error.

And then its time to upgrade.

---

### Post by uhuala on 2016-03-15
Done.

update:
```

Ign http://ca.archive.ubuntu.com trusty InRelease
Hit http://ca.archive.ubuntu.com trusty-updates InRelease                      
Ign http://dl.google.com stable InRelease                                      
Hit http://ca.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ca.archive.ubuntu.com trusty Release.gpg                            
Ign http://archive.canonical.com trusty InRelease                              
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ca.archive.ubuntu.com trusty-updates/main Sources                   
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ca.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://dl.google.com stable Release                                        
Hit http://ca.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://ca.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://ca.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ca.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ca.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ca.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ca.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ca.archive.ubuntu.com trusty-updates/universe Translation-en        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ca.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ca.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ca.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://ca.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Ign http://dl.google.com stable/main Translation-en_CA                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ca.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://ca.archive.ubuntu.com trusty Release                                
Hit http://ca.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ca.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://ca.archive.ubuntu.com trusty/universe Sources                       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ca.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ca.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ca.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://ca.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ca.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ca.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages            
Hit http://ca.archive.ubuntu.com trusty/universe i386 Packages    
Hit http://ca.archive.ubuntu.com trusty/multiverse i386 Packages  
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com trusty/main Translation-en_CA                 
Hit http://ca.archive.ubuntu.com trusty/main Translation-en                    
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ca.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ca.archive.ubuntu.com trusty/restricted Translation-en  
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en_CA 
Hit http://ppa.launchpad.net trusty Release                        
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty Release                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ca.archive.ubuntu.com trusty/multiverse Translation-en_CA           
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Ign http://ca.archive.ubuntu.com trusty/restricted Translation-en_CA
Hit http://ppa.launchpad.net trusty Release                         
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main amd64 Packages            
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://ppa.launchpad.net trusty/main Translation-en_CA
Ign http://ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done

```

Upgrade:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-33 linux-headers-3.16.0-33-generic
  linux-image-3.16.0-33-generic linux-image-extra-3.16.0-33-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by v3.xx on 2016-03-15
Nice :)

No errors and upgrade went through without error.  Now one more thing and this is a done deal.

```
sudo apt-get dist-upgrade
```

That will process any kernel upgrades.  If that goes without error then you need to reboot and your 100%.

Then you can

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by uhuala on 2016-03-15
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-33 linux-headers-3.16.0-33-generic
  linux-image-3.16.0-33-generic linux-image-extra-3.16.0-33-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by v3.xx on 2016-03-15
All is well.

Take note of the request to autoremove.  This will remove packages that are no longer required.  In your case, an old kernel.  So go for it :D

```
sudo apt-get autoremove
```

And a nice reference

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Any thing else?

---

### Post by uhuala on 2016-03-15
> **v3.xx said:**
> 

Any thing else?

I'd like to understand a bit of what we just did. for starters, how are update and upgrade different?


Edit: Nevermind. I just saw that you reference link above explains this.

thanks for all the help.

---

### Post by v3.xx on 2016-03-15
Update will do just that, update all installed packages, but changes nothing on your system.

Upgrade will install all of these updates to your system.

Make sense?

---

### Post by uhuala on 2016-03-15
Yup. Thanks.

---

### Post by v3.xx on 2016-03-16
Your welcome

Enjoy ):P

---

