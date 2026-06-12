---
title: "Install both 32bit and 64bit libpng12"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by dayzman on 2012-05-19
Hi

I'm in 64bit oneric and would like to install Skype. It seems only the 32bit is available for oneric, but I can't install the 32bit libpng12-0 without removing the 64bit one. Can the 32b and 64b not coexist?

Thanks

---

### Post by Lisiano on 2012-05-19
Ola.
Skype is available in the Ubuntu Software Center. No need to mess around with libpng. Just [press here](apt://skype) to open Ubuntu Software Center and install Skype. If you wish to install both i386 and amd64 libs, you will have to drop down to a terminal (Ctrl+Alt+T) and type ```
sudo apt-get install libpng12-0 libpng12-0:i386
```

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> Ola.
Skype is available in the Ubuntu Software Center. No need to mess around with libpng. Just [press here](apt://skype) to open Ubuntu Software Center and install Skype. If you wish to install both i386 and amd64 libs, you will have to drop down to a terminal (Ctrl+Alt+T) and type ```
sudo apt-get install libpng12-0 libpng12-0:i386
```

Thanks for the reply. That link you gave me doesn't work. I get

```
NOT found
There isn't a software package called "skype" in your current software sources.
```

I've enabled "Partners" and Skype:i386 is available in synaptic, but it complains about

```
Depends: libqtgui4 but it is not going to be installed
```

I get the following as well:

```
sudo apt-get install skype:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype:i386 : Depends: libqtgui4:i386 (>= 4:4.5.3) but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I kept tracing back what is needed to install libqtgui4, and I arrived at libpng12 being one of its dependencies.

As you suggested,

```
sudo apt-get install libpng12-0 libpng12-0:i386

``` but it gives

```
The following packages have unmet dependencies.
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.46-3ubuntu1.3) but 1.2.46-3ubuntu1 is to be installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.46-3ubuntu1) but 1.2.46-3ubuntu1.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```

This is what I don't understand. In synaptic, libpng12-0 (64b) is 1.2.46-3ubuntu1.3 but libpng3:i386 is 1.2.46-3ubuntu1. Do I have to uninstall the 64b package?

Thanks

---

### Post by Lisiano on 2012-05-19
I noticed your other thread after I replied here.
It seems you have borked multiarch, please post the contents of /etc/dpkg/dpkg.cfg.d/ and the contents of every file in that directory

Also, can you try running ```
sudo apt-get -f install
```

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> I noticed your other thread after I replied here.
It seems you have borked multiarch, please post the contents of /etc/dpkg/dpkg.cfg.d/ and the contents of every file in that directory

Also, can you try running ```
sudo apt-get -f install
```

Yeah, I wonder if it's all related. Here's my dpkg.cfg.d

```
multiarch  multiarchsudo
```

```

cat *
foreign-architecture i386
foreign-architecture i386

```
```

apt-get -f install
``` doesn't give me much though

```


sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 lib32tinfo5 ia32-libs libc6-i386 lib32ffi6 lib32gcc1
  lib32asound2 lib32ncursesw5 lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Thanks

---

### Post by Lisiano on 2012-05-19
Delete multiarchsudo 
After that, run this
```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install ubuntu-desktop
```

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> Delete multiarchsudo 
After that, run this
```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install ubuntu-desktop
```

Hmm. There doesn't seem to be a difference.

```


$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 lib32tinfo5 ia32-libs libc6-i386 lib32ffi6 lib32gcc1
  lib32asound2 lib32ncursesw5 lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype:i386 : Depends: libqtgui4:i386 (>= 4:4.5.3) but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Thanks

---

### Post by Lisiano on 2012-05-19
Try installing ubuntu-desktop instead of skype
It might at least point to what is the problem. ubuntu-desktop is a metapackage which depends on every GUI app in Ubuntu which then in turn depend on their libraries and etc.

Note, noticed you lost konsole and okular, if you are using Kubuntu, then replace ubuntu-desktop with kubuntu-desktop

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> Try installing ubuntu-desktop instead of skype
It might at least point to what is the problem. ubuntu-desktop is a metapackage which depends on every GUI app in Ubuntu which then in turn depend on their libraries and etc.

OK. I can install ubuntu-desktop fine. No error at all.

I should add that if I just install libqtgui4:i386, I get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libqtgui4:i386 : Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
                  Depends: libfreetype6:i386 (>= 2.3.5) but it is not going to be installed
                  Depends: libpng12-0:i386 (>= 1.2.13-4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by Unterseeboot_234 on 2012-05-19
You "can" install libs that ia32-lib won't handle for you but I would opinion you will still have dependency problems because we speak of audio codecs. Ubuntu tried to make installation easier with Pulse audio libs and it was my experience if you break those links, or let a 32-bit lib replace a 64-bit lib, I had a broken Ubuntu which then required a new install.

Here is a link I used to try and get JavaFX to fit on my 64-bit. On one box the "hack" does work. On another box this same "hack" doesn't work.

**_[COLOR="Blue"][http://www.weiqigao.com/blog/2012/02/03/running_32_bit_javafx_2_1_beta_sdk_on_64_bit_ubuntu_11_10.html]("http://www.weiqigao.com/blog/2012/02/03/running_32_bit_javafx_2_1_beta_sdk_on_64_bit_ubuntu_11_10.html")[/COLOR]_**

You are better off making another partition and installing 32-bit Oneric. Boot into the i586 Ubuntu when you want Skype.

---

### Post by dayzman on 2012-05-19
I think the main issue here is with the 64b/32b gap. It doesn't let me install both 32b and 64b of libpng12-0.

---

### Post by Lisiano on 2012-05-19
Skype i386 works fine on amd64, I'm using it atm. It's just your particular dependency hell which is blocking the install... I would suggest backing up everything at this moment and reinstalling Ubuntu amd64, without trying to touch mutliarch and letting dpkg resolve i386 Skype itself.

And a quick question before you reinstall. Did you touch /etc/apt/sources.list?

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> Skype i386 works fine on amd64, I'm using it atm. It's just your particular dependency hell which is blocking the install... I would suggest backing up everything at this moment and reinstalling Ubuntu amd64, without trying to touch mutliarch and letting dpkg resolve i386 Skype itself.

Right. But just looking at libpng12-0:i386

```
sudo apt-get install libpng12-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 apache2.2-common : Depends: procps but it is not going to be installed
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.46-3ubuntu1.3) but 1.2.46-3ubuntu1 is to be installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.46-3ubuntu1) but 1.2.46-3ubuntu1.3 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Do you know why the 64bit version is version 1.2.46-3ubuntu1.3 whereas the 32bit version is 1.2.46-3ubuntu1? Is this expected?

Thanks

---

### Post by Lisiano on 2012-05-19
```
lisiano@Lisiano-Ubuntu:~$ dpkg -l libpng12-0 libpng12-0:i386
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  libpng12-0                      1.2.46-3ubuntu4                 PNG library - runtime
ii  libpng12-0:i386                 1.2.46-3ubuntu4                 PNG library - runtime

```I'm starting to wonder more and more if you touched sources.list, can you post it's content here and the process of ```
sudo apt-get update
```

---

### Post by dayzman on 2012-05-19
Here's the content:

```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://repository.spotify.com stable non-free
# deb http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu oneiric main


```

sudo apt-get update gives

```

Ign http://archive.canonical.com oneiric InRelease
Ign http://gb.archive.ubuntu.com oneiric InRelease                                      
Ign http://extras.ubuntu.com oneiric InRelease                                          
Hit http://repository.spotify.com stable InRelease                                      
Hit http://archive.canonical.com oneiric Release.gpg                                    
Get:1 http://gb.archive.ubuntu.com oneiric Release.gpg [198 B]                          
Hit http://extras.ubuntu.com oneiric Release.gpg                                        
Ign http://dl.google.com stable InRelease                                               
Hit http://archive.canonical.com oneiric Release                                        
Hit http://repository.spotify.com stable/non-free amd64 Packages                        
Get:2 http://gb.archive.ubuntu.com oneiric Release [40.8 kB]                            
Hit http://extras.ubuntu.com oneiric Release                                            
Get:3 http://dl.google.com stable Release.gpg [198 B]                                   
Hit http://archive.canonical.com oneiric/partner Sources                                
Hit http://repository.spotify.com stable/non-free i386 Packages                         
Ign http://repository.spotify.com stable/non-free TranslationIndex                      
Hit http://extras.ubuntu.com oneiric/main Sources                                       
Get:4 http://dl.google.com stable Release [1,347 B]                                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                         
Hit http://archive.canonical.com oneiric/partner i386 Packages                          
Ign http://archive.canonical.com oneiric/partner TranslationIndex                       
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                                
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                 
Get:5 http://dl.google.com stable/main amd64 Packages [1,222 B]                         
Get:6 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                              
Get:7 http://dl.google.com stable/main i386 Packages [1,220 B]                          
Ign http://repository.spotify.com stable/non-free Translation-en_GB                     
Ign http://archive.canonical.com oneiric/partner Translation-en_GB                      
Ign http://repository.spotify.com stable/non-free Translation-en                        
Ign http://archive.canonical.com oneiric/partner Translation-en                         
Ign http://dl.google.com stable/main TranslationIndex                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                  
Ign http://extras.ubuntu.com oneiric/main Translation-en
Get:8 http://gb.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:9 http://gb.archive.ubuntu.com oneiric/universe Sources [4,677 kB]         
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://dl.google.com stable/main Translation-en                            
Get:10 http://gb.archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:11 http://gb.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]
Get:12 http://gb.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]
Get:13 http://gb.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]
Get:14 http://gb.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]          
Get:15 http://gb.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]               
Get:16 http://gb.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]          
Get:17 http://gb.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]           
Get:18 http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                                                                                                  
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                                                                                                                                                 
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                                                                                                                                                
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                                                                                                                                                   
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB                                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB                                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en                                                                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB                                                                                                                                            
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en                                                                                                                                               
Fetched 17.4 MB in 11s (1,488 kB/s)                                                                                                                                                                            
Reading package lists... Done


```

---

### Post by Lisiano on 2012-05-19
The package list got updated now and the sources.list looks okay.
Try running a dist upgrade
```
sudo apt-get dist-upgrade
sudo apt-get install skype
```

---

### Post by dayzman on 2012-05-19
Hmm still no difference

```


$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype:i386 : Depends: libqtgui4:i386 (>= 4:4.5.3) but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by dayzman on 2012-05-19
I suspect if I could get a dependency like libpng12-0:i386 installed then it could be the fix. However, the 32b and 64b versions don't seem to match.

---

### Post by Lisiano on 2012-05-19
Well. Looks completely borked to me. Maybe someone more versed in package management could help you but I'm suggesting a reinstall now.


EDIT: You could try enabling the oneiric-proposed and oneiric-backports sources.
EDIT2: Also try switch to the Main server. Maybe the UK server is being weird and contains outdated lists.

---

### Post by dayzman on 2012-05-19
I think I know why the discrepancy in the versions. 1.2.46-3ubuntu1.3 came as an update and 1.2.46-3ubuntu1 was in the release. I wonder if the PPA hasn't been updated to 1.3.

---

### Post by dayzman on 2012-05-19
Yay! I've fixed it. I had to add

```


deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main multiverse universe

```

into sources.list

Thanks!

---

### Post by Lisiano on 2012-05-19
Congrats.

---

### Post by dayzman on 2012-05-19
1.3 is actually under oneiric-updates rather than oneiric but I didn't have oneiric-updates in my sources.list.

Thanks for the time.

---

