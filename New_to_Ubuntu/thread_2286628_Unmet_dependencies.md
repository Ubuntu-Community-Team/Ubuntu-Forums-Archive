---
title: "Unmet dependencies"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by oglipogli2 on 2015-07-13
after upgrading to Ubuntu 15.04 error message on top toolbar

tried apt-get -f install

it says

```
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb
 /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

tried using rm to remove the packages access denied.

error still continues

system settings not opening too.

tried repairing the packages the following output is seen

```
dpkg: error processing package zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on zenity; however:
  Package zenity is not configured yet.


dpkg: error processing package metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 3.12.11-0ubuntu3); however:
  Version of evolution-common on system is 3.12.10-0ubuntu1~14.10.1.


dpkg: error processing package evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 3.12.11-0ubuntu3); however:
  Package evolution is not configured yet.


dpkg: error processing package evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up fontconfig (2.11.1-0ubuntu6) ...
Regenerating fonts cache... failed.
See /var/log/fontconfig.log for more information.
dpkg: error processing package fontconfig (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-session-flashback:
 gnome-session-flashback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.


dpkg: error processing package gnome-session-flashback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on fontconfig; however:
  Package fontconfig is not configured yet.


dpkg: error processing package libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qt-at-spi:i386:
 qt-at-spi:i386 depends on libqtgui4 (>= 4:4.8~); however:
  Package libqtgui4:i386 is not configured yet.


dpkg: error processing package qt-at-spi:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pyatspi:
 python3-pyatspi depends on qt-at-spi; however:
  Package qt-at-spi:i386 is not configured yet.


dpkg: error processing package python3-pyatspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:
 libqt4-designer:i386 depends on libqtgui4 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1); however:
  Package libqtgui4:i386 is not configured yet.


dpkg: error processing package libqt4-designer:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-help:i386:
 libqt4-help:i386 depends on libqtgui4 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1); however:
  Package libqtgui4:i386 is not configured yet.


dpkg: error processing package libqt4-help:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:i386 is not configured yet.


dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on fontconfig; however:
  Package fontconfig is not configured yet.


dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:4.4.2-0ubuntu2); however:
  Package libreoffice-core is not configured yet.


dpkg: error processing package libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
```


help

help.!!!

---

### Post by sandyd on 2015-07-13
Hi, can I get the output of the following (Side note: it might not fix the issue, but show what the true error is)
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity
```

I also need the output of the following:
```

ls -l /etc/apt/sources.list.d
cat /etc/apt/sources.list
```

Regards,

---

### Post by oglipogli2 on 2015-07-14
for the first code the output is as follows

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fontconfig is already the newest version.
qt-at-spi is already the newest version.
zenity is already the newest version.
libqtgui4 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.12.11-0ubuntu3) but 3.12.10-0ubuntu1~14.10.1 is to be installed
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


whereas fr the 2nd one the output is as follows

```
total 36
-rw-r--r-- 1 root root 176 Jul 14 01:34 google-chrome.list
-rw-r--r-- 1 root root 176 Jul 14 01:26 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 Jul 13 07:57 google-chrome.list.save
-rw-r--r-- 1 root root 160 Jul 14 01:34 peterlevi-ubuntu-ppa-utopic.list
-rw-r--r-- 1 root root 160 Jul 14 01:26 peterlevi-ubuntu-ppa-utopic.list.distUpgrade
-rw-r--r-- 1 root root 160 Jul 13 07:57 peterlevi-ubuntu-ppa-utopic.list.save
-rw-r--r-- 1 root root 210 Jul 14 01:34 ubuntu-audio-dev-ppa-trusty.list
-rw-r--r-- 1 root root 210 Jul 14 01:26 ubuntu-audio-dev-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root 210 Jul 13 07:57 ubuntu-audio-dev-ppa-trusty.list.save
```

and

```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid main restricted universe multiverse #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates main restricted universe multiverse #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-proposed main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-proposed main universe restricted multiverse #Added by software-properties
deb [http://debian.sur5r.net/i3/](http://debian.sur5r.net/i3/) vivid universe # disabled on upgrade to vivid
```

---

### Post by v3.xx on 2015-07-14
Try removing those old PPAs and see if that clears the problem.

```
software-properties-gtk
```

---

### Post by sandyd on 2015-07-14
Your system somehow wants a evolution version built for Ubuntu 14.10 over the one in the repo. Lets fix that one first.

A few more tries...
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3
```

---

### Post by mc4man on 2015-07-14
Also to try & show - 
```
sudo apt-get update
```
```
apt-cache policy zenity-common evolution-common
```
You could also just remove evolution-common, then maybe the newer version could be installed.
However zenity-common cannot be removed as things that you want depend on it.

Also worth looking at, just a simulation
```
sudo apt-get -s dist-upgrade
```

---

### Post by oglipogli2 on 2015-07-14
out put of 

```
sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3

```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fontconfig is already the newest version.
qt-at-spi is already the newest version.
zenity is already the newest version.
libqtgui4 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by oglipogli2 on 2015-07-14
> **mc4man said:**
> Also to try & show - 
```
sudo apt-get update
```
```
apt-cache policy zenity-common evolution-common
```
You could also just remove evolution-common, then maybe the newer version could be installed.
However zenity-common cannot be removed as things that you want depend on it.

Also worth looking at, just a simulation
```
sudo apt-get -s dist-upgrade
```

```
zenity-common:
  Installed: 3.12.1-1.1
  Candidate: 3.14.0-1
  Version table:
     3.14.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ vivid/main i386 Packages
 *** 3.12.1-1.1 0
        100 /var/lib/dpkg/status
evolution-common:
  Installed: 3.12.10-0ubuntu1~14.10.1
  Candidate: 3.12.11-0ubuntu3
  Version table:
     3.12.11-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ vivid/main i386 Packages
 *** 3.12.10-0ubuntu1~14.10.1 0
        100 /var/lib/dpkg/status

