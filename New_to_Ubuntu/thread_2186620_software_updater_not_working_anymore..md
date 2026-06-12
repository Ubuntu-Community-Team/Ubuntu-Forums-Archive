---
title: "software updater not working anymore."
date: 2013-11-08
forum: New to Ubuntu
---

### Post by shrynakesavan2 on 2013-11-08
[B]i was installing couple of softwares in Ubuntu when i suddenly started getting an error with the "Software Updater"

Couple of things i installed sucessfully before getting the errors[/B]
[B]Unity Tweak Tool
Variety wallpaper manager


then the problem arose with 
[/B]sudo apt-get install ubuntu-restricted-extras**, when i got a huge info sheet or licence within the terminal ending with a " <Ok >** " 
[B]in the middle of it... I didn't know how to proceed since i could't type anything anywhere so i just closed that terminal window and opened another one to proceed with rythmbox
when i got this error.[/B]

lucifel@lucifel-desktop:~$ sudo apt-get install rhythmbox
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lucifel@lucifel-desktop:~$ 

**then when i tried the software updater it gave me error and asked me to use "apt-get install -f"**


lucifel@lucifel-desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
lucifel@lucifel-desktop:~$ 

**Now i can**[B]'t install anything or remove anything, please help

T___T sorry if got too carried away with the sudo's 
[/B]

---

### Post by shrynakesavan2 on 2013-11-08
in software updater i get the option of partial upgrade
if i continue without it, i get
 "Software index is broken - 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

when i click on partial upgrade, i get 
"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

:(

---

### Post by fantab on 2013-11-08
The Package, 'ubuntu-restricted-extras' also installs some of Microsoft's core fonts like, arial, verdana etc, the lincence is for that. You should agree to it. Its nothing. These fonts come in handy when we open certain made in microsoft documents and websites.

Post the complete output of:
```
sudo apt-get update
```

Close all other package managers, like 'software center' or 'synaptic' before you run that command in the Terminal.

---

### Post by shrynakesavan2 on 2013-11-08
> **fantab said:**
> The Package, 'ubuntu-restricted-extras' also installs some of Microsoft's core fonts like, arial, verdana etc, the lincence is for that. You should agree to it. Its nothing. These fonts come in handy when we open certain made in microsoft documents and websites.

Post the complete output of:
```
sudo apt-get update
```

Close all other package managers, like 'software center' or 'synaptic' before you run that command in the Terminal.


Thanks a lot fantab , totally appretiate it.. :)

lucifel@lucifel-desktop:~$ sudo apt-get update
[sudo] password for lucifel: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease                          
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release.gpg [933 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_IN               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_IN                      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed Release.gpg [933 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release [49.6 kB]        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed Release [49.6 kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en                    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [28.0 kB]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [8,509 B]      
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [14 B]       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [70.1 kB]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B] 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [28.4 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Sources [14 B]           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Sources [14 B]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Sources [14 B]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Sources [834 B]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main i386 Packages [14 B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe i386 Packages [14 B] 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en          
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [7,939 B]         
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [4,315 B]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [14 B]      
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages [32.3 kB]   
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages [9,684 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages [14 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse i386 Packages [14 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted i386 Packages [14 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main i386 Packages [24.6 kB]   
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe i386 Packages [19.2 kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main Translation-en [13.9 kB]  
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse Translation-en [14 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted Translation-en [14 B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe Translation-en [10.7 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_IN                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe Translation-en_IN
Fetched 461 kB in 1min 8s (6,694 B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lucifel@lucifel-desktop:~$

---

### Post by fantab on 2013-11-08
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This error appears only when you run more than one package manger. Reboot computer and run 'sudo apt-get update' again. If you still get any errors than post the output.

---

### Post by shrynakesavan2 on 2013-11-08
lucifel@lucifel-desktop:~$ sudo apt-get update
[sudo] password for lucifel: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease                          
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports InRelease                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg                                
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release.gpg [933 B]  
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_IN               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_IN                      
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release [49.6 kB]        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed Release [49.6 kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en                    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [28.0 kB]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [8,509 B]      
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [14 B]       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [70.1 kB]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B] 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [28.4 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Sources [14 B]           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Sources [14 B]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Sources [14 B]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Sources [834 B]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main i386 Packages [14 B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe i386 Packages [14 B] 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en          
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [7,939 B]         
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [4,315 B]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [14 B]      
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages [32.3 kB]   
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages [9,684 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages [14 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse i386 Packages [14 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted i386 Packages [14 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main i386 Packages [24.6 kB]   
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe i386 Packages [19.2 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_IN                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-proposed/universe Translation-en_IN
Fetched 437 kB in 1min 1s (7,067 B/s)
Reading package lists... Done
lucifel@lucifel-desktop:~$

---

### Post by fantab on 2013-11-08
See you don't have any errors.

Install the packages you want to.

---

### Post by shrynakesavan2 on 2013-11-08
> **fantab said:**
> See you don't have any errors.

Install the packages you want to.

ehm...!!! 

Guess i freaked..!!!

Never the less thanks fantab, i totally appretiate it.

And thanks for putting up with assholes like me ... 

Haven't been more embarassed ever...  ;) thanks buddy.

---

### Post by fantab on 2013-11-08
No need to curse yourself, we all went through the same when we were beginning.

Mark the Tread as 'Solved' using Thread Tools.

---

