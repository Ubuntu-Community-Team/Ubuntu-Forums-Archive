---
title: "Install menu is missing from Ubuntu Software Center"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by cadefoster on 2013-11-13
Hi I'm a newbie here,

This is not the first time I've installed Ubuntu on my PC, I've been using it for years but only for office work like typing, printing etc.

I would like to install entertainement apps like VLC through GUI i.e. Ubuntu Software Center but the install menu is absent for all the apps I've searched for.

Per these links it should be there, but it's not:

[http://www.wikihow.com/Install-Software-in-Ubuntu](http://www.wikihow.com/Install-Software-in-Ubuntu)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Screenshot is attached, and I've the latest 13.10 version.

Thanks in advance!

---

### Post by philinux on 2013-11-13
Click more info button first. :P

---

### Post by cadefoster on 2013-11-14
> **philinux said:**
> Click more info button first. :P

Of course, that's the first thing I did but there is nothing there except "use this source" button which doesn't install anything at all. Screenshot coming soon in a few minutes.

---

### Post by cadefoster on 2013-11-14
Here's a screenshot. Using "Use this source" doesn't anything at all.

[ATTACH=CONFIG]247811[/ATTACH]

---

### Post by philinux on 2013-11-14
> **s2nasir said:**
> Of course, that's the first thing I did but there is nothing there except "use this source" button which doesn't install anything at all. Screenshot coming soon in a few minutes.

Righto - then lets have a look at your sources.

```
cat /etc/apt/sources.list | pastebinit
```

---

### Post by cadefoster on 2013-11-14
Doing so gives me this:

[ATTACH=CONFIG]247812[/ATTACH]

Also, when I go to VLC's website and try to download VLC app it keeps on looking for apt. When I try 'choose' there is no app/prgoram to open or download it:

[ATTACH=CONFIG]247813[/ATTACH]

---

### Post by philinux on 2013-11-14
```
sudo apt-get install pastebinit
```

Install it then and then lets see your sources list.

---

### Post by vasa1 on 2013-11-14
First install pastebinit, if you can. **Then** run **cat /etc/apt/sources.list | pastebinit**

---

### Post by cadefoster on 2013-11-14
It says it cannot locate it :(

[ATTACH=CONFIG]247815[/ATTACH]

---

### Post by philinux on 2013-11-14
> **s2nasir said:**
> It says it cannot locate it :(



Ah ok then thats an indication that something amiss.

So. Just

```
cat /etc/apt/sources.list
```

Copy and paste the result into your next post. Put code tags around it though. highlight the text in your post then the # key in the editior to wrap it with code tags. Makes it easier to read.

---

### Post by vasa1 on 2013-11-14
Is this Ubuntu installed in your office? Perhaps the IT admin has disabled installation of software? Just a thought!

---

### Post by cadefoster on 2013-11-14
Here it is:[B]

```
sulaco@sulaco-Rev-1-0:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy universe
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
sulaco@sulaco-Rev-1-0:~$ 
```

[/B]> **vasa1 said:**
> Is this Ubuntu installed in your office? Perhaps  the IT admin has disabled installation of software? Just a  thought!No, I installed it myself on a home computer. During installation, I don't recall unchecking any such option to my best knowledge.

---

### Post by philinux on 2013-11-14
Sources list is fine. What does this spit out. Post back any errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cadefoster on 2013-11-14
Yes, it errors out somewhere in the middle (see bold code)

```
sulaco@sulaco-Rev-1-0:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for sulaco: 
Ign http://extras.ubuntu.com saucy InRelease                                   
Ign http://security.ubuntu.com saucy-security InRelease                        
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://security.ubuntu.com saucy-security Release.gpg                      
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://security.ubuntu.com saucy-security Release                          
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://security.ubuntu.com saucy-security/main Sources                     
Hit http://security.ubuntu.com saucy-security/restricted Sources               
Hit http://security.ubuntu.com saucy-security/universe Sources                 
Hit http://security.ubuntu.com saucy-security/multiverse Sources               
Hit http://security.ubuntu.com saucy-security/main i386 Packages               
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages         
Hit http://security.ubuntu.com saucy-security/universe i386 Packages           
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages         
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://security.ubuntu.com saucy-security/main Translation-en              
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en        
Hit http://security.ubuntu.com saucy-security/restricted Translation-en        
Hit http://security.ubuntu.com saucy-security/universe Translation-en          
Ign http://security.ubuntu.com saucy-security/main Translation-en_US           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US       
[B]Err http://pk.archive.ubuntu.com saucy InRelease         
  
Err http://pk.archive.ubuntu.com saucy-updates InRelease 
  
Err http://pk.archive.ubuntu.com saucy-backports InRelease
  
Err http://pk.archive.ubuntu.com saucy Release.gpg       
  Unable to connect to pk.archive.ubuntu.com:http:
Err http://pk.archive.ubuntu.com saucy-updates Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Err http://pk.archive.ubuntu.com saucy-backports Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease  

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg  Unable to connect to pk.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]
sulaco@sulaco-Rev-1-0:~$ 


```

---

### Post by philinux on 2013-11-14
Top right gear icon, system settings, software and updates. 

Change the server to Main. and try to update upgrade again.

---

### Post by cadefoster on 2013-11-14
No errors, and this time it updated/upgraded a lot of stuff. What do I do now?

---

### Post by philinux on 2013-11-14
> **s2nasir said:**
> No errors, and this time it updated/upgraded a lot of stuff. What do I do now?

Ah though so. That just means your local country servers were off line you can leave it on main or change it back anytime.

Does the software center work normally now? With an iinstall button?

If not you can install vlc easily.

```
sudo apt-get install vlc
```

---

### Post by cadefoster on 2013-11-14
Yes, it does!

[ATTACH=CONFIG]247816[/ATTACH]

Thank you so much for your help. You're a lifesaver!

---

