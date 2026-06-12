---
title: "Requires installation of untrusted packages?!?"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by RotorRick on 2011-11-10
Requires installation of untrusted packages?!?

I'm wanting to install a couple of image editing software packages, from the Ubuntu Software Center, like GIMP and Xara, but I get this message pop up, but I have no idea how to proceed further:



> Requires installation of untrusted packages
The action would require the installation of packages from unauthenticated sources.

xaralx xaralx-svg

and in GIMP:

> libbabl-0.0-0 libgegl-0.0-0

I've never seen this before, still new to Linux, so any help appreciated! Thanks!!!

---

### Post by oldos2er on 2011-11-10
Can you run ```
sudo apt-get update
``` in a terminal and post the output here?

---

### Post by centaurusa on 2011-11-10
> **RotorRick said:**
> Requires installation of untrusted packages?!?

I recently came across the same glitch while trying to update FreeFileSync from a PPA that I had added to the list of Software Sources.  The fix was to download a security key.  The tip came for Ubuntu 10.10 but it worked just fine on the current release (Version 11.10). 

See:  How to Fix &#8216;Requires installation of untrusted packages&#8217; error in Ubuntu 10.10 Maverick Meerkat
 [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

---

### Post by RotorRick on 2011-11-10
Oh, I forgot: I"m using[COLOR=DarkRed]** Ubuntu 10.04LTS **[/COLOR]


Ok, have a look at this:

> 
//////-laptop:~$ sudo apt-get update
[sudo] password for rick: 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA          
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA    
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                       
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources                      
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [523kB]         
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_CA        
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]               
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [464B]                         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [219kB]          
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [68.0kB]          
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [90.8kB]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [26.2kB]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,537B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [1,742B]   
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [3,998B] 
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [205kB]         
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [1,850B]  
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [235kB]    
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [82.1kB]    
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB] 
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [5,070B]  
Fetched 1,567kB in 1min 26s (18.0kB/s)                                         
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
/////-laptop:~$ 

---

### Post by alphacrucis2 on 2011-11-10
Try a different mirror.

---

