---
title: "[SOLVED] reloading synaptic I get this response is something wrong?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-13
I'm new to ubuntu and was wondering if anyone can answer this. When I go to system-administration-synaptic package manager and I click on reload it seems to reload but I always see this at the end. Just would like to know is this usual or is there something else I need to do. This is what it says after reloading: failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release) unable to find expected entry non-free gksudo/binary-i386/packages in meta index file (malformed release file?) Some index files failed to download, they have been ignored or old ones used instead.

---

### Post by plucky on 2008-08-14
> **brucegriffin said:**
> I'm new to ubuntu and was wondering if anyone can answer this. When I go to system-administration-synaptic package manager and I click on reload it seems to reload but I always see this at the end. Just would like to know is this usual or is there something else I need to do. This is what it says after reloading: failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release) unable to find expected entry non-free gksudo/binary-i386/packages in meta index file (malformed release file?) Some index files failed to download, they have been ignored or old ones used instead.


Open a terminal **Applications > Accessories > Terminal** and input ```
sudo apt-get update
```.It will ask for your login password,but will not echo the input.Post back the output if you get any errors.

Also post output of these commands ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/medibuntu.list
```

Good Luck

---

### Post by brucegriffin on 2008-08-14
Thanks for reply, here is the output from sudo apt-get updates there seems to be errorsHit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-freegksudo Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/gedit Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy//etc/apt/sources.list Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-freegksudo Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/gedit Packages   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy//etc/apt/sources.list Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Packages 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Packages   
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-freegksudo Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/gedit Packages   
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy//etc/apt/sources.list Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Packages 
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Packages   
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-freegksudo/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-freegksudo/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/gedit/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/gedit/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy//etc/apt/sources.list/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy//etc/apt/sources.list/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/(Source/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/(Source/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Code)/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/Code)/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
dasleyefox@dasleyefox-desktop:~$ 

results from cat/etc/apt/sources.list

 cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory


results from cat/etc/apt/sources.list.d/medibuntu.list

cat/etc/apt/sources.list.d/medibuntu.list
bash: cat/etc/apt/sources.list.d/medibuntu.list: No such file or directory

It appears they are not there, if you can post what I need to do to get them, thanks.

---

### Post by halitech on 2008-08-14
the first few seem to be there but I'm guessing there is a problem with the Packages.gz file

[http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/)

the last 2 on the list don't exist as folders though...

[http://packages.medibuntu.org/dists/hardy/](http://packages.medibuntu.org/dists/hardy/)

---

### Post by Elfy on 2008-08-14
I think that medibuntu is up and down which is why the error.

cat/etc/apt/sources.list

needs a gap after cat 

```
cat /etc/apt/sources.list
```

---

### Post by brucegriffin on 2008-08-14
Results since putting gap after cat

cat /etc/apt/sources.list

cat /etc/apt/sources.list
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-freegksudo gedit /etc/apt/sources.list # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free (Source Code)
  results for cat /etc/apt/sources.list.d/medibuntu.list

 cat /etc/apt/sources.list.d/medibuntu.list
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

That looks much better Thank You but when I do a sudo apt-get update at the end if you look is there something wrong, here is what I get when I do a sudo apt-get update

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-freegksudo Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/gedit Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy//etc/apt/sources.list Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Translation-en_US    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
Fetched 189B in 1s (175B/s)
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  non-freegksudo/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
I also get the same thing when I reload synaptic, thanks again for the replies.

---

### Post by Elfy on 2008-08-14
I'd be inclined to edit the medibuyntu list - delete the whole contents and start again.

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

delete the contents and then save, then run these 2 seperate commands

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Please - when you are posting long lists use code tags - either the # buttonon the advance edit/new reply box or type

[noparse]```
[/noparse]at the beginning of the list and [noparse]
```[/noparse]

---

### Post by brucegriffin on 2008-08-14
I deleted and then put in the two commands result from first command, it seems to have the same result at the end of the second command. I did tag but forget how to do it Sorry. Thanks for the reply.

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
--12:25:42--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

12:25:43 (14.03 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]


result from second command

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-freegksudo Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/gedit Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy//etc/apt/sources.list Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Translation-en_US                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  non-freegksudo/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nothingspecial on 2008-08-14
From other posts and looking at my own synaptic, I think there`s something up with the medibuntu repo at the moment.

---

### Post by plucky on 2008-08-14
You need to edit your **sources.list** file and delete this part of the first line
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-freegksudo gedit /etc/apt/sources.list

To edit the sources.list file open a terminal and copy and paste this command```
gksudo gedit /etc/apt/sources.list
```

Delete the first part of the line up to the #,then save the file and then try ```
sudo apt-get update
```.

You should not get any errors.

Good Luck

---

### Post by brucegriffin on 2008-08-14
this is how my source list appears after doing the first command you suggest and then deleting the first line, and saving

 # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free (Source Code)


Then when I enter the scond command sudo apt-get update this is the result


sudo apt-get update
[sudo] password for dasleyefox: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Packages 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Packages   
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Packages 
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Packages   
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/(Source/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/(Source/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Code)/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/Code)/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Elfy on 2008-08-14
Medibuntu is sometimes down at the moment, as I type [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is working, but could be down again once I've posted.

Assuming that the sources lists are now correct there is nopt anything you can do about that.

Check that the medibutu list looks ok - all lines without a # should start either deb or deb-src - anything else is not right - check with the 

```
cat /etc/apt/sources.list.d/medibuntu.list
```like this

> ## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Please surround your lists with code tags

```
at the beginning of the list and 
```

it makes life much easier for people reading your posts.

---

### Post by brucegriffin on 2008-08-14
When I enter cat /etc/apt/sources.list.d/medibuntu.list this is my output

cat /etc/apt/sources.list.d/medibuntu.list
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


Then when I enter sudo apt-get update this is my result, does the result at the end mean the site to download is down.

sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/(Source Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/Code) Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  (Source/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2008-08-14
I have just seen you have medibuntu in both your sources.list file and medibuntu.list file.

From the bottom of your sources.list file

> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free (Source Code)


Remove these two lines from the sources.list file and try again.

I would also recommend you put a # in front of all the deb-src lines in your sources.list file as you probably don't need the source listings of the software you download.

Good Luck

---

### Post by brucegriffin on 2008-08-14
I did as you suggested plucky and deleted the two entries and also put the # signs where you suggested and it seems to be working properly now. Thank You very much. I put solved in the title but it didn't seem to take. I would have liked to tag it solved but don't know how.

---

### Post by Elfy on 2008-08-14
Use the mark thread in thread tools at the top

---

### Post by brucegriffin on 2008-08-14
Thank you forestpixie, I marked the thread.

---

