---
title: "Folder windows keep re-opening when I close them [Ubuntu Mate 14.04]"
date: 2016-04-06
forum: New to Ubuntu
---

### Post by deffydef on 2016-04-06
Things have recently gotten messed up on my system. I have no idea what may have caused this.

For certain folders, which I get to by going to "Places", if I close one (ctrl-w) then I immediately see a new window open, which displays "starting caja", and then becomes my downloads folder. I try to close it, and then the process repeats.

Can someone please help me with this?

---

### Post by v3.xx on 2016-04-06
Hi deffydef

You have a odd problem.  I wonder if it system wide or just something in your user profile.  Boot up your guest session and see if it is affected.

There are some bug reports out there.  One ctrl-w bug was traced back to the theme in use.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ctrl-w+bugs+launchpad&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ctrl-w+bugs+launchpad&sa=Search&cof=FORID:9)

---

### Post by deffydef on 2016-04-07
Seems to be just my profile. I couldn't reproduce the problem logged in as guest.

Just to be clear, the problem is the same if I click the x to close as well, not only when I use ctrl-w.

---

### Post by Bucky Ball on 2016-04-07
Have you added a file manager other than the default one? Not familiar with Mate, but has it got something like 'preferred applications'? Have a look in there and see what the preferred file manager is.

---

### Post by deffydef on 2016-04-07
Caja is the preferred file manager, and it's the only available option in the drop-down.

---

### Post by v3.xx on 2016-04-07
You have a caja configuration file in your home directory.  This can be reset by changing its name.  With caja closed, open a terminal and enter..

```
mv ~/.config/caja ~/.config/caja.old
```

Now open caja and see if that did any good.  If not, restore the original file..

```
mv ~/.config/caja.old ~/.config/caja
```

I would also like to look at your sources for any possible conflicts.  Please post the output of..

```
inxi -r
```

Its late here so be back tomorrow.  Maybe Bucky has some other ideas.

---

### Post by deffydef on 2016-04-07
Moving those files around doesn't seem to have helped. Although I'm not sure how I am supposed to close Caja.

Here's the output you requested:
```

inxi -r
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty universe
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty universe
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
           deb http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
           deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu trusty-security main restricted
           deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
           deb http://security.ubuntu.com/ubuntu trusty-security universe
           deb-src http://security.ubuntu.com/ubuntu trusty-security universe
           deb http://security.ubuntu.com/ubuntu trusty-security multiverse
           deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
           deb http://archive.canonical.com/ubuntu trusty partner
           deb-src http://archive.canonical.com/ubuntu trusty partner
           deb http://extras.ubuntu.com/ubuntu trusty main
           deb-src http://extras.ubuntu.com/ubuntu trusty main
           Active apt sources in file: /etc/apt/sources.list.d/extra-ppas.list
           deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu trusty main
           deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
           deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main
           deb http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu trusty main
           deb http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu trusty main
           Active apt sources in file: /etc/apt/sources.list.d/google-chrome.list
           deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
           Active apt sources in file: /etc/apt/sources.list.d/ubuntu-elisp-ppa-trusty.list
           deb http://ppa.launchpad.net/ubuntu-elisp/ppa/ubuntu trusty main
           Active apt sources in file: /etc/apt/sources.list.d/xqms-opencv-nonfree-trusty.list
           deb http://ppa.launchpad.net/xqms/opencv-nonfree/ubuntu trusty main


```

---

### Post by Bucky Ball on 2016-04-07
Can you run these two commands in a terminal and see what pops up, out of curiousity. Report any errors that might occur at the end of the output.

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

You added Mate over Ubuntu and are booting into the Mate desktop? 

```
Active apt sources in file: /etc/apt/sources.list.d/extra-ppas.list
           deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu trusty main
           deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
           deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main
           deb http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu trusty main
```

If that is the case, there could be some obscure(d) conflict going on between Nautilus and Caja.

---

### Post by deffydef on 2016-04-07
I ran the first 3 commands, here's the output.

```
 sudo apt-get autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

sudo apt-get update

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources [271 kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources [152 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [35.2 kB]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main amd64 Packages [754 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [455 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,991 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [429 kB]  
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe amd64 Packages [357 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages [720 kB] 
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages [359 kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en [378 kB]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,227 B]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en [187 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
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
Fetched 4,716 kB in 32s (146 kB/s)                                             
Reading package lists... Done

sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst1.5 libapt-pkg4.12
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,846 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main libapt-pkg4.12 amd64 1.0.1ubuntu2.12 [637 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main apt amd64 1.0.1ubuntu2.12 [954 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main libapt-inst1.5 amd64 1.0.1ubuntu2.12 [58.6 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main apt-utils amd64 1.0.1ubuntu2.12 [172 kB]
Get:5 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main apt-transport-https amd64 1.0.1ubuntu2.12 [25.1 kB]
Fetched 1,846 kB in 5s (328 kB/s)             
(Reading database ... 274873 files and directories currently installed.)
Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.12_amd64.deb ...
Unpacking libapt-pkg4.12:amd64 (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...
Setting up libapt-pkg4.12:amd64 (1.0.1ubuntu2.12) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
(Reading database ... 274873 files and directories currently installed.)
Preparing to unpack .../apt_1.0.1ubuntu2.12_amd64.deb ...
Unpacking apt (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up apt (1.0.1ubuntu2.12) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
(Reading database ... 274873 files and directories currently installed.)
Preparing to unpack .../libapt-inst1.5_1.0.1ubuntu2.12_amd64.deb ...
Unpacking libapt-inst1.5:amd64 (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...
Preparing to unpack .../apt-utils_1.0.1ubuntu2.12_amd64.deb ...
Unpacking apt-utils (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...
Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.12_amd64.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libapt-inst1.5:amd64 (1.0.1ubuntu2.12) ...
Setting up apt-utils (1.0.1ubuntu2.12) ...
Setting up apt-transport-https (1.0.1ubuntu2.12) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
```

I didn't manually install mate. It all came as one image: [https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/)

---