### Post by oldos2er on 2011-11-10
Try the solution given in this thread: [http://ubuntuforums.org/showthread.php?t=1776763](http://ubuntuforums.org/showthread.php?t=1776763)

---

### Post by RotorRick on 2011-11-10
Tried the other solutions/thread, and it did not seem to work.

> **alphacrucis2 said:**
> Try a different mirror.

I'd like to, but I've no idea how to change this...

---

### Post by oldos2er on 2011-11-10
> **RotorRick said:**
> Tried the other solutions/thread, and it did not seem to work.

You ran the commands 
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```?  Can you please post the output from those commands?

---

### Post by RotorRick on 2011-11-11
Sure:

> rick@rick-laptop:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for rick: 
Sorry, try again.
[sudo] password for rick: 
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_main_i18n_Translation-en%5fCA'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_main_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_i18n_Translation-en%5fCA'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_universe_i18n_Translation-en%5fCA'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_universe_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_Release'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_Release.gpg'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_source_Sources'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_universe_source_Sources'
rick@rick-laptop:~$ 


And secondly:

> 
rick@rick-laptop:~$ 
rick@rick-laptop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_CA        
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg [189B]  
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Get:5 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [464B]                         
Get:7 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA 
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release [57.2kB]                      
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [219kB]         
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [67.8kB]         
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [90.8kB]    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [26.2kB]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,557B]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [1,750B]   
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [523kB]        
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [3,998B] 
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [205kB]         
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [1,850B]  
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [235kB]    
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [82.1kB]    
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB] 
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [5,070B]  
Fetched 12.6MB in 2min 47s (75.2kB/s)                                          
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
rick@rick-laptop:~$ 


Thanks! :D

---

### Post by rakesh.swapna on 2011-11-11
I am also facing same problem. This is my out put


ammu@ammu:~$ sudo apt-get update
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease [7,096 B]                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Sources [3,279 B]             
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Sources [4,354 B]         
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages [3,208 B]       
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages [6,378 B]   
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Get:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,208 B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,756 B]                      
Get:12 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                
Get:13 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5,922 B]                  
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,751 B]                      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:15 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [1,847 B]          
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [1,408 B]                 
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [2,120 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:18 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [3,512 B]    
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [3,607 B]                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [7,679 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:21 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                     
Get:22 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:23 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [14 B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Get:24 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [14 B]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US               
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]           
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_US           
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg [198 B]          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en              
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40.8 kB]                     
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [32.4 kB]             
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release [24.3 kB]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release [28.2 kB]            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources [877 kB]                 
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources [5,351 B]          
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources [4,677 kB]           
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources [149 kB]           
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]         
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B]    
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]     
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]     
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]       
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B] 
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B] 
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]   
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources [75.1 kB]        
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources [1,345 B]  
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources [12.9 kB]    
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources [1,032 B]  
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [146 kB]   
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,878 B]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [38.7 kB]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [2,703 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]  
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources [743 B]        
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]   
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources [2,580 B]  
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]   
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages [649 B]  
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages [3,383 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex [71 B]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex [72 B]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources [6,185 B]       
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources [14 B]    
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources [14 B]      
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources [14 B]    
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB] 
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages [6,722 B]
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages [14 B]
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex [72 B] 
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [70 B]
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex [72 B]
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en [701 kB]          
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]   
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]   
Get:84 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB]    
Get:85 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en [73.0 kB] 
Get:86 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en [1,190 B]
Get:87 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en [508 B]
Get:88 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en [23.0 kB]
Get:89 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en [604 B] 
Get:90 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en [14 B]
Get:91 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en [14 B]
Get:92 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en [2,997 B]
Get:93 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en [13.0 kB]
Get:94 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en [14 B]
Get:95 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:96 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en [4,303 B]
Fetched 16.1 MB in 2min 9s (124 kB/s)                                          
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2011-11-11
I second the idea to try a different server. Run ```
software-properties-gtk
``` under the Ubuntu Software tab, Download from: click the drop-down menu, choose either Main server or Other, Select Best Server.

Once that's done run ```
sudo apt-get update
``` again, and hopefully the errors will be gone.

rakesh.swapna, your problem is not the same; please start your own thread.

---

### Post by RotorRick on 2011-11-13
> **oldos2er said:**
> I second the idea to try a different server. Run ```
software-properties-gtk
``` 


right after running that I got this message:

> You need to be root to run this program

:confused:

It didn't prompt me for a password like I expected...

---

### Post by alphacrucis2 on 2011-11-13
> **RotorRick said:**
> right after running that I got this message:



:confused:

It didn't prompt me for a password like I expected...

Just put sudo in front of the command ie:

```
sudo software-properties-gtk 
```


Odd though. I don't need to run that program as root. It just prompts for my password if I try to change anything.

---

### Post by oldos2er on 2011-11-13
Should be **gksudo software-properties-gtk** since it's a graphical program.

---

### Post by RotorRick on 2011-11-13
Thank you! That seems to have fixed the problem!

I'm guessing that the original server mine was connected to, wasn't up to date with all the latest updates? I wish I'd taken note of which server that was, so I could inform them...

---

### Post by carbondalebaby on 2011-11-13
hi im totally new to ubuntu i tryed to install cheese to access my webcam and im getting the error no internet connection and untrusted packages help!!!!!!!!!!!!!!

---

### Post by oldos2er on 2011-11-14
carbondalebaby, please start your own thread and give full details of your issue.

---

### Post by eskararriba on 2012-04-09
it worked! just to make sure, the right command is 
sudo software-properties-gtk

---

### Post by MuRToN on 2012-09-11
> **eskararriba said:**
> it worked! just to make sure, the right command is 
sudo software-properties-gtk
Fixed it for me as well.
Changed from German server to main server.

---

### Post by jean noel on 2013-01-16
Recently got the same problem. worked perfectly well. Thanks.
Jean Noel

---

### Post by alex huhn on 2013-04-22
> **oldos2er said:**
> I second the idea to try a different server. Run ```
software-properties-gtk
``` under the Ubuntu Software tab, Download from: click the drop-down menu, choose either Main server or Other, Select Best Server.

Once that's done run ```
sudo apt-get update
``` again, and hopefully the errors will be gone.

rakesh.swapna, your problem is not the same; please start your own thread.

Worked for me. I changed mirror and was all ok. Thx **oldos2er!**

---

### Post by johndhutcheson on 2013-11-09
This tread may be 2 years old, but it did solve my problem, when a new gimp update turned up and failed.

[FONT=system][COLOR=#008000][FONT=courier new]sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update[/FONT][/COLOR]
[/FONT]
did the trick

---

### Post by oldos2er on 2013-11-09
Old thread closed.

---

