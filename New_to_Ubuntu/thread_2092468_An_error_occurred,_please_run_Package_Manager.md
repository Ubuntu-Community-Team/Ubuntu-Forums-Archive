---
title: "An error occurred, please run Package Manager"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Nagle75 on 2012-12-07
When I updated to Ubuntu 12.04 my printer suddenly stopped working, it's an older model, 8045D. I tried a few different "howto's" including this one: [http://ubuntuforums.org/showthread.php?t=590793&highlight=printing+brother+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=printing+brother+printer) After I followed this I then received this annoying red (minus) icon on the top right of my desktop. If I click on it I get this message: "An error occurred, please run package manager from the right click menu or apt-get in a terminal..."  I then tried to be resourceful & resolve the issue on my own which lead me to this page: [http://www.linuxquestions.org/questions/linux-software-2/an-error-occurred-please-run-package-manager-819045/](http://www.linuxquestions.org/questions/linux-software-2/an-error-occurred-please-run-package-manager-819045/) This only made problems worse, because now, when I try to open Software Manager or "Synaptic", they crash & give me this error: "System Program Problem Detected". :confused: If any one could please help it would be greatly appreciated, Thanks!

---

### Post by Nagle75 on 2012-12-08
Can some one please tell me how to un-do what I did above? Thanks!

---

### Post by ibjsb4 on 2012-12-08
Could use some more info.  Open a terminal and enter:

```
sudo apt-get update
```

And please post the output.

---

