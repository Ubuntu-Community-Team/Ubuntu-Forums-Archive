---
title: "cannot upgrade"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by dblackmon on 2012-04-01
I have a new icon at the top of my screen it is a red circle with a white vertical line through it. Reminds me of a do not enter highway sign.
When I upgrade on through the terminal, it gives the message " 37 not upgraded." This number keeps increasing.

---

### Post by 2F4U on 2012-04-01
Can you open a terminal, run the following commands and post the output?

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by dblackmon on 2012-04-01
d@d-LT20:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric InRelease                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Get:1 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric Release.gpg [198 B]                
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric Release [4,221 B]                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric/cairo-dock i386 Packages [5,814 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric/cairo-dock TranslationIndex          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric/cairo-dock Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) oneiric/cairo-dock Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 10.5 kB in 3s (2,944 B/s)
Reading package lists... Done
d@d-LT20:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 gnome-shell : Depends: libmutter0 (< 3.4) but 3.4.0-0ubuntu1~oneiric1 is to be installed
               Depends: gnome-shell-common (= 3.3.4+git20120206.c63fe5ee-0ubuntu1~11.10~ricotz0) but 3.4.0-0ubuntu1~oneiric1 is to be installed
 libmutter0 : Breaks: gnome-shell (< 3.3.92~) but 3.3.4+git20120206.c63fe5ee-0ubuntu1~11.10~ricotz0 is to be installed
 mutter-common : Breaks: gnome-shell (< 3.3.92~) but 3.3.4+git20120206.c63fe5ee-0ubuntu1~11.10~ricotz0 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by HiImTye on 2012-04-01
please paste the output of the following command
```
apt-cache-policy  libmutter0 gnome-shell-common gnome-shell mutter-common
```

---

### Post by raja.genupula on 2012-04-01
do this in terminal
```
sudo apt-get install -f
```

try again .

---

### Post by dblackmon on 2012-04-01
> **HiImTye said:**
> please paste the output of the following command
```
apt-cache-policy  libmutter0 gnome-shell-common gnome-shell mutter-common
```

apt-cache-policy: command not found

---

### Post by dblackmon on 2012-04-01
Thanks- I've tried all of these suggestions, but I still get no upgrades. now it says this :

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by raja.genupula on 2012-04-02
> **dblackmon said:**
> Thanks- I've tried all of these suggestions, but I still get no upgrades. now it says this :

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

ok do these things in your terminal 
```
sudo -i
apt-get clean 
apt-get auto clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

All the best :)

---