```

```
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com vivid InRelease                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Get:3 http://archive.canonical.com vivid Release.gpg [933 B]                   
Hit http://debian.sur5r.net vivid InRelease                                    
Ign http://archive.ubuntu.com vivid InRelease                                  
Ign http://ppa.launchpad.net vivid InRelease                             
Get:4 http://archive.canonical.com vivid Release [9,356 B]                     
Get:5 http://dl.google.com stable/main i386 Packages [1,182 B]                 
Ign http://archive.ubuntu.com vivid-updates InRelease                          
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:6 http://archive.canonical.com vivid/partner Sources [3,045 B]             
Get:7 http://archive.canonical.com vivid/partner i386 Packages [3,302 B]       
Ign http://archive.ubuntu.com vivid-security InRelease                         
Hit http://ppa.launchpad.net vivid Release                                     
Get:8 http://archive.canonical.com vivid/partner Translation-en [1,973 B]      
Ign http://archive.ubuntu.com vivid-proposed InRelease                         
Hit http://debian.sur5r.net vivid/universe i386 Packages                       
Hit http://archive.ubuntu.com vivid Release.gpg                                
Ign http://dl.google.com stable/main Translation-en_IN                         
Get:9 http://archive.ubuntu.com vivid-updates Release.gpg [933 B]     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net vivid/main i386 Packages                 
Get:10 http://archive.ubuntu.com vivid-security Release.gpg [933 B]   
Hit http://ppa.launchpad.net vivid/main Translation-en                
Get:11 http://archive.ubuntu.com vivid-proposed Release.gpg [933 B]   
Hit http://archive.ubuntu.com vivid Release                                    
Get:12 http://archive.ubuntu.com vivid-updates Release [63.5 kB]               
Ign http://debian.sur5r.net vivid/universe Translation-en_IN                   
Ign http://debian.sur5r.net vivid/universe Translation-en                      
Get:13 http://archive.ubuntu.com vivid-security Release [63.5 kB]              
Get:14 http://archive.ubuntu.com vivid-proposed Release [217 kB]               
Get:15 http://archive.ubuntu.com vivid-updates/main Sources [59.1 kB]          
Get:16 http://archive.ubuntu.com vivid-updates/restricted Sources [28 B]       
Get:17 http://archive.ubuntu.com vivid-updates/universe Sources [27.3 kB]      
Get:18 http://archive.ubuntu.com vivid-updates/multiverse Sources [1,960 B]    
Get:19 http://archive.ubuntu.com vivid-updates/main i386 Packages [135 kB]     
Get:20 http://archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B] 
Get:21 http://archive.ubuntu.com vivid-updates/universe i386 Packages [78.9 kB]
Get:22 http://archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,675 B]
Hit http://archive.ubuntu.com vivid-updates/restricted Translation-en          
Get:23 http://archive.ubuntu.com vivid-security/main Sources [26.4 kB]         
Get:24 http://archive.ubuntu.com vivid-security/restricted Sources [28 B]      
Get:25 http://archive.ubuntu.com vivid-security/universe Sources [12.9 kB]     
Get:26 http://archive.ubuntu.com vivid-security/multiverse Sources [1,960 B]   
Get:27 http://archive.ubuntu.com vivid-security/main i386 Packages [79.9 kB]   
Get:28 http://archive.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:29 http://archive.ubuntu.com vivid-security/universe i386 Packages [40.9 kB]
Get:30 http://archive.ubuntu.com vivid-security/multiverse i386 Packages [3,675 B]
Hit http://archive.ubuntu.com vivid-security/restricted Translation-en         
Get:31 http://archive.ubuntu.com vivid-proposed/main Sources [78.2 kB]         
Get:32 http://archive.ubuntu.com vivid-proposed/universe Sources [6,558 B]     
Get:33 http://archive.ubuntu.com vivid-proposed/restricted Sources [1,371 B]   
Get:34 http://archive.ubuntu.com vivid-proposed/multiverse Sources [28 B]      
Get:35 http://archive.ubuntu.com vivid-proposed/main i386 Packages [85.9 kB]   
Get:36 http://archive.ubuntu.com vivid-proposed/universe i386 Packages [23.1 kB]
Get:37 http://archive.ubuntu.com vivid-proposed/restricted i386 Packages [3,271 B]
Get:38 http://archive.ubuntu.com vivid-proposed/multiverse i386 Packages [551 B]
Get:39 http://archive.ubuntu.com vivid-proposed/universe Translation-en [17.6 kB]
Hit http://archive.ubuntu.com vivid/main Sources                               
Hit http://archive.ubuntu.com vivid/restricted Sources                         
Hit http://archive.ubuntu.com vivid/universe Sources                           
Hit http://archive.ubuntu.com vivid/multiverse Sources                         
Hit http://archive.ubuntu.com vivid/main i386 Packages                         
Hit http://archive.ubuntu.com vivid/restricted i386 Packages                   
Hit http://archive.ubuntu.com vivid/universe i386 Packages                     
Hit http://archive.ubuntu.com vivid/multiverse i386 Packages                   
Hit http://archive.ubuntu.com vivid/main Translation-en                        
Hit http://archive.ubuntu.com vivid/multiverse Translation-en                  
Hit http://archive.ubuntu.com vivid/restricted Translation-en                  
Hit http://archive.ubuntu.com vivid/universe Translation-en                    
Hit http://archive.ubuntu.com vivid-updates/main Translation-en                
Hit http://archive.ubuntu.com vivid-updates/multiverse Translation-en          
Hit http://archive.ubuntu.com vivid-updates/universe Translation-en            
Hit http://archive.ubuntu.com vivid-security/main Translation-en               
Hit http://archive.ubuntu.com vivid-security/multiverse Translation-en         
Hit http://archive.ubuntu.com vivid-security/universe Translation-en           
Hit http://archive.ubuntu.com vivid-proposed/main Translation-en               
Hit http://archive.ubuntu.com vivid-proposed/multiverse Translation-en         
Hit http://archive.ubuntu.com vivid-proposed/restricted Translation-en         
Fetched 1,057 kB in 1min 20s (13.1 kB/s)                                       
Reading package lists... Done

```
```
sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.12.11-0ubuntu3) but 3.12.10-0ubuntu1~14.10.1 is installed
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by mc4man on 2015-07-14
I'd likely just download those 2 packages & try installing  with dpkg but first you could try - 
Can you install aptitude? and if so what does it report?
```
sudo apt-get install aptitude
```
if that works then
```
sudo aptitude upgrade
```
If it fails then choose no (n) & post complete output

---

### Post by CantankRus on 2015-07-14
From post #3...
> **oglipogli2 said:**
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) [COLOR="#FF0000"]**vivid-proposed**[/COLOR] main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) [COLOR="#FF0000"]**vivid-proposed**[/COLOR] main universe restricted multiverse #Added by software-properties

Is this the cause of the problem?

---

### Post by oglipogli2 on 2015-07-15
> **mc4man said:**
> I'd likely just download those 2 packages & try installing  with dpkg but first you could try - 
Can you install aptitude? and if so what does it report?
```
sudo apt-get install aptitude
```
if that works then
```
sudo aptitude upgrade
```
If it fails then choose no (n) & post complete output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: aptitude-common (= 0.6.11-1ubuntu3) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Recommends: aptitude-doc-en but it is not going to be installed or
                        aptitude-doc
 evolution : Depends: evolution-common (= 3.12.11-0ubuntu3) but 3.12.10-0ubuntu1~14.10.1 is to be installed
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by oglipogli2 on 2015-07-15
the output for apt-get -f install

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 libaudclient2 libgif4 libgnome-media-profiles-3.0-0
  libid3tag0 libimlib2 libinput0 libjavascriptcoregtk-1.0-0 libllvm3.5
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmirclient8driver-mesa
  libmircommon2 libmozjs-24-0 libopts25 libpoppler46 libqqwing2 libts-0.0-0
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libxmmsclient6
  linux-headers-3.16.0-31 linux-headers-3.16.0-31-generic
  linux-image-3.16.0-31-generic linux-image-extra-3.16.0-31-generic ntp tsconf
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  evolution-common zenity-common
The following packages will be upgraded:
  evolution-common zenity-common
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
439 not fully installed or removed.
Need to get 1,306 kB of archives.
After this operation, 28.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) vivid/main evolution-common all 3.12.11-0ubuntu3 [1,085 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) vivid/main zenity-common all 3.14.0-1 [221 kB]
Fetched 1,306 kB in 1min 8s (19.1 kB/s)                                        
(Reading database ... 274416 files and directories currently installed.)
Preparing to unpack .../evolution-common_3.12.11-0ubuntu3_all.deb ...
Unpacking evolution-common (3.12.11-0ubuntu3) over (3.12.10-0ubuntu1~14.10.1) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/oc/evolution/contacts-usage-delete-contact.page': Input/output error
Preparing to unpack .../zenity-common_3.14.0-1_all.deb ...
Unpacking zenity-common (3.14.0-1) over (3.12.1-1.1) ...
dpkg: error processing archive /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png': Input/output error
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.44.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb
 /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


