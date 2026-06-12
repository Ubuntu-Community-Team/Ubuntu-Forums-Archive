---
title: "Error when I put sudo apt-get update"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by LethalBoy on 2008-11-28
How can I solve this problem?

Here's part of the error:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources                
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources             
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages             
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources              
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages               
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages                          
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages                    
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages                         
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                       
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources                          
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources                        
  404 Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources                           
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources                
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources                     
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages                  
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages            
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages                   
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources                    
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources                
  404 Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources                   
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources             
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources              
  404 Not Found [IP: 91.189.88.40 80]
65% [Connecting to packages.freecontrib.org (34.52.53.34)]

---

### Post by Paqman on 2008-11-28
404 means your system can't connect to the server. Try going to System > Admin > Software Sources > Download from > Other > Select Best Server. It should locate a good server for you.

EDIT: Hang on! *Breezy!* You're going to struggle to find a repo open for that anywhere. It's really out-of-date. You need to get your hands on a more recent version of Ubuntu. That one is three years old, and no longer supported.

---

### Post by LethalBoy on 2008-11-28
It gives me the samething... and when I'm downloading the package information it gives me alot of failed things

---

### Post by HereInOz on 2008-11-28
Breezy is pretty old and well out of support.  It could be that those links just don't work any more - no longer in existence.  You may have to upgrade to a later version of Ubuntu.

---

### Post by LethalBoy on 2008-11-28
I'm using 8.10

---

### Post by Paqman on 2008-11-28
> **LethalBoy said:**
> I'm using 8.10

Ok, how did your sources.list end up looking for Breezy packages? Have you edited it?

If so, edit it back, replacing all references to Breezy with the word Intrepid. Gedit can find and replace them all for you in one go.

---

### Post by LethalBoy on 2008-11-28
> **Paqman said:**
> Yep, that's because you're trying to connect to something that isn't there any more. Namely the repositories of software for Ubuntu 5.10 (Breezy Badger). If you want to be able to install software you need to install either 8.04 (Hardy Heron) or the new 8.10 (Intrepid Ibex).

What!! I'm using 8.10!! I updated yesterday

---

### Post by adult swim on 2008-11-28
you are going to need to change them as Paqman suggested because for some reason your sources.list didnt update
you can edit them by running ```
gksudo gedit /etc/apt/sources.list
``` and then do a search/replace

---

### Post by LethalBoy on 2008-11-28
Hmm I think I need the complete sources.lst of Ubuntu 8.10!!

Anyone can put it here please?

---

### Post by adult swim on 2008-11-28
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release Candidate i386 (20081022)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu intrepid partner
#deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
```

---

### Post by LethalBoy on 2008-11-28
Ok, that solved my problem!! Thanks for your help adult swim & Paqman

God bless you!! and BTW I love Ubuntu so far :)

---

