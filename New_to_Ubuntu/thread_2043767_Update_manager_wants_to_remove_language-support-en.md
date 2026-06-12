---
title: "Update manager wants to remove language-support-en"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by peterson43 on 2012-08-17
Today when update manager started up it gave me a message that for some reason only a partial upgrade would be completed. I'm not sure why that is, but I proceeded to continue. However, when it gave the details of what would be done it said that it would remove 1 package. I clicked to see what package would be removed at it was the language-support-en package for English language support. 

I cancelled the update at that point because I don't want to lose English from my Ubuntu installation. Does anyone have ideas for what I should do? What would happen if I did remove that package?

---

### Post by NikTh on 2012-08-17
Hi , 
please open a terminal (ctrl+alt+t) and post the output of 
```
sudo apt-get update ; sudo apt-get dist-upgrade
``` 
you can cancel the installation with n(no) but we want to see the full output. 

Please put the results inside [CODE] tags , by highlighting the output and click the** #** button on message toolbar.
Thanks

---

### Post by peterson43 on 2012-08-17
> **NikTh said:**
> Hi , 
please open a terminal (ctrl+alt+t) and post the output of 
```
sudo apt-get update ; sudo apt-get dist-upgrade
``` 
you can cancel the installation with n(no) but we want to see the full output. 

I ran that command and got the following output
```

Fetched 2,767 B in 21s (129 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  language-support-en
The following packages will be upgraded:
  aptdaemon aptdaemon-data compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default dconf-gsettings-backend dconf-service dconf-tools
  flashplugin-downloader flashplugin-installer gcalctool gnome-settings-daemon
  google-chrome-stable indicator-weather libdconf-dbus-1-0 libdconf0
  libdecoration0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libmission-control-plugins0 libnspr4 libnspr4-0d libnux-2.0-0
  libnux-2.0-common libperl5.14 libsqlite3-0 libxatracker1 nux-tools perl
  perl-base perl-modules python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets
  python-aptdaemon.pkcompat telepathy-mission-control-5 tzdata tzdata-java
  xserver-xorg-video-intel
44 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 51.4 MB of archives.
After this operation, 371 kB disk space will be freed.
Do you want to continue [Y/n]? 

```
There was a bunch of stuff preceeding this that I think was just the log of the communications with the mirrors and software sources. If you want that included too I can list that as well.

---

### Post by peterson43 on 2012-08-17
Not sure if this will help or not, but I noticed that when I open up update manager there are two updates that are not checked. Maybe this is the reason why it says it will be a "partial upgrade." These are the Netscape Portable Runtime Library, libnspr4 and libnspr4-0d.

Again, I'm not sure if this has anything to do with update manager wanting to remove the English language package, but I thought it might help someone figure out what's going on.

---

### Post by NikTh on 2012-08-17
Hi , 
what version of Ubuntu you are running ? 
```
cat /etc/lsb-release && uname -r
``` 
Thanks

---

### Post by peterson43 on 2012-08-17
> **NikTh said:**
> Hi , 
what version of Ubuntu you are running ? 
```
cat /etc/lsb-release && uname -r
``` 
Thanks

I'm running Ubuntu 12.04
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
3.2.0-29-generic-pae

```

---

### Post by NikTh on 2012-08-17
Hi  , 
I cannot understand what this package.. "language-support-en" ... is.
We have the same Distribution but when i tried to locate this package.. just fails.. 

```
apt-cache policy language-support-en
N: Unable to locate package language-support-en
``````
apt-cache show language-support
N: Unable to locate package language-support
E: No packages found
```It seems that this package is not in Official repositories anymore ? 

Package language-pack-en , exists instead. 
```
apt-cache policy language-pack-en 
language-pack-en:
  Installed: 1:12.04+20120801
  Candidate: 1:12.04+20120801
  Version table:
 *** 1:12.04+20120801 0
        500 http://gr.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
``````
apt-cache show language-pack-en

Package: language-pack-en
Priority: optional
Section: translations
Installed-Size: 30
Maintainer: Language pack maintainers <language-packs@ubuntu.com>
Architecture: all
Version: 1:12.04+20120801
Replaces: language-pack-en (<< 1:12.04+20120801), language-pack-en-base, language-pack-gnome-en (<< 1:12.04+20120801), language-pack-gnome-en-base (<< 1:12.04+20120801), language-pack-kde-en (<< 1:12.04+20120801), language-pack-kde-en-base (<< 1:12.04+20120801)
Depends: language-pack-en-base (>= 1:12.04+20120801)
Pre-Depends: dpkg (>= 1.10.27ubuntu1)
Filename: pool/main/l/language-pack-en/language-pack-en_12.04+20120801_all.deb
Size: 1994
MD5sum: b98f4f8b6d876982de5a61d2460b4f73
SHA1: e629c62b981d6b39437970240d7df3b858a596fd
SHA256: 9da209f64207305da0855551178d6f591fcd70aff93046a5f6fdf6fc4c2f6897
Description-en: translation updates for language English
 Translation data updates for all supported packages for:
 English
 .
 language-pack-en-base provides the bulk of translation data
 and is updated only seldom. This package provides frequent translation
 updates.
