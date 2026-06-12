---
title: "Can't download from ubuntu software centre"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by jayrjay on 2012-02-01
Hi after a software update this week I have tried to download programs from Ubuntu software center. It starts to download then stops and goes back to the "install" button I don't get any error message anybody know what the problem is?:confused:

---

### Post by cortman on 2012-02-01
> **jayrjay said:**
> Hi after a software update this week I have tried to download programs from Ubuntu software center. It starts to download then stops and goes back to the "install" button I don't get any error message anybody know what the problem is?:confused:

Odd. Have you restarted your computer since you download the updates?

To make sure that you're connecting to the repositories ok, open a terminal and run

```
sudo apt-get update
```

and post the output here.

It could be a problem only with the Software Centre program, or it could be an aptitutde or package system problem.

---

### Post by jayrjay on 2012-02-01
Hi Cortman there is a pile of information hope you can see something. Yes I have restarted my PC the first time I did it it gave me a choice of 3.0 or such didnt understand it so hit top one.

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [40.8 kB]     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release [40.8 kB]             
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric InRelease                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources [120 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release.gpg                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]  
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources [40.8 kB]     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release                          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources [3,654 B]   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [280 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main TranslationIndex            
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]                                                          
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [92.8 kB]                                                            
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,336 B]                                                          
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]                                                                
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]                                                          
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]                                                          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]                                                            
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources [27.1 kB]                                                                     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources [14 B]                                                                  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources [8,967 B]                                                                 
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources [1,629 B]                                                               
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages [76.5 kB]                                                               
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]                                                            
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages [24.7 kB]                                                           
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3,345 B]                                                         
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]                                                               
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]                                                         
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]                                                         
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_GB                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_GB                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_GB                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_GB                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en                                                                      
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en [55.3 kB]                                                           
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en [39.8 kB]                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en                                                                       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en_GB                                                                         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en                                                                            
Fetched 867 kB in 19s (45.0 kB/s)                                                                                                            
Reading package lists... Done

Thanks :P

---

### Post by cortman on 2012-02-01
Your apt-get (the real package program, for which the USC is just a graphical front-end) is running fine. How about you try downloading your program using Synaptic, or the command line? To use the command line, type 

```
sudo apt-get install program_name
```

Note that software package names usually differ slightly from their name in the Software Centre. To find out what the package name is, you can type

```
apt-cache search -n program_name
```

This will show a list of all the packages that include the program name. Find the one you want, and use apt-get to install it.
If it installs fine, you may just want to uninstall and reinstall Ubuntu Software Centre. You can do that with

```
sudo apt-get remove software-center
sudo apt-get install software-center
```

Post back if you have any more questions. Good luck!

---

### Post by jayrjay on 2012-02-01
Thank you so much did as you suggested and the program downloaded fine, so unistalled then reinstalled software market and it's now downloading a treat. :D

Now if you can just tell me how to access my installation directory I'll be a happy man :P

Link to that post is

[http://ubuntuforums.org/showthread.php?t=1917164](http://ubuntuforums.org/showthread.php?t=1917164)

Thank you so much for your help

Jay Jay
[ ]("http://ubuntuforums.org/showthread.php?t=1917164")

---

### Post by cortman on 2012-02-01
> **jayrjay said:**
> Thank you so much did as you suggested and the program downloaded fine, so unistalled then reinstalled software market and it's now downloading a treat. :D

Now if you can just tell me how to access my installation directory I'll be a happy man :P

Link to that post is

[http://ubuntuforums.org/showthread.php?t=1917164](http://ubuntuforums.org/showthread.php?t=1917164)

Thank you so much for your help

Jay Jay
[ ]("http://ubuntuforums.org/showthread.php?t=1917164")

Great! Glad it's working for you. Mark this thread as [SOLVED] using the thread tools, if you would. I'll have a look at your other thread.

---

