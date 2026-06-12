---
title: "sudo apt-get update errors"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Winchman on 2012-08-22
Hi, 
I am completely new to Ubuntu 12.04 LTS and am struggling to find  a solution to this problem:
When I type ***'sudo apt-get update'*** into the command terminal I am getting the following 2 error messages:

W: Failed to fetch [http://archive.canonical.com/(lsb_release/dists/-sc)/partner/source/Sources]("http://archive.canonical.com/%28lsb_release/dists/-sc%29/partner/source/Sources")  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch [http://archive.canonical.com/(lsb_release/dists/-sc)/partner/binary-i386/Packages]("http://archive.canonical.com/%28lsb_release/dists/-sc%29/partner/binary-i386/Packages")  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

Could someone help me with this?

I have tried various suggestions including trying different download servers.

Many thanks

---

### Post by eneskuray on 2012-08-22
did you try on  different days ? can it be sometimes

---

### Post by Lisiano on 2012-08-22
It seems you have manually modified /etc/apt/sources.list
You will need to find either find all occurances of ```
(lsb_release -sc)
``` and change it to ```
$(lsb_release -sc)
``` or to ```
precise
```

As an example, here is my sources.list
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe #Added by software-properties
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by Winchman on 2012-08-22
Thanks Lisiano, but in simple terms, step by step, how do I carry out the modifications that you are suggesting?

---

### Post by Winchman on 2012-08-22
> **eneskuray said:**
> did you try on  different days ? can it be sometimes
yes have been trying since Sunday !

---

### Post by Lisiano on 2012-08-22
Sorry.
Press Alt+F2 (Or do it in a terminal via Ctrl+Alt+T) and type in ```
gksudo gedit /etc/apt/sources.list
```
You will be asked for your password, provide it. Now Gedit will open and show sources.list, try to make it look like the example I posted (Or you can blatantly copy paste it) then save it. Do a normal ```
sudo apt-get update
``` and your sources should get downloaded.

If you are afraid to modify it and don't want to use the one I posted, please just copy paste the contents here and I will modify it appropriately.

---

### Post by Winchman on 2012-08-22
Thanks Lisiano. I tried to follow your instructions as best I could, but still can't download missing bits. 

This is how the errors look right now:


mps@mps-E122X:~$ sudo apt-get update
[sudo] password for mps: 

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                  
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc) InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security InRelease         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc) Release.gpg                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                     
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc) Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                      
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc)/partner TranslationIndex                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                     
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release [49.6 kB]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Err [http://archive.canonical.com](http://archive.canonical.com) -sc)/partner Sources                          
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex  
Err [http://archive.canonical.com](http://archive.canonical.com) -sc)/partner i386 Packages                    
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex             
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [158 kB]       
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc)/partner Translation-en_GB                
Ign [http://archive.canonical.com](http://archive.canonical.com) -sc)/partner Translation-en                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                  
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [49.2 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en           
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [378 kB]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [125 kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Sources [40.6 kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Sources [11.4 kB]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main i386 Packages [161 kB]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe i386 Packages [41.2 kB]
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [181 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [74.5 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Translation-en
Fetched 1,365 kB in 4s (326 kB/s)                
W: Failed to fetch http://archive.canonical.com/$(lsb_release/dists/-sc)/partner/source/Sources  404  Not Found

W: Failed to fetch http://archive.canonical.com/$(lsb_release/dists/-sc)/partner/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
mps@mps-E122X:~$ 

[B]This is how the the sources.list now looks:
[/B]
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb http://archive.canonical.com/$(lsb_release -sc) partner
deb-src http://archive.canonical.com/$(lsb_release -sc) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by Lisiano on 2012-08-22
> **Winchman said:**
> ```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/$(lsb_release -sc) partner
deb-src http://archive.canonical.com/$(lsb_release -sc) partner
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
```
It seems it won't work with shell exapansion, also I can see that you already have the correct line. Just remove the last 4 lines (Yes, the last 4). You don't need the last 2 instances since you already have it here > **Winchman said:**
> ```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

```

---

### Post by Winchman on 2012-08-22
Not quite sure I understand correctly what needs to be done.
 I'm scared of making things worse with my woeful lack of knowledge!
It might be better as you originally suggested if you  were to post the correct text for me to copy and paste into sources.list
thanks

---

### Post by Lisiano on 2012-08-22
Sorry again. I start typing too much and forget to keep it short and simple.
Basically just replace the content with this.
```
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by Winchman on 2012-08-22
Did as instructed and now getting the following:
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
mps@mps-E122X:~$ 

thanks

---

### Post by Lisiano on 2012-08-22
Strange. I didn't leave a duplicate in your list. Either way this line in particular shouldn't cause any problems. I think it will go away the next time you try to run an update.

---

### Post by NikTh on 2012-08-22
Hi , 
please open a terminal and copy-paste from here to your terminal for more accuracy.

```
sudo cp /etc/apt/sources.list /etc/apt/sources-bad
sudo wget "http://pastebin.com/raw.php?i=t7A5NFk3" -O /etc/apt/sources.list
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```If errors occurred again , then give the results of this command 
```
ls /etc/apt/sources.list.d/
```You can put the results inside ```
 tags so can be easily readable .
[noparse][code]results here
```[/noparse]
Thanks

---

### Post by Winchman on 2012-08-23
thanks. Here is latest result:
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

mps@mps-E122X:~$ ls /etc/apt/sources.list.d/

precise-partner.list        tualatrix-ppa-precise.list.save
precise-partner.list.save   tualatrix--precise.list
tualatrix-ppa-precise.list  tualatrix--precise.list.save
mps@mps-E122X:~$

---

### Post by sandyd on 2012-08-23
post output of
```

cat /etc/apt/sources.list.d/precise-partner.list

```

---

### Post by Winchman on 2012-08-23
mps@mps-E122X:~$ cat /etc/apt/sources.list.d/precise-partner.list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center

mps@mps-E122X:~$

---

### Post by oldos2er on 2012-08-23
```
sudo rm /etc/apt/sources.list.d/precise-partner.*

sudo apt-get update
```

---

### Post by Winchman on 2012-08-23
> **oldos2er said:**
> ```
sudo rm /etc/apt/sources.list.d/precise-partner.*

sudo apt-get update
```
Thanks [[COLOR=#DD4814]**oldos2er**[/COLOR]]("http://ubuntuforums.org/member.php?u=338320").that appears to have finally sorted it out.
Grateful thanks to all who helped

---

### Post by sebin on 2012-09-02
> **Lisiano said:**
> It seems it won't work with shell exapansion, also I can see that you already have the correct line. Just remove the last 4 lines (Yes, the last 4). You don't need the last 2 instances since you already have it here

I am having almost the same doubt

Is these two line are the same?> deb http://archive.canonical.com/$(lsb_release -sc) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner 

---

### Post by sebin on 2012-09-02
> **sebin said:**
> I am having almost the same doubt

Is these two line are the same?


Ah! i got it.

$ lsb_release -sc
precise


:)

---

