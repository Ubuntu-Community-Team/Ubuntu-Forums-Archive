---
title: "VLC Player has been removed, now I can't reinstall it"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by jakkups on 2012-11-14
I don't know what happened. I clicked on update and it removed some stuff including VLC player. But now when I go to reinstall it I can't do it and I'm at a loss at what to do. 

This is what it said is **_Ubuntu Software center_**
> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.1-4) but 2.0.1-4 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

**_Terminal_**
> sudo apt-get install vlc
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 2.0.1-4) but it is not going to be installed
       Depends: libavcodec53 (>= 4:0.8-1~) but it is not going to be installed or
                libavcodec-extra-53 (>= 4:0.8-1~) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.1-4) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.1-4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Also can't do it in **_Synaptic Manager_**
> Could not mark all upgrades for installation or upgrade
The following packages have unresolvable dependencies.
Make sure all the required repositories are addedand enabled in the 'Repositories' option under 'Settings'.
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libavcodec53 but it is not going to be installed or
 	libavcodec-extra-53 but it is not going to be installed
 Recommends: vlc-plugin-notify but it is not going to be installed
 Recommends: vlc-plugin-pulse but it is not going to be installed



I'm running Ubuntu 12.04 on an Acer Aspire Revo if that helps out at all. Please help me, thank you in advance.

---

### Post by critin on 2012-11-14
Have you installed "Ubuntu restricted extras"?  If not, find it in Software Center.  It may help with some dependencies.

---

### Post by Paqman on 2012-11-14
Hmm, try refreshing your package lists and if that doesn't work try switching to a different download server. For some reason the one you're connected to isn't giving you the packages you need.

---

### Post by jakkups on 2012-11-14
> **critin said:**
> Have you installed "Ubuntu restricted extras"?  If not, find it in Software Center.  It may help with some dependencies.

> **Paqman said:**
> Hmm, try refreshing your package lists and if that doesn't work try switching to a different download server. For some reason the one you're connected to isn't giving you the packages you need.

Did both of these, hasn't solved the problem though.

---

### Post by ibjsb4 on 2012-11-14
"Make sure all the required repositories are added and enabled in the 'Repositories' option under 'Settings'."

Do you have all of them checked?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by jakkups on 2012-11-14
> **ibjsb4 said:**
> "Make sure all the required repositories are added and enabled in the 'Repositories' option under 'Settings'."

Do you have all of them checked?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Yep, have them all checked, still not playing ball with me though.

---

### Post by sandyd on 2012-11-14
What PPAs do you have installed?

---

### Post by jakkups on 2012-11-14
> **sandyd said:**
> What PPAs do you have installed?

[IMG]http://i47.tinypic.com/6olt88.png[/IMG]

---

### Post by mc4man on 2012-11-14
What doesn't look right from orig. post
> Depends: libavcodec-extra-53 (>= 4:0.8-1~) but [COLOR="Red"]4:0.8.1ubuntu1 [/COLOR]is to be installed
Depends: libavutil-extra-51 (>= 4:0.8-1~) but [COLOR="Navy"]4:0.8.4ubuntu0.12.04.1 [/COLOR]is to be installed

libavcodec & libavutil should be the same version which currently is 
4:0.8.4ubuntu0.12.04.1

Search libavcodec in synaptic & see if 4:0.8.4ubuntu0.12.04.1 is available

---

### Post by jakkups on 2012-11-14
> **mc4man said:**
> What doesn't look right from orig. post

libavcodec & libavutil should be the same version which currently is 
4:0.8.4ubuntu0.12.04.1

Search libavcodec in synaptic & see if 4:0.8.4ubuntu0.12.04.1 is available

OK I was able to get both of those to be the same versions but it still won't let me install VLC player. Am I doing something wrong?

---

### Post by jakkups on 2012-11-14
Also I just remembered that this happened after I did a partial upgrade if that helps.

---

### Post by Paqman on 2012-11-15
> **jakkups said:**
> Also I just remembered that this happened after I did a partial upgrade if that helps.

Ah. Partial upgrades are a bad idea. You generally only get them if the repos are in an unstable condition and the package manager isn't able to resolve all the dependencies require to do a full update.

Are you running the testing branch (Raring Ringtail)? Getting a partial upgrade offered is extremely rare unless you're testing. 

Either way, the best way to resolve a problem with the repos is to wait a day or two then try again. Sometimes switching to a different server helps, but you've already done that once.

---

### Post by jakkups on 2012-11-15
> **Paqman said:**
> Ah. Partial upgrades are a bad idea. You generally only get them if the repos are in an unstable condition and the package manager isn't able to resolve all the dependencies require to do a full update.