and for autoremove

 ```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.12.11-0ubuntu3) but 3.12.10-0ubuntu1~14.10.1 is installed
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by mc4man on 2015-07-15
could you run this simulation - 
```
sudo apt-get -s purge evolution-common evolution zenity-common zenity 
```

---

### Post by oglipogli2 on 2015-07-15
> **mc4man said:**
> could you run this simulation - 
```
sudo apt-get -s purge evolution-common evolution zenity-common zenity 
```

the output for the above is as follows

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 evolution-plugins : Depends: evolution (= 3.12.11-0ubuntu3) but it is not going to be installed
 gnome-panel : Depends: evolution-common (>= 3.4.3) but it is not going to be installed
 metacity : Depends: zenity but it is not going to be installed
 ubuntu-desktop : Depends: zenity but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by oglipogli2 on 2015-07-15
Is there any space/memory/allocation issue ???

---

### Post by mc4man on 2015-07-15
> **oglipogli2 said:**
> Is there any space/memory/allocation issue ???

Nothing you've posted indicates - run some commands & check - [http://www.tecmint.com/how-to-check-disk-space-in-linux/](http://www.tecmint.com/how-to-check-disk-space-in-linux/)

---

### Post by sandyd on 2015-07-15
Run
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1
```

---

### Post by mc4man on 2015-07-16
This maybe of some interest - 
> dpkg: error processing archive /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/oc/evolution/contacts-usage-delete-contact.page': Input/output error
Preparing to unpack .../zenity-common_3.14.0-1_all.deb ...
Unpacking zenity-common (3.14.0-1) over (3.12.1-1.1) ...
dpkg: error processing archive /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png': Input/output error