### Post by Nagle75 on 2012-12-08
```
nagel@nagel-G41D3:~$ sudo apt-get update
[sudo] password for nagel: 
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (201208nagel@nagel-G41D3:~$ sudo apt-get update
[sudo] password for nagel: 
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [195 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [65.8 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [441 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [160 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [448 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [18.1 kB]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,392 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [208 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [161 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,661 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [19.0 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [17.8 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [17.8 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [216 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [58.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,189 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [215 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [96.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [59.2 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,388 B]
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [35.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en        
Fetched 2,726 kB in 2s (1,121 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
23.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [195 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [65.8 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [441 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [160 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [448 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [18.1 kB]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,392 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [208 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [161 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,661 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [19.0 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [17.8 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [17.8 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [216 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [58.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,189 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [215 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [96.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [59.2 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,388 B]
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [35.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en        
Fetched 2,726 kB in 2s (1,121 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ibjsb4 on 2012-12-08
Open your "Software Sources' and uncheck Cdrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Then run another update.  Also ..

```
nagel@nagel-G41D3:~$ sudo apt-get update
[sudo] password for nagel: 
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (201208nagel@nagel-G41D3:~$ sudo apt-get update
[sudo] password for nagel: 
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64  (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64  (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [195 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [65.8 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [441 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [160 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [448 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [18.1 kB]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,392 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [208 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [161 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,661 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [19.0 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [17.8 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [17.8 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [216 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [58.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,189 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [215 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [96.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [59.2 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,388 B]
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [35.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en        
Fetched 2,726 kB in 2s (1,121 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/main/binary-amd64/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64  (20120823.1)/dists/precise/restricted/binary-amd64/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
23.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64  (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64  (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [195 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [65.8 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [441 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [160 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [448 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [18.1 kB]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,392 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [208 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [161 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,661 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [19.0 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [17.8 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [17.8 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [216 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [58.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,189 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [215 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [96.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [59.2 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,388 B]
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [35.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en        
Fetched 2,726 kB in 2s (1,121 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64 (20120823.1)/dists/precise/main/binary-amd64/Packages   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get  update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ -  Release amd64  (20120823.1)/dists/precise/restricted/binary-amd64/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Please use code tags when posting, the hash mark (#) in advance editor.

---

### Post by Nagle75 on 2012-12-08
I've been using gnome, so I logged out & then back in under Ubuntu & did followed these instructions... [http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu) & I do not have a "software sources" button. I cannot open the "Software Center", "Synaptic", or "Update Manager", as they all crash before opening. I read the link you posted & also tried to edit it from the command line, so I clicked on the link for: "Managing Repositories from the Command Line" but it didn't explain how to properly delete a source. I'm also not sure what you mean by using "code tags" when posting, or where to put them.:oops:

---

### Post by Nagle75 on 2012-12-08
Anyone else have any ideas on how I should proceed?

---

### Post by ibjsb4 on 2012-12-08
Patients please :)

In terminal:

```
cat -n /etc/apt/sources.list
```

And please post

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=code+tags&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=code+tags&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ibjsb4 on 2012-12-08
```
To place something in code tags first highlight it and then click on the hash mark (#).
```

[ATTACH]228402[/ATTACH]

---

### Post by lisati on 2012-12-08
> **Nagle75 said:**
>  I'm also not sure what you mean by using "code tags" when posting, or where to put them.:oops:

When copying the output from a command, type in [noparse]```
, then copy in the output from the command, then type 
```[/noparse]. Doing so will help keep your post readable, and will preserve the formatting of the output from the command.

---

### Post by Nagle75 on 2012-12-08
```
 cat -n /etc/apt/sources.list
     1    deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2    
     3    deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4    deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    20    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    22    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    
    42    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://security.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main 
```

---

### Post by oldos2er on 2012-12-08
> **Nagle75 said:**
>  I'm also not sure what you mean by using "code tags" when posting, or where to put them.:oops:

See [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Try ```
gksudo software-properties-gtk
``` to edit your sources; under the 'Other Software' tab you should be able to untick any boxes referencing CDROM.

---

### Post by Nagle75 on 2012-12-08
Ok, I got to the "software sources" & unchecked the cdrom box & ran sudo apt-get update again. It wont update the "restricted packages", & I also still have the red minus icon on the top right of my desktop. Still cannot open "Software Manager", or "synaptic". 
```

 sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise Release                     
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://extras.ubuntu.com precise Release                          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [195 kB]
Hit http://extras.ubuntu.com precise/main Sources                              
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [65.8 kB]
Hit http://ppa.launchpad.net precise Release.gpg                      
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:12 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [441 kB]
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [448 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:18 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:20 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:21 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:22 http://us.archive.ubuntu.com precise-backports/universe Sources [19.0 kB]
Get:23 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:24 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:25 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:26 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [17.8 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:28 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:29 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [17.8 kB]
Get:31 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:32 http://security.ubuntu.com precise-security/main Sources [58.4 kB]      
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:33 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:34 http://security.ubuntu.com precise-security/universe Sources [18.1 kB]  
Get:35 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:36 http://security.ubuntu.com precise-security/main amd64 Packages [208 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise Release                     
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://extras.ubuntu.com precise Release                          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [195 kB]
Hit http://extras.ubuntu.com precise/main Sources                              
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [65.8 kB]
Hit http://ppa.launchpad.net precise Release.gpg                      
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:12 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [441 kB]
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [448 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:18 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:20 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:21 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:22 http://us.archive.ubuntu.com precise-backports/universe Sources [19.0 kB]
Get:23 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:24 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:25 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:26 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [17.8 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:28 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:29 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [17.8 kB]
Get:31 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:32 http://security.ubuntu.com precise-security/main Sources [58.4 kB]      
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:33 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:34 http://security.ubuntu.com precise-security/universe Sources [18.1 kB]  
Get:35 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:36 http://security.ubuntu.com precise-security/main amd64 Packages [208 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en 
Get:37 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:38 http://security.ubuntu.com precise-security/universe amd64 Packages [58.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en   
Get:39 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:40 http://security.ubuntu.com precise-security/main i386 Packages [215 kB]
Get:41 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:42 http://security.ubuntu.com precise-security/universe i386 Packages [59.2 kB]
Get:43 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,366 kB in 5s (426 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
 sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise Release                     
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://extras.ubuntu.com precise Release                          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [195 kB]
Hit http://extras.ubuntu.com precise/main Sources                              
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [65.8 kB]
Hit http://ppa.launchpad.net precise Release.gpg                      
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:12 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [441 kB]
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [448 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:18 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:20 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:21 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:22 http://us.archive.ubuntu.com precise-backports/universe Sources [19.0 kB]
Get:23 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:24 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:25 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:26 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [17.8 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:28 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:29 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [17.8 kB]
Get:31 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:32 http://security.ubuntu.com precise-security/main Sources [58.4 kB]      
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:33 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:34 http://security.ubuntu.com precise-security/universe Sources [18.1 kB]  
Get:35 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:36 http://security.ubuntu.com precise-security/main amd64 Packages [208 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en 
Get:37 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:38 http://security.ubuntu.com precise-security/universe amd64 Packages [58.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en   
Get:39 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:40 http://security.ubuntu.com precise-security/main i386 Packages [215 kB]
Get:41 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:42 http://security.ubuntu.com precise-security/universe i386 Packages [59.2 kB]
Get:43 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,366 kB in 5s (426 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
 sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise Release                     
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://extras.ubuntu.com precise Release                          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [195 kB]
Hit http://extras.ubuntu.com precise/main Sources                              
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [65.8 kB]
Hit http://ppa.launchpad.net precise Release.gpg                      
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:12 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [441 kB]
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [448 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:18 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:20 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:21 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:22 http://us.archive.ubuntu.com precise-backports/universe Sources [19.0 kB]
Get:23 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:24 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:25 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:26 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [17.8 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:28 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:29 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [17.8 kB]
Get:31 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:32 http://security.ubuntu.com precise-security/main Sources [58.4 kB]      
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:33 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:34 http://security.ubuntu.com precise-security/universe Sources [18.1 kB]  
Get:35 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:36 http://security.ubuntu.com precise-security/main amd64 Packages [208 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en 
Get:37 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:38 http://security.ubuntu.com precise-security/universe amd64 Packages [58.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en   
Get:39 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:40 http://security.ubuntu.com precise-security/main i386 Packages [215 kB]
Get:41 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:42 http://security.ubuntu.com precise-security/universe i386 Packages [59.2 kB]
Get:43 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,366 kB in 5s (426 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

Get:37 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:38 http://security.ubuntu.com precise-security/universe amd64 Packages [58.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en   
Get:39 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:40 http://security.ubuntu.com precise-security/main i386 Packages [215 kB]
Get:41 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:42 http://security.ubuntu.com precise-security/universe i386 Packages [59.2 kB]
Get:43 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,366 kB in 5s (426 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Nagle75 on 2012-12-09
I went back into "software sources" & found a couple more things in the next tab that said "cdrom", so I unchecked those & saved the settings. Then went back into a terminal & ran sudo apt-get update.  Now, I don't get any error messages in the terminal. However, still can't open " Software Manager", "Synaptic", or "Update Manager", & the red minus icon still appears on the top right hand side of my desktop. I'm thinking that the main problem is that I moved the directory for the sources, which is causing everything to act broken. I need to undo this & put it back the way that it's supposed to be.  [http://www.linuxquestions.org/questions/linux-software-2/an-error-occurred-please-run-package-manager-819045/](http://www.linuxquestions.org/questions/linux-software-2/an-error-occurred-please-run-package-manager-819045/)```

Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise Release                     
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources           
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://us.archive.ubuntu.com precise/multiverse Sources           
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [195 kB]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [65.8 kB]  
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [441 kB]
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:11 http://security.ubuntu.com precise-security/main Sources [58.4 kB]      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:13 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [160 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:15 http://us.archive.ubuntu.com precise-updates/main i386 Packages [448 kB]
Get:16 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:17 http://security.ubuntu.com precise-security/universe Sources [18.1 kB]  
Get:18 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:19 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:20 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:22 http://security.ubuntu.com precise-security/main amd64 Packages [208 kB]
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_US
Get:23 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:24 http://security.ubuntu.com precise-security/universe amd64 Packages [58.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en                      
Get:25 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:26 http://security.ubuntu.com precise-security/main i386 Packages [215 kB]
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [59.2 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,247 kB in 3s (658 kB/s)
Reading package lists... Done
```

---

### Post by oldos2er on 2012-12-09
> **Nagle75 said:**
> However, still can't open " Software Manager", "Synaptic", or "Update Manager", & the red minus icon still appears on the top right hand side of my desktop. I'm thinking that the main problem is that I moved the directory for the sources, which is causing everything to act broken.

What exactly did you move, where, and why? Also I'm unsure of the significance of the link you posted.

---

### Post by Nagle75 on 2012-12-09
The significance is that my system acted completely broken after I followed those directions. I didn't really understand the directions,  so I may be wrong in what I was thinking, but I was desperate to get things fixed & it only made things worse. Even as I'm typing this I keep getting this error popping up every few minutes : "system program problem detected". I thought that if I could undo what ever it is that I did in that link that it would fix all the errors I'm getting. Then at least I could get back to working on what I was doing, before all this happened (Brother Printer Drivers).

---

### Post by ibjsb4 on 2012-12-09
Try opening the software center in terminal.

```
software-center
```or

```
gksudo software-center
```Hopefully this will spit out some errors that will help find a fix.

---

### Post by Nagle75 on 2012-12-09
```
 software-center
2012-12-09 12:57:42,226 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-12-09 12:57:42,268 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-12-09 12:57:43,080 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-12-09 12:57:43,400 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-12-09 12:57:43,865 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package dcp8045dlpr:i386 needs to be reinstalled, but I can't find an archive for it.
2012-12-09 12:57:46,473 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

---

### Post by oldos2er on 2012-12-09
You ran the commands in post #8 of [http://www.linuxquestions.org/questi...anager-819045/](http://www.linuxquestions.org/questi...anager-819045/) (it helps greatly to be precise about these things)? Those commands will fix a BADSIG error which is not the error you posted about. However those commands will not hurt your package management software.

"system program problem detected" is unrelated to your previous apt-cdrom problem, in my opinion.

---

### Post by ibjsb4 on 2012-12-09
@oldos2er

Im thinking clean>update>remove/reinstall software-center, but this does not explain other problems.

---

### Post by Nagle75 on 2012-12-09
Could I do a clean install of 12.04 or would that wipe out all my media files?

---

### Post by ibjsb4 on 2012-12-09
You would have to backup all personal files before reinstalling or they will be lost.

Try this (copy/paste) in terminal:

```
sudo apt-get clean && sudo apt-get update && sudo apt-get install --reinstall software-center
```

---

### Post by oldos2er on 2012-12-09
You may want to try ```
sudo apt-get update && sudo apt-get dist-upgrade
``` before a reinstall of the OS.

---