Description-md5: 1d50dcc1c889caf78b59116d95acb689
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-live, ubuntu-usb-live, kubuntu-live, kubuntu-active-live, kubuntu-active-live, edubuntu-live, edubuntu-usb-live, edubuntu-dvd-live, xubuntu-live, lubuntu-live, ubuntustudio-dvd-live

Package: language-pack-en
Priority: optional
Section: translations
Installed-Size: 30
Maintainer: Language pack maintainers <language-packs@ubuntu.com>
Architecture: all
Version: 1:12.04+20120417
Replaces: language-pack-en (<< 1:12.04+20120417), language-pack-en-base, language-pack-gnome-en (<< 1:12.04+20120417), language-pack-gnome-en-base (<< 1:12.04+20120417), language-pack-kde-en (<< 1:12.04+20120417), language-pack-kde-en-base (<< 1:12.04+20120417)
Depends: language-pack-en-base (>= 1:12.04+20120417)
Pre-Depends: dpkg (>= 1.10.27ubuntu1)
Filename: pool/main/l/language-pack-en/language-pack-en_12.04+20120417_all.deb
Size: 1970
MD5sum: 0d0d6984983b4c51ccca3e00beb9fc71
SHA1: d207039ba6ba657ddeea53efd77272a3b038bf02
SHA256: 55705c457fe741f581bf49e2abd617666b30856669bce7f5dd6544ed0f398442
Description-en: translation updates for language English
 Translation data updates for all supported packages for:
 English
 .
 language-pack-en-base provides the bulk of translation data
 and is updated only seldom. This package provides frequent translation
 updates.
Description-md5: 1d50dcc1c889caf78b59116d95acb689
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-live, ubuntu-usb-live, kubuntu-live, kubuntu-active-live, kubuntu-active-live, edubuntu-live, edubuntu-usb-live, edubuntu-dvd-live, xubuntu-live, lubuntu-live, ubuntustudio-dvd-live
```Maybe different packages for different architectures ? (I have Ubuntu 64bit). 
Hmmm... I am not very sure but in your position I would do the update from terminal... 
```
sudo apt-get update ; sudo apt-get dist-upgrade
```dist-upgrade is more secure (solves conflicts) command and terminal is more trustworthy than Update manager (GUI)
Thanks

---

### Post by peterson43 on 2012-08-17
> **NikTh said:**
> Hi  , 
I cannot understand what this package.. "language-support-en" ... is.
We have the same Distribution but when i tried to locate this package.. just fails.. 


I can get the following information on the language-support-en package from Synaptic Package Manager
> 
This metapackage depends on all packages that provide native language
support for applications. (like spell checkers,
dictionaries, OpenOffice and Mozilla locale packages, etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-en.

Language: English

Not exactly sure what to make of this information, but it seems that at worst my spell checkers would maybe stop working. I don't think I'd suddenly be using a Spanish version of Ubuntu or anything.

---

### Post by fleamour on 2012-08-17
*BUMP*

Me too!

Any solution?

---

### Post by fleamour on 2012-08-17
I was always told you must never do a partial update as it can break the system.  However I think this applies to pre-release betas rather than this situation?

:confused: :-k :confused:

---

### Post by CoreyB. on 2012-08-17
language-support-en is not in the 12.04 repos. The last release to have it was natty.

Did you upgrade from natty (11.04), [language-support-en is in there]("http://packages.ubuntu.com/natty/language-support-en")?

It appears that language-support-en is just a metapackage anyways, I don't think any harm will happen if you remove it.

---

### Post by fleamour on 2012-08-17
Ah, thank you for clarification.

Would seem safe to proceed then.

---

### Post by peterson43 on 2012-08-17
I did an update from the terminal like NikTh suggested. So far I haven't noticed any problems. I opened up LibreOffice and the spell checker seems to still work. I'll post if I find any issues later.

---

### Post by Deepak J on 2012-08-17
have you tried to upgrade to 12.10 but cancelled that in the middle...?

---

### Post by bogan on 2012-08-17
Hi!, **All,**

I have just had the same problem, before reading this Thread.

The differences are : I am running 12.04.1 LTS - GENERIC - not PAE - v3.2.0-29 #46, updated originally from 9.1:

 I Previosly had the same 'Partial Update' message and updated from a terminal, ran ```
sudo apt-get -f install
sudo dpkg --configure -a
```following screen prompts.

After that, Update Manager seemed OK, until today, and I ran the partial update leaving the two Netscape files unticked. I then ran ```
sudo apt-get update
 sudo apt-get upgrade
```It reported that the two libnspr4 files were "held Back". So I then ran ```
sudo dpkg-reconfigure libnspr4 libnspr4-0d
```And this is when it said 'language-support-en' would be removed and installed the 4.89-1  version of those lib files.

After checking Synaptic - I could not find anything - I removed the 'language-support-en' package, after trying to update it - it gave "could not find xxxx".

At the moment, everything seems normal, including UM.

Chao!, **bogan.**

---

### Post by peterson43 on 2012-08-20
Update: I still haven't had any problems after I did my update as NikTh suggested. I did upgrade to 12.04 from a previous version of Ubuntu so maybe that's why that package was there in the first place. I still don't understand why it wanted to do the partial upgrade, but at least it hasn't seemed to cause any problems.

---