Are you running the testing branch (Raring Ringtail)? Getting a partial upgrade offered is extremely rare unless you're testing. 

Either way, the best way to resolve a problem with the repos is to wait a day or two then try again. Sometimes switching to a different server helps, but you've already done that once.

This is what version I'm running.

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


---

### Post by Paqman on 2012-11-15
OK, that's the regular release then. So you've definitely refreshed your sources and switched to a different server? Have you added or removed any new repos, PPAs, etc lately?

---

### Post by jakkups on 2012-11-15
> **Paqman said:**
> OK, that's the regular release then. So you've definitely refreshed your sources and switched to a different server? Have you added or removed any new repos, PPAs, etc lately?

Since this partial upgrade added videolan/master-daily PPA and added libavcodec & libavutil 4:0.8.4ubuntu0.12.04.1 repos.

Unchecked and then rechecked all the software sources and chose a different server aswell.

---

### Post by Paqman on 2012-11-15
Righto, you may not be running a testing branch of Ubuntu, but you've got a testing PPA enabled. That's where the breakage has come from. For future reference, anything calling itself a "daily" is likely to be unstable, and should be treated with a bit of caution. 

If you do enable some unstable sources and get offered a "partial upgrade", open up a tool like [Synaptic]("apt:synaptic") and check exactly what will be removed before you decide to either accept or refuse the upgrade.

Uncheck that PPA, open a terminal with Ctrl-T and run:
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install vlc

```

This will get a list of packages minus all the stuff from the PPA, remove anything you don't need installed, then try to install VLC. Post back any errors you get.

---

### Post by jakkups on 2012-11-15
Everything worked fine up until the installation part. This is what I got back:

> sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Paqman on 2012-11-15
> **jakkups said:**
> E: Unable to correct problems, you have held broken packages.

Right, we're getting there. Try:
```
sudo apt-get -f install
```
Or if you have Synaptic installed it has a filter to locate and fix broken packages. They both do the same thing AFAIK.

---

### Post by jakkups on 2012-11-15
OK, this is what I got:

> sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mc4man on 2012-11-15
If (for the moment or for good) you want to return to the ubuntu repo vlc vs. the videolan ppa version try this - 

Disable the ppa in sources (if not already done

```
sudo apt-get purge vlc-data 
```
```
sudo apt-get update && sudo apt-get install vlc
```
see what occurs ...

---

### Post by jakkups on 2012-11-15
> **mc4man said:**
> If (for the moment or for good) you want to return to the ubuntu repo vlc vs. the videolan ppa version try this - 

Disable the ppa in sources (if not already done

```
sudo apt-get purge vlc-data 
``````
sudo apt-get update && sudo apt-get install vlc
```see what occurs ...

Heres what I got:

> sudo apt-get purge vlc-data 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc-data is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get update && sudo apt-get install vlc
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [7,659 B]                  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [9,946 B]            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]               
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_GB [96.4 kB]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_GB [79.8 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_GB [2,406 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Fetched 16.8 MB in 48s (344 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.3+git20121114+r428-0~r41~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Still no luck I'm afraid

---

### Post by mc4man on 2012-11-15
Well in post 8 you showed the videolan/master-daily ppa enabled.
Now you are trying to install from the videolan/stable-daily ppa

Did you have both enabled before or just add the stable ppa before this latest attempt?
I'd suggest for the moment removing ALL vlc ppa's, updating & trying to install the Ubuntu version of vlc (2.0.3-0ubuntu0.12.04.1

What does this show?
```
ls /etc/apt/sources.list.d/
```

---

### Post by jakkups on 2012-11-15
It shows this

> ls /etc/apt/sources.list.d/
hizo-logiciels-precise.list            sgringwe-beatbox-precise.list
hizo-logiciels-precise.list.save       sgringwe-beatbox-precise.list.save
jd-team-jdownloader-precise.list       videolan-stable-daily-precise.list
jd-team-jdownloader-precise.list.save  videolan-stable-daily-precise.list.save


---

### Post by mc4man on 2012-11-16
nv for the moment

---

### Post by jakkups on 2012-11-17
Any more ideas fellas?

---

### Post by ranger1021994 on 2012-11-17
This happened with me.
But in my case a simple restart would fix my problem.

Try manually installing all components

---

### Post by jakkups on 2012-11-17
> **ranger1021994 said:**
> This happened with me.
But in my case a simple restart would fix my problem.

Try manually installing all components

Done that and it's back on my PC again. Problem solved.

---