Have seen some rare examples in launchpad of this behavior, though no explained reason?? 
(- wonder what would happen if they were removed or renamed? (root owned..

---

### Post by oglipogli2 on 2015-07-16
> **sandyd said:**
> Run
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1
```
 

The output for the above.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fontconfig is already the newest version.
qt-at-spi is already the newest version.
zenity is already the newest version.
libqtgui4 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

Was forced to switch to i3wm as nothing wa working in default WM by ubuntu

---

### Post by MGrowl on 2015-07-16
There must be a conflict in the PPA. If I remember correctly I received similar errors after adding a PPA.

What I did to solve that was to first uninstall the program, unticked all the sources and just left the PPA of the program I needed. Then I installed. I got the latest version of what I needed, and lost those errors. 

I also unticked the programs PPA's after and ticked back the main ones.

---

### Post by sandyd on 2015-07-17
Run
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1 zenity-common=3.14.0-1
```

---

### Post by oglipogli2 on 2015-07-19
> **sandyd said:**
> Run
```

sudo apt-get -s install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1 zenity-common=3.14.0-1
```


The output for the above is as follows

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fontconfig is already the newest version.
qt-at-spi is already the newest version.
zenity is already the newest version.
libqtgui4 is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 libaudclient2 libgif4
  libgnome-media-profiles-3.0-0 libid3tag0 libimlib2 libinput0
  libjavascriptcoregtk-1.0-0 libllvm3.5 libmagickcore5
  libmagickcore5-extra libmagickwand5 libmirclient8driver-mesa
  libmircommon2 libmozjs-24-0 libopts25 libpoppler46 libqqwing2
  libts-0.0-0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libxmmsclient6 linux-headers-3.16.0-31
  linux-headers-3.16.0-31-generic linux-image-3.16.0-31-generic
  linux-image-extra-3.16.0-31-generic ntp tsconf
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  evolution-common zenity-common
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
439 not fully installed or removed.
Inst evolution-common [3.12.10-0ubuntu1~14.10.1] (3.12.11-0ubuntu3 Ubuntu:15.04/vivid [all]) [zenity:i386 ]
Inst zenity-common [3.12.1-1.1] (3.14.0-1 Ubuntu:15.04/vivid [all])
Conf dh-python (1.20141111-2ubuntu1 Ubuntu:15.04/vivid [all])
Conf python3 (3.4.3-1 Ubuntu:15.04/vivid [i386])
Conf python3-apt (0.9.3.11build1 Ubuntu:15.04/vivid [i386])
Conf language-selector-common (0.143 Ubuntu:15.04/vivid [all])
Conf fontconfig (2.11.1-0ubuntu6 Ubuntu:15.04/vivid [i386])
Conf libpango-1.0-0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf plymouth (0.9.0-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf mountall (2.54ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libpangoft2-1.0-0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf libpangocairo-1.0-0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf librsvg2-2 (2.40.9-1 Ubuntu:15.04/vivid [i386])
Conf librsvg2-common (2.40.9-1 Ubuntu:15.04/vivid [i386])
Conf mir-client-platform-mesa2 (0.12.1+15.04.20150324-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libmirclient8 (0.12.1+15.04.20150324-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgtk-3-0 (3.14.13-0ubuntu1 Ubuntu:15.04/vivid-updates [i386])
Conf libgtk2.0-0 (2.24.27-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-themes-standard (3.14.2.3-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libwxgtk3.0-0 (3.0.2-1 Ubuntu:15.04/vivid [i386])
Conf 0ad (0.0.18-1 Ubuntu:15.04/vivid [i386])
Conf libgldi3 (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf cairo-dock-core (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libdbusmenu-gtk3-4 (12.10.3+15.04.20150410.2-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libido3-0.1-0 (13.10.0+15.04.20150319-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libvte-2.90-9 (1:0.36.3-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libwebkitgtk-3.0-0 (2.4.8-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf cairo-dock-plug-ins (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf cairo-dock-plug-ins-dbus-interface-python (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf cairo-dock-plug-ins-integration (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libmetacity-private2 (1:3.14.3-1ubuntu7 Ubuntu:15.04/vivid [i386])
Conf libwnck-3-0 (3.14.0-1 Ubuntu:15.04/vivid [i386])
Conf gconf-service-backend (3.2.6-3ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gconf-service (3.2.6-3ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gconf2 (3.2.6-3ubuntu1 Ubuntu:15.04/vivid [i386])
Conf compiz-gnome (1:0.9.12.1+15.04.20150410.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf compiz-plugins (1:0.9.12.1+15.04.20150410.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgnome-control-center1 (1:3.14.2-2ubuntu3 Ubuntu:15.04/vivid [i386])
Conf libnautilus-extension1a (1:3.14.2-0ubuntu9.1 Ubuntu:15.04/vivid-proposed [i386])
Conf libpeas-1.0-0 (1.12.1-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-control-center1 (15.04.0+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgtk-3-bin (3.14.13-0ubuntu1 Ubuntu:15.04/vivid-updates [i386])
Conf humanity-icon-theme (0.6.8 Ubuntu:15.04/vivid [all])
Conf adwaita-icon-theme (3.14.0-2ubuntu8 Ubuntu:15.04/vivid [all])
Conf ubuntu-mono (14.04+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf deja-dup (32.0-0ubuntu5 Ubuntu:15.04/vivid [i386])
Conf libnss3-nssdb (2:3.19.2-0ubuntu15.04.1 Ubuntu:15.04/vivid-updates [all])
Conf libnss3 (2:3.19.2-0ubuntu15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf libnss3-1d (2:3.19.2-0ubuntu15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf libcamel-1.2-49 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libedataserver-1.2-18 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libecal-1.2-16 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libcanberra-gtk3-0 (0.30-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libebackend-1.2-7 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libebook-contacts-1.2-0 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libedata-book-1.2-20 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libebook-1.2-14 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgail-3-0 (3.14.13-0ubuntu1 Ubuntu:15.04/vivid-updates [i386])
Conf libgcr-ui-3-1 (3.14.0-2build1 Ubuntu:15.04/vivid [i386])
Conf libgnome-desktop-3-10 (3.14.1-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libgtkhtml-4.0-common (4.8.5-1ubuntu1 Ubuntu:15.04/vivid [all])
Conf libgtkhtml-4.0-0 (4.8.5-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgtkhtml-editor-4.0-0 (4.8.5-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgweather-3-6 (3.16.0-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libevolution (3.12.11-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf evolution-common (3.12.11-0ubuntu3 Ubuntu:15.04/vivid [all])
Conf evolution-data-server-online-accounts (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libedata-cal-1.2-23 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf evolution-data-server (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf evolution (3.12.11-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf gcr (3.14.0-2build1 Ubuntu:15.04/vivid [i386])
Conf gnome-keyring (3.16.0-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gstreamer0.10-plugins-bad (0.10.23-7.4ubuntu2 Ubuntu:15.04/vivid [i386])
Conf language-pack-en-base (1:15.04+20150615 Ubuntu:15.04/vivid-updates [all])
Conf language-pack-en (1:15.04+20150615 Ubuntu:15.04/vivid-updates [all])
Conf language-pack-gnome-en-base (1:15.04+20150615 Ubuntu:15.04/vivid-updates [all])
Conf language-pack-gnome-en (1:15.04+20150615 Ubuntu:15.04/vivid-updates [all])
Conf libafterimage0 (2.2.12-3 Ubuntu:15.04/vivid [i386])
Conf libdbusmenu-gtk4 (12.10.3+15.04.20150410.2-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libappindicator1 (12.10.1+15.04.20141110-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libappindicator3-1 (12.10.1+15.04.20141110-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libavahi-ui-gtk3-0 (0.6.31-4ubuntu4 Ubuntu:15.04/vivid [i386])
Conf libbonoboui2-0 (2.24.5-0ubuntu4 Ubuntu:15.04/vivid [i386])
Conf libcanberra-gtk0 (0.30-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf gnome-session-canberra (0.30-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libcogl-pango20 (1.18.2-3 Ubuntu:15.04/vivid [i386])
Conf libclutter-1.0-0 (1.20.0-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libclutter-gst-2.0-0 (2.0.12-1build1 Ubuntu:15.04/vivid [i386])
Conf gstreamer1.0-x (1.4.5-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libcheese7 (3.14.1-2ubuntu4 Ubuntu:15.04/vivid [i386])
Conf libclutter-gtk-1.0-0 (1.6.0-1 Ubuntu:15.04/vivid [i386])
Conf gstreamer1.0-clutter (2.0.12-1build1 Ubuntu:15.04/vivid [i386])
Conf libcheese-gtk23 (3.14.1-2ubuntu4 Ubuntu:15.04/vivid [i386])
Conf libcolord-gtk1 (0.1.25-1.1build2 Ubuntu:15.04/vivid [i386])
Conf libgail18 (2.24.27-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgegl-0.2-0 (0.2.0-7ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgoa-backend-1.0-1 (3.14.2-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libgtkmm-3.0-1 (3.14.0-1 Ubuntu:15.04/vivid [i386])
Conf libgtksourceview-3.0-1 (3.14.4-1 Ubuntu:15.04/vivid [i386])
Conf dmeventd (2:1.02.90-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf liblvm2cmd2.02 (2.02.111-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libnux-4.0-0 (4.0.7+15.04.20150410.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libpangoxft-1.0-0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf libqtgui4 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-declarative (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-designer (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-help (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-opengl (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-scripttools (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt4-svg (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt5gui5 (5.4.1+dfsg-2ubuntu4.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt5multimedia5 (5.4.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libqt5feedback5 (5.0~git20130529-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf libqt5widgets5 (5.4.1+dfsg-2ubuntu4.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt5opengl5 (5.4.1+dfsg-2ubuntu4.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt5printsupport5 (5.4.1+dfsg-2ubuntu4.1 Ubuntu:15.04/vivid-updates [i386])
Conf libqt5quick5 (5.4.1-1ubuntu5 Ubuntu:15.04/vivid [i386])
Conf libqt5svg5 (5.4.1-1 Ubuntu:15.04/vivid [i386])
Conf libqt5webkit5 (5.4.1+dfsg-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-gtk2-parser0 (0.0.0+15.04.20150118-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-gtk3-parser0 (0.0.0+15.04.20150118-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libwebkitgtk-1.0-0 (2.4.8-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf apparmor (2.9.1-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf lightdm (1.14.2-0ubuntu1.1 Ubuntu:15.04/vivid-proposed [i386])
Conf libnm-gtk0 (0.9.10.1-0ubuntu4 Ubuntu:15.04/vivid [i386])
Conf nautilus (1:3.14.2-0ubuntu9.1 Ubuntu:15.04/vivid-proposed [i386])
Conf gstreamer0.10-gconf (0.10.31-3+nmu1ubuntu6 Ubuntu:15.04/vivid [i386])
Conf gnome-media (3.4.0-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-settings-daemon1 (15.04.1+15.04.20150408-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-settings-daemon (15.04.1+15.04.20150408-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-settings-daemon (3.14.2-3ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-menus (3.10.1-0ubuntu5 Ubuntu:15.04/vivid [i386])
Conf gnome-font-viewer (3.14.0-2 Ubuntu:15.04/vivid [i386])
Conf libgnome-bluetooth11 (3.8.2.1-0ubuntu12 Ubuntu:15.04/vivid [i386])
Conf gnome-control-center (1:3.14.2-2ubuntu3 Ubuntu:15.04/vivid [i386])
Conf libtimezonemap1 (0.4.3build1 Ubuntu:15.04/vivid [i386])
Conf libgnomekbd8 (3.6.0-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gkbd-capplet (3.6.0-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf indicator-keyboard (0.0.0+15.04.20150310-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-pango-1.0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf gir1.2-gtk-3.0 (3.14.13-0ubuntu1 Ubuntu:15.04/vivid-updates [i386])
Conf gir1.2-ibus-1.0 (1.5.9-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf ibus (1.5.9-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf indicator-datetime (13.10.0+15.04.20150406-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-control-center (15.04.0+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-gnomebluetooth-1.0 (3.8.2.1-0ubuntu12 Ubuntu:15.04/vivid [i386])
Conf policykit-1-gnome (0.105-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf network-manager-gnome (0.9.10.1-0ubuntu4 Ubuntu:15.04/vivid [i386])
Conf gnome-bluetooth (3.8.2.1-0ubuntu12 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtfeedback (5.0~git20130529-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtquick2 (5.4.1-1ubuntu5 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtgraphicaleffects (5.4.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtquick-privatewidgets (5.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtquick-dialogs (5.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtquick-window2 (5.4.1-1ubuntu5 Ubuntu:15.04/vivid [i386])
Conf qml-module-qtwebkit (5.4.1+dfsg-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qt-at-spi (0.3.1-5fakesync1 Ubuntu:15.04/vivid [i386])
Conf liboxideqtcore0 (1.7.9-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf liboxideqtquick0 (1.7.9-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf liboxideqt-qmlplugin (1.7.9-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf qtdeclarative5-qtquick2-plugin (5.4.1-1ubuntu5 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-dialogs-plugin (5.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-window-plugin (5.4.1-1ubuntu5 Ubuntu:15.04/vivid [i386])
Conf libqt5qml-graphicaleffects (5.4.1-1ubuntu1 Ubuntu:15.04/vivid [all])
Conf qml-module-qtquick-layouts (5.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-qtfeedback-plugin (5.0~git20130529-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-ubuntu-ui-toolkit-plugin (1.2.1458+15.04.20150422-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-ubuntu-web-plugin (0.23+15.04.20150416-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-ubuntu-ui-extras-browser-plugin (0.23+15.04.20150416-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf webbrowser-app (0.23+15.04.20150416-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf root-plugin-geom-gdml (5.34.19+dfsg-1.2 Ubuntu:15.04/vivid [i386])
Conf root-plugin-graf2d-asimage (5.34.19+dfsg-1.2 Ubuntu:15.04/vivid [i386])
Conf ubuntu-drivers-common (1:0.4.5 Ubuntu:15.04/vivid [i386])
Conf unity-gtk2-module (0.0.0+15.04.20150118-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-gtk3-module (0.0.0+15.04.20150118-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf update-notifier-common (3.160 Ubuntu:15.04/vivid [all])
Conf gstreamer1.0-plugins-bad (1.4.5-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libpangox-1.0-0 (0.0.2-5 Ubuntu:15.04/vivid [i386])
Conf console-setup (1.108ubuntu5 Ubuntu:15.04/vivid [all])
Conf kbd (1.15.5-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf console-setup-linux (1.108ubuntu5 Ubuntu:15.04/vivid [all])
Conf ubuntu-minimal (1.334 Ubuntu:15.04/vivid [i386])
Conf python3-gdbm (3.4.3-1 Ubuntu:15.04/vivid [i386])
Conf python3-commandnotfound (0.3ubuntu15.3 Ubuntu:15.04/vivid [all])
Conf command-not-found (0.3ubuntu15.3 Ubuntu:15.04/vivid [all])
Conf plymouth-theme-ubuntu-text (0.9.0-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf python3-distupgrade (1:15.04.14 Ubuntu:15.04/vivid [all])
Conf python3-update-manager (1:15.04.7 Ubuntu:15.04/vivid [all])
Conf ubuntu-release-upgrader-core (1:15.04.14 Ubuntu:15.04/vivid [all])
Conf ubuntu-standard (1.334 Ubuntu:15.04/vivid [i386])
Conf ufw (0.34~rc-0ubuntu5 Ubuntu:15.04/vivid [all])
Conf update-manager-core (1:15.04.7 Ubuntu:15.04/vivid [all])
Conf empathy (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf libpurple0 (1:2.10.9-0ubuntu8 Ubuntu:15.04/vivid [i386])
Conf telepathy-haze (0.8.0-2 Ubuntu:15.04/vivid [i386])
Conf mcp-account-manager-uoa (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf unity-asset-pool (0.8.24+15.04.20141217-0ubuntu2 Ubuntu:15.04/vivid [all])
Conf account-plugin-aim (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf account-plugin-facebook (0.12+15.04.20150415.1-0ubuntu2 Ubuntu:15.04/vivid-updates [all])
Conf account-plugin-flickr (0.12+15.04.20150415.1-0ubuntu2 Ubuntu:15.04/vivid-updates [all])
Conf account-plugin-google (0.12+15.04.20150415.1-0ubuntu2 Ubuntu:15.04/vivid-updates [all])
Conf account-plugin-jabber (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf account-plugin-salut (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf account-plugin-twitter (0.12+15.04.20150415.1-0ubuntu2 Ubuntu:15.04/vivid-updates [all])
Conf account-plugin-windows-live (0.12+15.04.20150415.1-0ubuntu2 Ubuntu:15.04/vivid-updates [all])
Conf account-plugin-yahoo (3.12.9-1ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf zeitgeist-datahub (0.9.14-2.2ubuntu3 Ubuntu:15.04/vivid [i386])
Conf zeitgeist (0.9.14-2.2ubuntu3 Ubuntu:15.04/vivid [all])
Conf activity-log-manager (0.9.7-0ubuntu19 Ubuntu:15.04/vivid [i386])
Conf activity-log-manager-control-center (0.9.7-0ubuntu19 Ubuntu:15.04/vivid [all])
Conf adobe-flashplugin (1:20150714.1-0vivid1 Partner archive:15.04/vivid [i386])
Conf adobe-flash-properties-gtk (1:20150714.1-0vivid1 Partner archive:15.04/vivid [i386])
Conf aisleriot (1:3.14.2-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf alacarte (3.11.91-2 Ubuntu:15.04/vivid [all])
Conf python3-problem-report (2.17.2-0ubuntu1.1 Ubuntu:15.04/vivid-updates [all])
Conf python3-apport (2.17.2-0ubuntu1.1 Ubuntu:15.04/vivid-updates [all])
Conf apport (2.17.2-0ubuntu1.1 Ubuntu:15.04/vivid-updates [all])
Conf gir1.2-wnck-3.0 (3.14.0-1 Ubuntu:15.04/vivid [i386])
Conf libvte-2.91-0 (0.38.3-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-terminal (3.14.2-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf apport-gtk (2.17.2-0ubuntu1.1 Ubuntu:15.04/vivid-updates [all])
Conf apturl-common (0.5.2ubuntu6 Ubuntu:15.04/vivid [i386])
Conf unattended-upgrades (0.83.6ubuntu1 Ubuntu:15.04/vivid-updates [all])
Conf python3-software-properties (0.96.4 Ubuntu:15.04/vivid [all])
Conf software-properties-common (0.96.4 Ubuntu:15.04/vivid [all])
Conf python3-pkg-resources (12.2-1 Ubuntu:15.04/vivid [all])
Conf python3-aptdaemon (1.1.1+bzr982-0ubuntu3.1 Ubuntu:15.04/vivid-updates [all])
Conf gir1.2-vte-2.91 (0.38.3-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-aptdaemon.gtk3widgets (1.1.1+bzr982-0ubuntu3.1 Ubuntu:15.04/vivid-updates [all])
Conf software-properties-gtk (0.96.4 Ubuntu:15.04/vivid [all])
Conf gir1.2-webkit-3.0 (2.4.8-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf apturl (0.5.2ubuntu6 Ubuntu:15.04/vivid [i386])
Conf qml-module-ubuntu-onlineaccounts (0.5+15.04.20150415.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf qtdeclarative5-accounts-plugin (0.5+15.04.20150415.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-webapps-qml (0.1+15.04.20150409-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf webapp-container (0.23+15.04.20150416-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-webapps-service (2.5.0~+15.04.20141217.2-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-webapps0 (2.5.0~+15.04.20141217.2-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf bamfdaemon (0.5.1+15.04.20150202-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libbrasero-media3-1 (3.12.0-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf brasero-cdrkit (3.12.0-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf brasero (3.12.0-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf cairo-dock (3.4.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf cheese (3.14.1-2ubuntu4 Ubuntu:15.04/vivid [i386])
Conf compiz (1:0.9.12.1+15.04.20150410.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf cryptsetup (2:1.6.1-1ubuntu7 Ubuntu:15.04/vivid [i386])
Conf gvfs-backends (1.24.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf deja-dup-backend-gvfs (32.0-0ubuntu5 Ubuntu:15.04/vivid [all])
Conf python-gtk2 (2.24.0-3ubuntu4 Ubuntu:15.04/vivid [i386])
Conf python-glade2 (2.24.0-3ubuntu4 Ubuntu:15.04/vivid [i386])
Conf python-notify (0.1.1-4 Ubuntu:15.04/vivid [i386])
Conf notification-daemon (3.14.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf dunst (1.1.0-2 Ubuntu:15.04/vivid [i386])
Conf notify-osd (0.9.35+15.04.20150126-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf deluge-gtk (1.3.11-0ubuntu2 Ubuntu:15.04/vivid [all])
Conf deluge (1.3.11-0ubuntu2 Ubuntu:15.04/vivid [all])
Conf gir1.2-peas-1.0 (1.12.1-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf eog (3.14.4-1 Ubuntu:15.04/vivid [i386])
Conf libevdocument3-4 (3.14.2-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libevview3-3 (3.14.2-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf evince (3.14.2-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf evolution-plugins (3.12.11-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf file-roller (3.14.2-0ubuntu5 Ubuntu:15.04/vivid [i386])
Conf signon-ui-x11 (0.17+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity-control-center-signon (0.1.7~+14.10.20140814-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf webaccounts-extension-common (0.5-0ubuntu4 Ubuntu:15.04/vivid [i386])
Conf firefox (39.0+build5-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf xul-ext-webaccounts (0.5-0ubuntu4 Ubuntu:15.04/vivid [i386])
Conf foomatic-db-compressed-ppds (20150415-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf gedit (3.10.4-0ubuntu10 Ubuntu:15.04/vivid [i386])
Conf libgimp2.0 (2.8.14-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gimp (2.8.14-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-appindicator3-0.1 (12.10.1+15.04.20141110-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-edataserver-1.2 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-ebookcontacts-1.2 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-ebook-1.2 (3.12.11-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-gconf-2.0 (3.2.6-3ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-gtksource-3.0 (3.14.4-1 Ubuntu:15.04/vivid [i386])
Conf libpanel-applet0 (1:3.14.0-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gir1.2-panelapplet-5.0 (1:3.14.0-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf librhythmbox-core8 (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf gir1.2-rb-3.0 (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf libtotem0 (3.14.3-0ubuntu0.1 Ubuntu:15.04/vivid-proposed [i386])
Conf gir1.2-totem-1.0 (3.14.3-0ubuntu0.1 Ubuntu:15.04/vivid-proposed [i386])
Conf gir1.2-vte-2.90 (1:0.36.3-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libgucharmap-2-90-7 (1:3.14.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-panel (1:3.14.0-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-applets (3.14.0-1 Ubuntu:15.04/vivid [i386])
Conf gnome-calculator (1:3.14.1-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf gnome-disk-utility (3.14.0-0ubuntu2 Ubuntu:15.04/vivid [i386])
Conf gnome-flashback (3.14.0-3ubuntu11 Ubuntu:15.04/vivid [i386])
Conf gnome-mahjongg (1:3.14.1-1 Ubuntu:15.04/vivid [i386])
Conf gnome-mines (1:3.14.1-2 Ubuntu:15.04/vivid [i386])
Conf vino (3.8.1-0ubuntu5 Ubuntu:15.04/vivid [i386])
Conf gnome-session-bin (3.14.0-2ubuntu5 Ubuntu:15.04/vivid-updates [i386])
Conf gnome-power-manager (3.14.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnome-session (3.14.0-2ubuntu5 Ubuntu:15.04/vivid-updates [all])
Conf gnome-screensaver (3.6.1-0ubuntu16 Ubuntu:15.04/vivid [i386])
Conf gnome-screenshot (3.14.0-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf zenity-common (3.14.0-1 Ubuntu:15.04/vivid [all])
Conf zenity (3.14.0-1 Ubuntu:15.04/vivid [i386])
Conf metacity (1:3.14.3-1ubuntu7 Ubuntu:15.04/vivid [i386])
Conf gnome-session-flashback (1:3.14.0-3ubuntu11 Ubuntu:15.04/vivid [all])
Conf gnome-system-monitor (3.15.91-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gnomine (1:3.14.1-2 Ubuntu:15.04/vivid [all])
Conf gparted (0.19.0-2 Ubuntu:15.04/vivid [i386])
Conf grub-pc (2.02~beta2-22ubuntu1.1 Ubuntu:15.04/vivid-updates [i386])
Conf grub-gfxpayload-lists (0.7 Ubuntu:15.04/vivid [i386])
Conf gtk2-engines-pixbuf (2.24.27-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf gucharmap (1:3.14.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf hplip-data (3.15.2-0ubuntu4.1 Ubuntu:15.04/vivid-updates [all])
Conf python3-pil (2.7.0-1 Ubuntu:15.04/vivid [i386])
Conf python3-pexpect (3.2-1 Ubuntu:15.04/vivid [all])
Conf python3-reportlab-accel (3.1.44-1 Ubuntu:15.04/vivid [i386])
Conf python3-reportlab (3.1.44-1 Ubuntu:15.04/vivid [all])
Conf hplip (3.15.2-0ubuntu4.1 Ubuntu:15.04/vivid-updates [i386])
Conf printer-driver-postscript-hp (3.15.2-0ubuntu4.1 Ubuntu:15.04/vivid-updates [all])
Conf ibus-gtk (1.5.9-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf ibus-gtk3 (1.5.9-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf ibus-table (1.9.1-3ubuntu1 Ubuntu:15.04/vivid [all])
Conf indicator-applet-complete (12.10.2+15.04.20141127.2-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf indicator-application (12.10.1+15.04.20150128-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf indicator-appmenu (15.02.0+15.04.20150302-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python-aptdaemon.gtk3widgets (1.1.1+bzr982-0ubuntu3.1 Ubuntu:15.04/vivid-updates [all])
Conf landscape-client-ui-install (14.12-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf aptdaemon (1.1.1+bzr982-0ubuntu3.1 Ubuntu:15.04/vivid-updates [all])
Conf language-selector-gnome (0.143 Ubuntu:15.04/vivid [all])
Conf libcanberra-gtk-module (0.30-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libgail-common (2.24.27-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libpango-perl (1.226-2 Ubuntu:15.04/vivid [i386])
Conf libgtk2-perl (2:1.2492-4 Ubuntu:15.04/vivid [i386])
Conf libgtk2.0-bin (2.24.27-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libmagickcore-6.q16-2-extra (8:6.8.9.9-5 Ubuntu:15.04/vivid [i386])
Conf libpango1.0-0 (1.36.8-3 Ubuntu:15.04/vivid [i386])
Conf libqt5webkit5-qmlwebkitplugin (5.4.1+dfsg-2ubuntu1 Ubuntu:15.04/vivid [all])
Conf libreoffice-core (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-pdfimport (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-avmedia-backend-gstreamer (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-base-core (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-calc (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-draw (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-gtk (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-gnome (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-writer (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-help-en-us (1:4.4.2-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf libreoffice-impress (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libreoffice-math (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf libunique-1.0-0 (1.1.6-5 Ubuntu:15.04/vivid [i386])
Conf unity-services (7.3.2+15.04.20150420-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libunity-core-6.0-9 (7.3.2+15.04.20150420-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libwnck22 (1:2.30.7-0ubuntu5 Ubuntu:15.04/vivid [i386])
Conf libyelp0 (3.12.0-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf light-themes (14.04+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf lvm2 (2.02.111-2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf mousetweaks (3.12.0-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf nautilus-sendto (3.8.2-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf network-manager-pptp-gnome (0.9.10.0-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-cairo (1.10.0+dfsg-4build1 Ubuntu:15.04/vivid [i386])
Conf onboard (1.1.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf onboard-data (1.1.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf openprinting-ppds (20150415-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf overlay-scrollbar-gtk2 (0.2.16+r359+15.04.20150319-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf overlay-scrollbar (0.2.16+r359+15.04.20150319-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf overlay-scrollbar-gtk3 (0.2.16+r359+15.04.20150319-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf pcmanfm (1.2.3-1.1 Ubuntu:15.04/vivid [i386])
Conf plymouth-label (0.9.0-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf plymouth-theme-ubuntu-logo (0.9.0-0ubuntu9 Ubuntu:15.04/vivid [i386])
Conf printer-driver-foo2zjs-common (20150214dfsg0-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf printer-driver-foo2zjs (20150214dfsg0-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf printer-driver-ptouch (1.3-8ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python-appindicator (12.10.1+15.04.20141110-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python-gconf (2.28.1+dfsg-1.1 Ubuntu:15.04/vivid [i386])
Conf python-qt4 (4.11.3+dfsg-1 Ubuntu:15.04/vivid [i386])
Conf python3-bs4 (4.3.2-2ubuntu2 Ubuntu:15.04/vivid [all])
Conf python3-chardet (2.3.0-1 Ubuntu:15.04/vivid [all])
Conf python3-cups (1.9.72-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-six (1.9.0-1 Ubuntu:15.04/vivid [all])
Conf python3-urllib3 (1.9.1-3 Ubuntu:15.04/vivid [all])
Conf python3-requests (2.4.3-6 Ubuntu:15.04/vivid [all])
Conf python3-cupshelpers (1.5.6+20150318-0ubuntu2.1 Ubuntu:15.04/vivid-updates [all])
Conf python3-feedparser (5.1.3-3 Ubuntu:15.04/vivid [all])
Conf python3-html5lib (0.999-3 Ubuntu:15.04/vivid [all])
Conf python3-httplib2 (0.9+dfsg-2 Ubuntu:15.04/vivid [all])
Conf python3-lxml (3.4.2-1 Ubuntu:15.04/vivid [i386])
Conf python3-mako (1.0.0+dfsg-0.1 Ubuntu:15.04/vivid [all])
Conf python3-pyatspi (2.14.0+dfsg-1 Ubuntu:15.04/vivid [all])
Conf python3-renderpm (3.1.44-1 Ubuntu:15.04/vivid [i386])
Conf python3-smbc (1.0.15.3-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-uno (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf qtdeclarative5-privatewidgets-plugin (5.4.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf remmina (1.1.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf remmina-plugin-rdp (1.1.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf remmina-plugin-vnc (1.1.1-1ubuntu1 Ubuntu:15.04/vivid [i386])
Conf rhythmbox (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf rhythmbox-plugins (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf rhythmbox-plugin-zeitgeist (3.1-1ubuntu3 Ubuntu:15.04/vivid [all])
Conf rhythmbox-plugin-cdrecorder (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf rhythmbox-mozilla (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf rhythmbox-plugin-magnatune (3.1-1ubuntu3 Ubuntu:15.04/vivid [i386])
Conf root-system-bin (5.34.19+dfsg-1.2 Ubuntu:15.04/vivid [i386])
Conf seahorse (3.15.90-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf signon-ui (0.17+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf simple-scan (3.16.1.1-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-oneconf (0.3.7.15.04.1 Ubuntu:15.04/vivid-proposed [all])
Conf oneconf (0.3.7.15.04.1 Ubuntu:15.04/vivid-proposed [all])
Conf software-center (13.10-0ubuntu6.1 Ubuntu:15.04/vivid-updates [all])
Conf ssh-askpass-gnome (1:6.7p1-5ubuntu1 Ubuntu:15.04/vivid [i386])
Conf system-config-printer-common (1.5.6+20150318-0ubuntu2.1 Ubuntu:15.04/vivid-updates [all])
Conf python3-aptdaemon.pkcompat (1.1.1+bzr982-0ubuntu3.1 Ubuntu:15.04/vivid-updates [all])
Conf system-config-printer-gnome (1.5.6+20150318-0ubuntu2.1 Ubuntu:15.04/vivid-updates [all])
Conf system-config-printer-udev (1.5.6+20150318-0ubuntu2.1 Ubuntu:15.04/vivid-updates [i386])
Conf thunderbird (1:31.7.0+build1-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf thunderbird-gnome-support (1:31.7.0+build1-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf thunderbird-locale-en (1:31.7.0+build1-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [i386])
Conf thunderbird-locale-en-us (1:31.7.0+build1-0ubuntu0.15.04.1 Ubuntu:15.04/vivid-updates [all])
Conf totem (3.14.3-0ubuntu0.1 Ubuntu:15.04/vivid-proposed [i386])
Conf totem-plugins (3.14.3-0ubuntu0.1 Ubuntu:15.04/vivid-proposed [i386])
Conf transmission-gtk (2.84-0.2ubuntu1 Ubuntu:15.04/vivid [i386])
Conf ubuntu-artwork (1:14.04+15.04.20150410-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf update-notifier (3.160 Ubuntu:15.04/vivid [i386])
Conf update-manager (1:15.04.7 Ubuntu:15.04/vivid [all])
Conf ubuntu-release-upgrader-gtk (1:15.04.14 Ubuntu:15.04/vivid [all])
Conf ubuntu-session (3.14.0-2ubuntu5 Ubuntu:15.04/vivid-updates [all])
Conf upstart (1.13.2-0ubuntu13.1 Ubuntu:15.04/vivid-proposed [i386])
Conf upstart-bin (1.13.2-0ubuntu13.1 Ubuntu:15.04/vivid-proposed [all])
Conf unity-greeter (15.04.4-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf unity (7.3.2+15.04.20150420-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf xdiagnose (3.7.2 Ubuntu:15.04/vivid [all])
Conf yelp (3.12.0-1ubuntu2 Ubuntu:15.04/vivid [i386])
Conf ubuntu-desktop (1.334 Ubuntu:15.04/vivid [i386])
Conf usb-creator-common (0.2.67ubuntu0.1 Ubuntu:15.04/vivid-updates [i386])
Conf usb-creator-gtk (0.2.67ubuntu0.1 Ubuntu:15.04/vivid-updates [i386])
Conf vlc (2.2.0-1 Ubuntu:15.04/vivid [i386])
Conf vlc-plugin-notify (2.2.0-1 Ubuntu:15.04/vivid [i386])
Conf xul-ext-ubufox (3.0-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf appmenu-qt5 (0.3.0+15.04.20150121-0ubuntu3 Ubuntu:15.04/vivid [i386])
Conf compizconfig-settings-manager (1:0.9.12.1+15.04.20150410.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf indicator-printers (0.1.7+15.04.20150220-0ubuntu1 Ubuntu:15.04/vivid [i386])
Conf libcanberra-gtk3-module (0.30-2ubuntu2 Ubuntu:15.04/vivid [i386])
Conf libreoffice-ogltrans (1:4.4.2-0ubuntu2 Ubuntu:15.04/vivid-proposed [i386])
Conf python3-brlapi (5.2~20141018-4ubuntu1 Ubuntu:15.04/vivid [i386])
Conf python3-speechd (0.8.1-0ubuntu1 Ubuntu:15.04/vivid [all])
Conf shotwell (0.20.2-0ubuntu3 Ubuntu:15.04/vivid [i386])

```

---

### Post by mc4man on 2015-07-19
[QUOTE=oglipogli2;13323638]The output for the above is as follows

Then run the same command again, this time for real, just remove the -s from the command, as in - 
```
sudo apt-get install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1 zenity-common=3.14.0-1

```

---

### Post by oglipogli2 on 2015-07-20
> **mc4man said:**
> [QUOTE=oglipogli2;13323638]The output for the above is as follows

Then run the same command again, this time for real, just remove the -s from the command, as in - 
```
sudo apt-get install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1 zenity-common=3.14.0-1

```

The output again shows an error message as follows
```
$ sudo apt-get install fontconfig libqtgui4:i386 qt-at-spi:i386 libqtgui4:i386 zenity evolution-common=3.12.11-0ubuntu3 zenity=3.14.0-1 zenity-common=3.14.0-1
[sudo] password for oglipogli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fontconfig is already the newest version.
qt-at-spi is already the newest version.
zenity is already the newest version.
libqtgui4 is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 libaudclient2 libgif4
  libgnome-media-profiles-3.0-0 libid3tag0 libimlib2 libinput0
  libjavascriptcoregtk-1.0-0 libllvm3.5 libmagickcore5
  libmagickcore5-extra libmagickwand5 libmirclient8driver-mesa
  libmircommon2 libmozjs-24-0 libopts25 libpoppler46 libqqwing2
  libts-0.0-0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libxmmsclient6 linux-headers-3.16.0-31
  linux-headers-3.16.0-31-generic linux-image-3.16.0-31-generic
  linux-image-extra-3.16.0-31-generic ntp tsconf
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  evolution-common zenity-common
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
439 not fully installed or removed.
Need to get 0 B/1,306 kB of archives.
After this operation, 28.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 274416 files and directories currently installed.)
Preparing to unpack .../evolution-common_3.12.11-0ubuntu3_all.deb ...
Unpacking evolution-common (3.12.11-0ubuntu3) over (3.12.10-0ubuntu1~14.10.1) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/oc/evolution/contacts-usage-delete-contact.page': Input/output error
Preparing to unpack .../zenity-common_3.14.0-1_all.deb ...
Unpacking zenity-common (3.14.0-1) over (3.12.1-1.1) ...
dpkg: error processing archive /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png': Input/output error
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.44.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_3.12.11-0ubuntu3_all.deb
 /var/cache/apt/archives/zenity-common_3.14.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mc4man on 2015-07-20
> **oglipogli2 said:**
> 

The output again shows an error message as follows 
Get rid of those 2 symlinks, in 14.04 they were links, now actual files, (at least the 1st. one.
```
sudo rm /usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png
```
```
sudo rm /usr/share/help/oc/evolution/contacts-usage-delete-contact.page

```
```
sudo apt-get clean && sudo apt-get dist-upgrade
```

---

### Post by Bashing-om on 2015-07-20
mc4man; Hello;

I have not paid close attention to this thread, but on my 14.04 system the symlink still exists :
```

sysop@1404mini:~$ ls -al /usr/share/help/ca/zenity/figures/
total 56
drwxr-xr-x 2 root root 4096 Jul  6  2014 .
drwxr-xr-x 3 root root 4096 Jul  6  2014 ..
lrwxrwxrwx 1 root root   74 Apr  7  2014 zenity-calendar-screenshot.png -> ../../../../help-langpack/ca/zenity/figures/zenity-calendar-screenshot.png
lrwxrwxrwx 1 root root   62 Apr  7  2014 zenity-colorselection-screenshot.png -> ../../../C/zenity/figures/zenity-colorselection-screenshot.png
<snip>

```

Not that this helps, but
[INDENT][INDENT][INDENT]I might be remiss otherwise
[/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2015-07-20
> **Bashing-om said:**
> mc4man; Hello;

I have not paid close attention to this thread, but on my 14.04 system the symlink still exists :
```

sysop@1404mini:~$ ls -al /usr/share/help/ca/zenity/figures/
total 56
drwxr-xr-x 2 root root 4096 Jul  6  2014 .
drwxr-xr-x 3 root root 4096 Jul  6  2014 ..
lrwxrwxrwx 1 root root   74 Apr  7  2014 zenity-calendar-screenshot.png -> ../../../../help-langpack/ca/zenity/figures/zenity-calendar-screenshot.png
lrwxrwxrwx 1 root root   62 Apr  7  2014 zenity-colorselection-screenshot.png -> ../../../C/zenity/figures/zenity-colorselection-screenshot.png
<snip>

```

Not that this helps, but
[INDENT][INDENT][INDENT]I might be remiss otherwise
[/INDENT][/INDENT][/INDENT]
The Op did some sort of upgrade to 15.04 & I think the symlinks were left behind & could be the reason why these 2 common packages can't be upgraded.  So at this point i'd just get rid of them, can't make anything worse, may just solve..
(- and if any other symlinks come up with same error then remove them also..

---

### Post by oglipogli2 on 2015-07-22
> **mc4man said:**
> Get rid of those 2 symlinks, in 14.04 they were links, now actual files, (at least the 1st. one.
```
sudo rm /usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png
```
```
sudo rm /usr/share/help/oc/evolution/contacts-usage-delete-contact.page

```
```
sudo apt-get clean && sudo apt-get dist-upgrade
```

the output for the above are as follows

```
$ sudo rm /usr/share/help/ca/zenity/figures/zenity-calendar-screenshot.png
[sudo] password for oglipogli: 
oglipogli@oglipogli-PORTEGE-M600:~$ sudo rm /usr/share/help/oc/evolution/contacts-usage-delete-contact.page
oglipogli@oglipogli-PORTEGE-M600:~$ sudo apt-get clean && sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.12.11-0ubuntu3) but 3.12.10-0ubuntu1~14.10.1 is installed
 zenity : Depends: zenity-common (= 3.14.0-1) but 3.12.1-1.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by bapoumba on 2015-07-22
As far as I can see, the installed evolution 3.12.10-0ubuntu1~14.10.1 is a backport for utopic. I also see you have utopic and trusty ppas.
Please uncheck these ppas and try to update/upgrade again, thanks.

---

### Post by oglipogli2 on 2015-08-01
Dear All,

I guess my hardware gave up on me, because now every time i boot into the system, Ubuntu goes into its built in shell. Busybox .

I think this thread must be declared closed.

thanks & regards

---

### Post by Bashing-om on 2015-08-01
oglipogli2; Hey;

> **oglipogli2 said:**
> Dear All,

I guess my hardware gave up on me, because now every time i boot into the system, Ubuntu goes into its built in shell. Busybox .

I think this thread must be declared closed.

thanks & regards

Let's start a new thread on this new issue, and fix the boot loader. 
Then if need be return to this thread.

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

