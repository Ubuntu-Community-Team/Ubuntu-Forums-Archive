---
title: "NOt able to install lsb-core"
date: 2016-08-17
forum: Packaging and Compiling Programs
---

### Post by sudeep4 on 2016-08-17
Hello,

I am not able to install lsb-core in Ubuntu-14.04 64 bit OS. Getting the below error.
============================================================
```
syslab@sudeep:~$ sudo apt-get install lsb-core
[sudo] password for siddharth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lsb-core : Depends: alien (>= 8.36) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
=============================================================

---

### Post by howefield on 2016-08-17
The output of..

```
cat /etc/apt/source.list
```
and
```
ls -al /etc/apt/sources.list.d
```
might help.

You could try fixing the broken packages with

```
sudo apt-get -f install
```

but most likely this is just a first step.

---

### Post by ajgreeny on 2016-08-17
I see you are a new forum user so wonder if you first ran command ```
sudo apt-get update
``` which is necessary to update the available package lists.

---

### Post by sudeep4 on 2016-08-17
Dear Forum Admin,

Below are the results of your suggestions:

```
root@siddharth-hpc:~# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty main restricted multiverse
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates main restricted multiverse
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty universe
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty universe
deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates universe
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security main restricted multiverse
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security main restricted multiverse
deb [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security universe
deb-src [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) trusty main
# deb-src [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) trusty main
```

```
root@siddharth-hpc:~# ls -al /etc/apt/sources.list.d
total 48
drwxr-xr-x 2 root root 4096 Jan  1  2016 .
drwxr-xr-x 6 root root 4096 Aug  2 14:53 ..
-rw-r--r-- 1 root root  189 Aug 10 12:33 google-chrome.list
-rw-r--r-- 1 root root  189 Aug 10 12:33 google-chrome.list.save
-rw-r--r-- 1 root root   56 Aug 10 12:33 openfoam.list
-rw-r--r-- 1 root root   56 Aug 10 12:33 openfoam.list.save
-rw-r--r-- 1 root root  134 Aug 10 12:33 ubuntu-wine-ppa-trusty.list
-rw-r--r-- 1 root root  134 Aug 10 12:33 ubuntu-wine-ppa-trusty.list.save
-rw-r--r-- 1 root root  150 Aug 10 12:33 ubuntu-x-swat-x-updates-trusty.list
-rw-r--r-- 1 root root  150 Aug 10 12:33 ubuntu-x-swat-x-updates-trusty.list.save
-rw-r--r-- 1 root root   70 Aug 10 12:33 virtualbox.list
-rw-r--r-- 1 root root   70 Aug 10 12:33 virtualbox.list.save
```

```
root@siddharth-hpc:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by sudeep4 on 2016-08-17
Dear Forum Moderator,

Below is the output of the update.

```
root@siddharth-hpc:~# sudo apt-get update
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty InRelease
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates InRelease                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security InRelease                    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty Release.gpg                           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security Release.gpg                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates Release                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security Release                      
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty InRelease                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Sources                          
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Sources                    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty Release                                
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main amd64 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse amd64 Packages             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe amd64 Packages               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main i386 Packages                    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted i386 Packages              
Get:2 [http://www.openfoam.org](http://www.openfoam.org) trusty InRelease [3,669 B]                       
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty InRelease                                   
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse i386 Packages              
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Translation-en                   
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main amd64 Packages/DiffIndex               
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Translation-en             
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main i386 Packages/DiffIndex                
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Translation-en             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Translation-en               
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main Sources                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted Sources            
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) trusty/main Translation-en_IN                 
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse Sources            
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe Sources              
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main amd64 Packages           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted amd64 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse amd64 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe amd64 Packages       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main i386 Packages            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_IN                     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted i386 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse i386 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe i386 Packages        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main Translation-en           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse Translation-en     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted Translation-en     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe Translation-en       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main Sources                 
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted Sources           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse Sources           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe Sources             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main amd64 Packages          
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted amd64 Packages    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse amd64 Packages    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe amd64 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main i386 Packages           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted i386 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse i386 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe i386 Packages       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main Translation-en          
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse Translation-en    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted Translation-en    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe Translation-en      
Hit [http://www.openfoam.org](http://www.openfoam.org) trusty/main amd64 Packages                         
Hit [http://www.openfoam.org](http://www.openfoam.org) trusty/main i386 Packages                          
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main Translation-en_IN                      
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main Translation-en                         
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Translation-en_IN                
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Translation-en_IN          
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Translation-en_IN          
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Translation-en_IN            
Fetched 3,741 B in 8s (440 B/s)                                                
Reading package lists... Done
W: GPG error: [http://www.openfoam.org](http://www.openfoam.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6C0DAC728B29D817
```

---

### Post by ajgreeny on 2016-08-17
So have you tried installing **lsb-core** again now that you've refreshed the package lists?

---

### Post by howefield on 2016-08-17
Sorry to ask for more information, but can you post the output of...

```
apt-cache policy alien
```

assuming, that you still have an issue.

---

### Post by sudeep4 on 2016-08-17
Dear Forum Moderator,

Thanks for the response.

yes, I did try to install lsb-core packages externally as .deb files but ultimately getting stuck in alien or dpkg-dev etc.

---

### Post by sudeep4 on 2016-08-17
Dear Forum Admin,

Thank you for your kind response.

siddharth@siddharth-hpc:~$ sudo apt-cache policy alien
[sudo] password for siddharth: 
alien:
  Installed: (none)
  Candidate: 8.90
  Version table:
     8.90 0
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main amd64 Packages
        500 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

Yes, the issue still persists.

---

### Post by sudeep4 on 2016-08-17
Dear Sir,

I am still not able to install lsb-core. Any guide would be highly appreciated.

---

### Post by sudeep4 on 2016-08-18
Dear Forum Admin and Moderators,

I am still facing the issue after refreshing the package list. please guide

```
siddharth@siddharth-hpc:~$ sudo apt-get install lsb-core
[sudo] password for siddharth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
** lsb-core : Depends: alien (>= 8.36) but it is not going to be installed**
E: Unable to correct problems, you have held broken packages.
```

---

### Post by howefield on 2016-08-18
Easy enough to confirm the issue using your sources.list..

```
hugh@trusty:~$ sudo apt edit-sources
[sudo] password for hugh: 

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.tiny

Choose 1-3 [2]: 
Your '/etc/apt/sources.list' file changed, please run 'apt-get update'.
hugh@trusty:~$  sudo apt update
Ign http://extras.ubuntu.com trusty InRelease
Get:1 http://ppa.launchpad.net trusty InRelease [15.4 kB]                      
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://cz.archive.ubuntu.com trusty InRelease                              
Get:3 http://cz.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:4 http://ppa.launchpad.net trusty/main amd64 Packages [30.4 kB]            
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:5 http://cz.archive.ubuntu.com trusty Release [58.5 kB]                    
Ign http://download.opensuse.org  InRelease                                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:6 http://ppa.launchpad.net trusty/main i386 Packages [30.4 kB]             
Get:7 http://download.opensuse.org  Release.gpg [189 B]                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:8 http://download.opensuse.org  Release [1,023 B]                          
Get:9 http://ppa.launchpad.net trusty/main Translation-en [11.8 kB]            
Get:10 http://cz.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:11 http://download.opensuse.org  Packages [3,597 B]                        
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://download.opensuse.org  Translation-en_GB                            
Ign http://download.opensuse.org  Translation-en                               
Get:12 http://cz.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]
Get:13 http://cz.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]    
Get:14 http://cz.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Ign http://ubuntu.excellmedia.net trusty InRelease                             
Ign http://ubuntu.excellmedia.net trusty-updates InRelease                     
Ign http://ubuntu.excellmedia.net trusty-security InRelease
Get:15 http://ubuntu.excellmedia.net trusty Release.gpg [933 B]
Get:16 http://ubuntu.excellmedia.net trusty-updates Release.gpg [933 B]
Get:17 http://ubuntu.excellmedia.net trusty-security Release.gpg [933 B]
Get:18 http://ubuntu.excellmedia.net trusty Release [58.5 kB]
Get:19 http://ubuntu.excellmedia.net trusty-updates Release [62.0 kB]          
Get:20 http://ubuntu.excellmedia.net trusty-security Release [62.0 kB]         
Get:21 http://ubuntu.excellmedia.net trusty/main Sources [1,064 kB]            
Get:22 http://ubuntu.excellmedia.net trusty/restricted Sources [5,433 B]       
Get:23 http://ubuntu.excellmedia.net trusty/multiverse Sources [174 kB]        
Get:24 http://ubuntu.excellmedia.net trusty/universe Sources [6,399 kB]        
Get:25 http://ubuntu.excellmedia.net trusty/main amd64 Packages [1,350 kB]     
Get:26 http://ubuntu.excellmedia.net trusty/restricted amd64 Packages [13.0 kB]
Get:27 http://ubuntu.excellmedia.net trusty/multiverse amd64 Packages [132 kB] 
Get:28 http://ubuntu.excellmedia.net trusty/universe amd64 Packages [5,859 kB] 
Get:29 http://ubuntu.excellmedia.net trusty/main i386 Packages [1,348 kB]      
Get:30 http://ubuntu.excellmedia.net trusty/restricted i386 Packages [13.4 kB] 
Get:31 http://ubuntu.excellmedia.net trusty/multiverse i386 Packages [134 kB]  
Get:32 http://ubuntu.excellmedia.net trusty/universe i386 Packages [5,866 kB]  
Get:33 http://ubuntu.excellmedia.net trusty/main Translation-en_GB [96.8 kB]   
Get:34 http://ubuntu.excellmedia.net trusty/main Translation-en [762 kB]       
Get:35 http://ubuntu.excellmedia.net trusty/multiverse Translation-en_GB [98.3 kB]
Get:36 http://ubuntu.excellmedia.net trusty/multiverse Translation-en [102 kB] 
Get:37 http://ubuntu.excellmedia.net trusty/restricted Translation-en_GB [3,483 B]
Get:38 http://ubuntu.excellmedia.net trusty/restricted Translation-en [3,457 B]
Get:39 http://ubuntu.excellmedia.net trusty/universe Translation-en_GB [7,557 B]
Get:40 http://ubuntu.excellmedia.net trusty/universe Translation-en [4,089 kB] 
Get:41 http://ubuntu.excellmedia.net trusty-updates/main Sources [161 kB]      
Get:42 http://ubuntu.excellmedia.net trusty-updates/restricted Sources [2,061 B]
Get:43 http://ubuntu.excellmedia.net trusty-updates/multiverse Sources [4,463 B]
Get:44 http://ubuntu.excellmedia.net trusty-updates/universe Sources [99.9 kB] 
Get:45 http://ubuntu.excellmedia.net trusty-updates/main amd64 Packages [412 kB]
Get:46 http://ubuntu.excellmedia.net trusty-updates/restricted amd64 Packages [8,875 B]
Get:47 http://ubuntu.excellmedia.net trusty-updates/multiverse amd64 Packages [11.2 kB]
Get:48 http://ubuntu.excellmedia.net trusty-updates/universe amd64 Packages [244 kB]
Get:49 http://ubuntu.excellmedia.net trusty-updates/main i386 Packages [402 kB]
Get:50 http://ubuntu.excellmedia.net trusty-updates/restricted i386 Packages [8,846 B]
Get:51 http://ubuntu.excellmedia.net trusty-updates/multiverse i386 Packages [11.3 kB]
Get:52 http://ubuntu.excellmedia.net trusty-updates/universe i386 Packages [245 kB]
Get:53 http://ubuntu.excellmedia.net trusty-updates/main Translation-en [196 kB]
Get:54 http://ubuntu.excellmedia.net trusty-updates/multiverse Translation-en [5,508 B]
Get:55 http://ubuntu.excellmedia.net trusty-updates/restricted Translation-en [2,266 B]
Get:56 http://ubuntu.excellmedia.net trusty-updates/universe Translation-en [125 kB]
Get:57 http://ubuntu.excellmedia.net trusty-security/main Sources [64.8 kB]    
Get:58 http://ubuntu.excellmedia.net trusty-security/restricted Sources [2,061 B]
Get:59 http://ubuntu.excellmedia.net trusty-security/multiverse Sources [1,896 B]
Get:60 http://ubuntu.excellmedia.net trusty-security/universe Sources [17.4 kB]
Get:61 http://ubuntu.excellmedia.net trusty-security/main amd64 Packages [200 kB]
Get:62 http://ubuntu.excellmedia.net trusty-security/restricted amd64 Packages [8,875 B]
Get:63 http://ubuntu.excellmedia.net trusty-security/multiverse amd64 Packages [3,458 B]
Get:64 http://ubuntu.excellmedia.net trusty-security/universe amd64 Packages [85.3 kB]
Get:65 http://ubuntu.excellmedia.net trusty-security/main i386 Packages [190 kB]
Get:66 http://ubuntu.excellmedia.net trusty-security/restricted i386 Packages [8,846 B]
Get:67 http://ubuntu.excellmedia.net trusty-security/multiverse i386 Packages [3,624 B]
Get:68 http://ubuntu.excellmedia.net trusty-security/universe i386 Packages [85.3 kB]
Get:69 http://ubuntu.excellmedia.net trusty-security/main Translation-en [101 kB]
Get:70 http://ubuntu.excellmedia.net trusty-security/multiverse Translation-en [1,580 B]
Get:71 http://ubuntu.excellmedia.net trusty-security/restricted Translation-en [2,266 B]
Get:72 http://ubuntu.excellmedia.net trusty-security/universe Translation-en [46.8 kB]
Fetched 34.2 MB in 3min 43s (153 kB/s)                                         
Reading package lists... Done
hugh@trusty:~$ sudo apt install lsb-core 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 lsb-core : Depends: alien (>= 8.36) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
hugh@trusty:~$ 
```

I'd be reluctant to offer a solution not knowing what ubuntu.excellmedia.net is or what the repositories contain.

Using a standard default set of repositories (I have a few over and above the default but none that would impact lsb-core) gives no such error.

```
hugh@trusty:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
hugh@trusty:~$ sudo mv /etc/apt/sources.list.save /etc/apt/sources.list
hugh@trusty:~$ sudo apt update
Hit http://ppa.launchpad.net trusty InRelease
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:1 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://download.opensuse.org  InRelease                                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty Release                                    
Get:2 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Hit http://download.opensuse.org  Release.gpg                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://download.opensuse.org  Release                                      
Get:3 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://download.opensuse.org  Packages                                     
Get:4 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:5 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [884 kB] 
Get:6 http://security.ubuntu.com trusty-security/main amd64 Packages [515 kB]  
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:7 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:8 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [368 kB]
Ign http://download.opensuse.org  Translation-en_GB                            
Ign http://download.opensuse.org  Translation-en                               
Get:9 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [14.8 kB]
Get:10 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [845 kB] 
Get:11 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:12 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:13 http://security.ubuntu.com trusty-security/universe amd64 Packages [130 kB]
Get:14 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [369 kB]
Get:15 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [15.2 kB]
Get:16 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [427 kB]
Get:17 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,990 B]
Get:18 http://security.ubuntu.com trusty-security/main i386 Packages [481 kB]  
Get:19 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,661 B]
Get:20 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:21 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [193 kB]
Get:22 http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages [13.3 kB]
Get:23 http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:24 http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages [43.2 kB]
Get:25 http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:26 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:27 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:28 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:29 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:30 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,493 B]
Get:31 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:32 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:33 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:34 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:35 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:36 http://gb.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:37 http://security.ubuntu.com trusty-security/universe i386 Packages [131 kB]
Get:38 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,178 B]
Get:39 http://security.ubuntu.com trusty-security/main Translation-en [284 kB] 
Get:40 http://gb.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:41 http://gb.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Get:42 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,570 B]
Get:43 http://security.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:44 http://security.ubuntu.com trusty-security/universe Translation-en [77.2 kB]
Get:45 http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:46 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]
Get:47 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:48 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:49 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:50 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]    
Get:51 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:52 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:53 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:54 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:55 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B] 
Get:56 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:57 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Fetched 25.1 MB in 13s (1,928 kB/s)                                            
Reading package lists... Done
hugh@trusty:~$ sudo apt install -s lsb-core 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-system1.54.0 libcdr-0.0-0 libcmis-0.4-4 libmspub-0.0-0 libntdb1
  liborcus-0.6-0 libvisio-0.0-0 libwps-0.2-2 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic python-ntdb xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alien at build-essential debhelper debugedit dh-apparmor dpkg-dev g++
  g++-4.8 heirloom-mailx lib32z1 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libmail-sendmail-perl
  librpm3 librpmbuild3 librpmio3 librpmsign1 libstdc++-4.8-dev
  libsys-hostname-long-perl lsb-security m4 ncurses-term pax po-debconf rpm
  rpm-common rpm2cpio
Suggested packages:
  lsb-rpm dh-make rpm-i18n apparmor-easyprof debian-keyring g++-multilib
  g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg libstdc++-4.8-doc
  libmail-box-perl elfutils
The following NEW packages will be installed
  alien at build-essential debhelper debugedit dh-apparmor dpkg-dev g++
  g++-4.8 heirloom-mailx lib32z1 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libmail-sendmail-perl
  librpm3 librpmbuild3 librpmio3 librpmsign1 libstdc++-4.8-dev
  libsys-hostname-long-perl lsb-core lsb-security m4 ncurses-term pax
  po-debconf rpm rpm-common rpm2cpio
0 to upgrade, 30 to newly install, 0 to remove and 80 not to upgrade.
Inst dpkg-dev (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all])
Inst po-debconf (1.0.16+nmu2ubuntu1 Ubuntu:14.04/trusty [all])
Inst dh-apparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [all])
Inst debhelper (9.20131227ubuntu1 Ubuntu:14.04/trusty [all])
Inst librpmio3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst librpm3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst librpmbuild3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst librpmsign1 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst rpm-common (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst rpm2cpio (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst debugedit (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst rpm (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst alien (8.90 Ubuntu:14.04/trusty [all])
Inst at (3.1.14-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libstdc++-4.8-dev (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Inst g++-4.8 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Inst g++ (4:4.8.2-1ubuntu6 Ubuntu:14.04/trusty [amd64])
Inst build-essential (11.6ubuntu6 Ubuntu:14.04/trusty [amd64])
Inst heirloom-mailx (12.5-2+deb7u1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst lib32z1 (1:1.2.8.dfsg-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libalgorithm-diff-perl (1.19.02-3 Ubuntu:14.04/trusty [all])
Inst libalgorithm-diff-xs-perl (0.04-2build4 Ubuntu:14.04/trusty [amd64])
Inst libalgorithm-merge-perl (0.08-2 Ubuntu:14.04/trusty [all])
Inst libsys-hostname-long-perl (1.4-3 Ubuntu:14.04/trusty [all])
Inst libmail-sendmail-perl (0.79.16-1 Ubuntu:14.04/trusty [all])
Inst m4 (1.4.17-2ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst ncurses-term (5.9+20140118-1ubuntu1 Ubuntu:14.04/trusty [all])
Inst pax (1:20120606-2+deb7u1 Ubuntu:14.04/trusty [amd64])
Inst lsb-security (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [amd64])
Inst lsb-core (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [amd64])
Conf dpkg-dev (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all])
Conf po-debconf (1.0.16+nmu2ubuntu1 Ubuntu:14.04/trusty [all])
Conf dh-apparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [all])
Conf debhelper (9.20131227ubuntu1 Ubuntu:14.04/trusty [all])
Conf librpmio3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf librpm3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf librpmbuild3 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf librpmsign1 (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf rpm-common (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf rpm2cpio (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf debugedit (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf rpm (4.11.1-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf alien (8.90 Ubuntu:14.04/trusty [all])
Conf at (3.1.14-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libstdc++-4.8-dev (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf g++-4.8 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf g++ (4:4.8.2-1ubuntu6 Ubuntu:14.04/trusty [amd64])
Conf build-essential (11.6ubuntu6 Ubuntu:14.04/trusty [amd64])
Conf heirloom-mailx (12.5-2+deb7u1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf lib32z1 (1:1.2.8.dfsg-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libalgorithm-diff-perl (1.19.02-3 Ubuntu:14.04/trusty [all])
Conf libalgorithm-diff-xs-perl (0.04-2build4 Ubuntu:14.04/trusty [amd64])
Conf libalgorithm-merge-perl (0.08-2 Ubuntu:14.04/trusty [all])
Conf libsys-hostname-long-perl (1.4-3 Ubuntu:14.04/trusty [all])
Conf libmail-sendmail-perl (0.79.16-1 Ubuntu:14.04/trusty [all])
Conf m4 (1.4.17-2ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf ncurses-term (5.9+20140118-1ubuntu1 Ubuntu:14.04/trusty [all])
Conf pax (1:20120606-2+deb7u1 Ubuntu:14.04/trusty [amd64])
Conf lsb-security (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [amd64])
Conf lsb-core (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [amd64])
hugh@trusty:~$ 
```

---

### Post by sudeep4 on 2016-08-19
Dear Forum Admin,

I am sorry to bother you again but I did the steps mentioned by you but looks like the issue still persists.

Please note that we are using Ubuntu 14.04

```
siddharth@siddharth-hpc:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
```

```
@siddharth-hpc:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
[sudo] password for siddharth: 
siddharth@siddharth-hpc:~$ sudo mv /etc/apt/sources.list.save /etc/apt/sources.list
```

```
siddharth@siddharth-hpc:~$ sudo apt update
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates InRelease                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security InRelease                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates Release.gpg                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.4 kB]                      
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security Release.gpg                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates Release                       
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.4 kB]                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Sources                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Sources                      
Get:4 [http://www.openfoam.org](http://www.openfoam.org) trusty InRelease [3,669 B]                       
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty InRelease                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main amd64 Packages                   
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse amd64 Packages             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main amd64 Packages/DiffIndex               
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main i386 Packages                    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse i386 Packages              
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main i386 Packages/DiffIndex                
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe i386 Packages                
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Translation-en                   
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Translation-en             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Translation-en             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_IN                     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main Sources                  
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted Sources            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse Sources            
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe Sources              
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main amd64 Packages           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted amd64 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse amd64 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe amd64 Packages       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main i386 Packages            
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted i386 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse i386 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe i386 Packages        
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/main Translation-en           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/multiverse Translation-en     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/restricted Translation-en     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-updates/universe Translation-en       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main Sources                 
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted Sources           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse Sources           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe Sources             
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main amd64 Packages          
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted amd64 Packages    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse amd64 Packages    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe amd64 Packages      
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main i386 Packages           
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted i386 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse i386 Packages     
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe i386 Packages       
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/main Translation-en          
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/multiverse Translation-en    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/restricted Translation-en    
Hit [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty-security/universe Translation-en      
Hit [http://www.openfoam.org](http://www.openfoam.org) trusty/main amd64 Packages                         
Hit [http://www.openfoam.org](http://www.openfoam.org) trusty/main i386 Packages                          
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main Translation-en_IN                      
Ign [http://www.openfoam.org](http://www.openfoam.org) trusty/main Translation-en                         
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/main Translation-en_IN                
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/multiverse Translation-en_IN          
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/restricted Translation-en_IN          
Ign [http://ubuntu.excellmedia.net](http://ubuntu.excellmedia.net) trusty/universe Translation-en_IN            
Fetched 34.6 kB in 8s (4,281 B/s)                                              
Reading package lists... Done
siddharth@siddharth-hpc:~$ sudo apt install -s lsb-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lsb-core : Depends: alien (>= 8.36) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by howefield on 2016-08-19
Please stop repeating the issue, it is clear what the problem is. And please use code tags for terminal output.

I didn't give you any steps, only an observation that with your sources.list the issue is easy to confirm, but also that using the main Ubuntu repositories results in lsb-core installing without problem.

---

### Post by sudeep4 on 2016-08-20
Thanks for the suggestions. the issue stands resolved

---

### Post by ajgreeny on 2016-08-21
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

Can we assume that what you needed to do was change the software-sources to the ubuntu main repositories?  If so can you please post and tell us as it helps future forum searchers.

---

