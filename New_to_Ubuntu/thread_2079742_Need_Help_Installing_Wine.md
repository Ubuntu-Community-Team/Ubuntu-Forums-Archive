---
title: "Need Help Installing Wine"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by rtwaller on 2012-11-02
I am running the current version of Ubuntu and I am having trouble installing wine. I tried to get it from the terminal, but I get this

> rtwaller@ubuntu:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
wine1.5 : Depends: wine1.5-i386 (= 1.5.16-0ubuntu1) but it is not installable
Recommends: ttf-droid
Recommends: ttf-mscorefonts-installer but it is not going to be installed
Recommends: ttf-umefont but it is not going to be installed
Recommends: ttf-unfonts-core but it is not going to be installed
Recommends: winbind but it is not going to be installed
Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



Just FYI I am really a novice user. I am new to Linux and I have basically no experience with the terminal.

Thanks ahead of time for any help.

---

### Post by NikTh on 2012-11-02
Hi ,

try ```
sudo apt-get install wine 
sudo apt-get install -f
```Also give the results of 
```
dpkg -l | grep -i wine 
lsb_release -rcd ; uname -r
apt-cache policy wine*
```

Put the results between these brackets [noparse]```
the results here
```[/noparse] to be easy to read.

Thanks

---

### Post by Mark Phelps on 2012-11-02
Since you're "new to Linux", you could save yourself a lot of time and grief if you tell us WHY you want to install Wine.

Why?

Because the two most common things folks use in MS Windows -- Internet Explorer and MS Office -- work very poorly in Wine.

You could also go to the WineHQ Application Compatibility website and look up the ratings for the Windows apps you want to run.  If they aren't listed, or if they are rated lower than Gold, then installing Wine is a waste of your time.

---

### Post by rtwaller on 2012-11-02
Thanks a lot for taking the time to help me out.

```
rtwaller@ubuntu:~$ sudo apt-get install wine 
[sudo] password for rtwaller: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
rtwaller@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rtwaller@ubuntu:~$ dpkg -l | grep -i wine 
rtwaller@ubuntu:~$ lsb_release -rcd ; uname -r
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
3.5.0-17-generic
rtwaller@ubuntu:~$ apt-cache policy wine*
libchewing3-dbg:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wxwin2.4-headers:
  Installed: (none)
  Candidate: (none)
  Version table:
libchewing3-dev:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
windows-el:
  Installed: (none)
  Candidate: 2.41-3
  Version table:
     2.41-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winff-dbg:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
arc-wine:
  Installed: (none)
  Candidate: (none)
  Version table:
libpam-winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
winefish:
  Installed: (none)
  Candidate: 1.3.3-0dl1ubuntu2
  Version table:
     1.3.3-0dl1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wxwin-i18n:
  Installed: (none)
  Candidate: (none)
  Version table:
winff-doc:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing3-data:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
kdeartwork-theme-window:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2
  Version table:
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
plplot9-driver-xwin:
  Installed: (none)
  Candidate: (none)
  Version table:
fte-xwindow:
  Installed: (none)
  Candidate: 0.50.2b6-1
  Version table:
     0.50.2b6-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-windowsbase3.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wine1.3-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.4-amd64:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
wings3d:
  Installed: (none)
  Candidate: 1.4.1-4
  Version table:
     1.4.1-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinglutils1abi1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
freepwing:
  Installed: (none)
  Candidate: 1.5-1
  Version table:
     1.5-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinactiveeffects1abi4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.5-i386:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.0:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.2:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.3:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.5:
  Installed: (none)
  Candidate: 1.5.16-0ubuntu1
  Version table:
     1.5.16-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
libmono-system-windows-forms4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libmono-system-drawing4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
account-plugin-windows-live:
  Installed: 0.8-0ubuntu2
  Candidate: 0.8-0ubuntu2
  Version table:
 *** 0.8-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
windowlab:
  Installed: (none)
  Candidate: 1.40-1
  Version table:
     1.40-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx1-java-doc:
  Installed: (none)
  Candidate: 1:1.0-1
  Version table:
     1:1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
x-window-manager:
  Installed: (none)
  Candidate: (none)
  Version table:
x-window-system:
  Installed: (none)
  Candidate: (none)
  Version table:
ibus-chewing:
  Installed: (none)
  Candidate: 1.3.10+clean-3build1
  Version table:
     1.3.10+clean-3build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libwings-dev:
  Installed: (none)
  Candidate: 0.95.3-2ubuntu1
  Version table:
     0.95.3-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing:
  Installed: (none)
  Candidate: (none)
  Version table:
kmfl-keyboards-mywin:
  Installed: (none)
  Candidate: 2.1.1-2
  Version table:
     2.1.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
openwince-include:
  Installed: (none)
  Candidate: 0.3.2-3.1
  Version table:
     0.3.2-3.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind-setjmp0:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
q4wine-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
kde-window-manager-active:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
not+darwin:
  Installed: (none)
  Candidate: (none)
  Version table:
libswingx-java:
  Installed: (none)
  Candidate: 1:1.6.2-1
  Version table:
     1:1.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wininfo:
  Installed: (none)
  Candidate: 0.7-5
  Version table:
     0.7-5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winbind4:
  Installed: (none)
  Candidate: 4.0.0~beta2+dfsg1-3
  Version table:
     4.0.0~beta2+dfsg1-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
worldwind:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
winff:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kde-window-manager-gles:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-mono0.0.4:
  Installed: (none)
  Candidate: 0.0.4-0ubuntu1~ppa1
  Version table:
     0.0.4-0ubuntu1~ppa1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
libjswingreader-java:
  Installed: (none)
  Candidate: 0.3-1
  Version table:
     0.3-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-mono0.0.8:
  Installed: (none)
  Candidate: 0.0.8-0ubuntu1~ppa1
  Version table:
     0.0.8-0ubuntu1~ppa1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
libkwineffects1abi4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingworker-java:
  Installed: (none)
  Candidate: 1.1-0ubuntu3
  Version table:
     1.1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
gnome-wine-icon-theme:
  Installed: (none)
  Candidate: 5.5.1-1ubuntu1
  Version table:
     5.5.1-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind-setjmp0-dev:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
x-window-system-core:
  Installed: (none)
  Candidate: (none)
  Version table:
hwinfo:
  Installed: (none)
  Candidate: 16.0-2.2
  Version table:
     16.0-2.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin-style-skulpture:
  Installed: (none)
  Candidate: 0.2.4-0ubuntu3
  Version table:
     0.2.4-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libjenkins-winstone-java:
  Installed: (none)
  Candidate: 0.9.10-jenkins-37+dfsg-1
  Version table:
     0.9.10-jenkins-37+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing3:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
matchbox-window-manager:
  Installed: (none)
  Candidate: 1.2-7ubuntu1
  Version table:
     1.2-7ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libapache2-mod-auth-ntlm-winbind:
  Installed: (none)
  Candidate: 0.0.0.lorikeet+svn+801-1
  Version table:
     0.0.0.lorikeet+svn+801-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
pd-windowing:
  Installed: (none)
  Candidate: 0.1-2
  Version table:
     0.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-common:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-gecko1.4:
  Installed: (none)
  Candidate: 1.4.0-0ubuntu2
  Version table:
     1.4.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
wine-gecko1.7:
  Installed: (none)
  Candidate: 1.7-0ubuntu1~ppa1~precise1
  Version table:
     1.7-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
wine-gecko1.8:
  Installed: (none)
  Candidate: 1.8-0ubuntu1~ppa1~precise1
  Version table:
     1.8-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
libwind0-heimdal:
  Installed: 1.6~git20120403+dfsg1-2
  Candidate: 1.6~git20120403+dfsg1-2
  Version table:
 *** 1.6~git20120403+dfsg1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
kde-window-manager:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-system-windows-forms-datavisualization4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
kde-window-manager-common:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libsfml-window1.6:
  Installed: (none)
  Candidate: 1.6+dfsg2-2build1
  Version table:
     1.6+dfsg2-2build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing-data:
  Installed: (none)
  Candidate: (none)
  Version table:
fcitx-chewing:
  Installed: (none)
  Candidate: 0.1.2-2
  Version table:
     0.1.2-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winetricks:
  Installed: (none)
  Candidate: 0.0+20120912
  Version table:
     0.0+20120912 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libtwin-dev:
  Installed: (none)
  Candidate: 12.04.13.17.57-g130ee5f-2
  Version table:
     12.04.13.17.57-g130ee5f-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-system-drawing-design4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wine-mono:
  Installed: (none)
  Candidate: (none)
  Version table:
navit-graphics-gtk-drawing-area:
  Installed: (none)
  Candidate: 0.5.0~svn5126+dfsg.1-2
  Version table:
     0.5.0~svn5126+dfsg.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-windowsbase4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wine-bin:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.5-amd64:
  Installed: (none)
  Candidate: 1.5.16-0ubuntu1
  Version table:
     1.5.16-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
wine-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
win32-loader:
  Installed: (none)
  Candidate: (none)
  Version table:
libcsfml-window1.6:
  Installed: (none)
  Candidate: 1.6-1
  Version table:
     1.6-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libparse-win32registry-perl:
  Installed: (none)
  Candidate: 1.0-1
  Version table:
     1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
science-viewing:
  Installed: (none)
  Candidate: 0.16ubuntu2
  Version table:
     0.16ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-bin-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
libtwin0:
  Installed: (none)
  Candidate: 12.04.13.17.57-g130ee5f-2
  Version table:
     12.04.13.17.57-g130ee5f-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-dbg:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-dev:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libwin-hivex-perl:
  Installed: (none)
  Candidate: 1.3.6-2
  Version table:
     1.3.6-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind7-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
q4wine:
  Installed: (none)
  Candidate: 0.121-4
  Version table:
     0.121-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.2-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
ucimf-chewing:
  Installed: (none)
  Candidate: 0.3-1+build1
  Version table:
     0.3-1+build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kwin-style-dekorator:
  Installed: (none)
  Candidate: 0.5.1-1ubuntu2
  Version table:
     0.5.1-1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kde-window-manager-active-gles:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine:
  Installed: (none)
  Candidate: 1.5.16-0ubuntu1
  Version table:
     1.5.16-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wing:
  Installed: (none)
  Candidate: 0.7-27.1build1
  Version table:
     0.7-27.1build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wink:
  Installed: (none)
  Candidate: (none)
  Version table:
all-knowing-dns:
  Installed: (none)
  Candidate: 1.3-1
  Version table:
     1.3-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-amd64:
  Installed: (none)
  Candidate: (none)
  Version table:
mono-winforms-a11y:
  Installed: (none)
  Candidate: 2.1-2
  Version table:
     2.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-i386:
  Installed: (none)
  Candidate: (none)
  Version table:
petitboot-twin:
  Installed: (none)
  Candidate: 12.03.29.20.47-g45e2534-2
  Version table:
     12.03.29.20.47-g45e2534-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
libwings2:
  Installed: (none)
  Candidate: 0.95.3-2ubuntu1
  Version table:
     0.95.3-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
worldwind-doc:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
libchewing2-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
avifile-win32-plugin:
  Installed: (none)
  Candidate: (none)
  Version table:
libswing-layout-java:
  Installed: (none)
  Candidate: 1.0.4-2
  Version table:
     1.0.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswing-layout-java-doc:
  Installed: (none)
  Candidate: 1.0.4-2
  Version table:
     1.0.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx1-java:
  Installed: (none)
  Candidate: 1:1.0-1
  Version table:
     1:1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
not+bsd-darwin:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin4-style-bespin:
  Installed: (none)
  Candidate: (none)
  Version table:
libkwinactiveglesutils1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinglesutils1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx-java-doc:
  Installed: (none)
  Candidate: 1:1.6.2-1
  Version table:
     1:1.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kwin-style-qtcurve:
  Installed: (none)
  Candidate: 1.8.14-1
  Version table:
     1.8.14-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
gextractwinicons:
  Installed: (none)
  Candidate: 0.3.1-1
  Version table:
     0.3.1-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
openwince-jtag:
  Installed: (none)
  Candidate: 0.5.1-6
  Version table:
     0.5.1-6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
hime-chewing:
  Installed: (none)
  Candidate: 0.9.9+git20120619+dfsg-1
  Version table:
     0.9.9+git20120619+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wing-data:
  Installed: (none)
  Candidate: 0.7-27.1build1
  Version table:
     0.7-27.1build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libjenkins-winstone-java-doc:
  Installed: (none)
  Candidate: 0.9.10-jenkins-37+dfsg-1
  Version table:
     0.9.10-jenkins-37+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
python-strongwind:
  Installed: (none)
  Candidate: 0.9-2build1
  Version table:
     0.9-2build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
scim-chewing:
  Installed: (none)
  Candidate: 0.3.4-4ubuntu2
  Version table:
     0.3.4-4ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
plplot11-driver-xwin:
  Installed: (none)
  Candidate: 5.9.9-5
  Version table:
     5.9.9-5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
phylowin:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin-style-crystal:
  Installed: (none)
  Candidate: 2.2.0-0ubuntu1
  Version table:
     2.2.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libworldwind-java:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
gcin-chewing:
  Installed: (none)
  Candidate: 2.7.6.1+dfsg-1
  Version table:
     2.7.6.1+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
avant-window-navigator:
  Installed: (none)
  Candidate: (none)
  Version table:
winkeydaemon:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.5-dbg:
  Installed: (none)
  Candidate: 1.5.16-0ubuntu1
  Version table:
     1.5.16-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
uim-chewing:
  Installed: (none)
  Candidate: 0.1.0-2
  Version table:
     0.1.0-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libnss-winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
winpdb:
  Installed: (none)
  Candidate: 1.4.8-2
  Version table:
     1.4.8-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.5-dev:
  Installed: (none)
  Candidate: 1.5.16-0ubuntu1
  Version table:
     1.5.16-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main amd64 Packages
libunwind8-dev:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libkwinactiveglutils1abi1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-uia-winforms1.0-cil:
  Installed: (none)
  Candidate: 2.1-2
  Version table:
     2.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind8:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libkwinactivenvidiahack4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingworker-java-doc:
  Installed: (none)
  Candidate: 1.1-0ubuntu3
  Version table:
     1.1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
shiki-wine-theme:
  Installed: (none)
  Candidate: 4.6-1ubuntu2
  Version table:
     4.6-1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-winforms2.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
ttf-symbol-replacement-wine1.3:
  Installed: (none)
  Candidate: (none)
  Version table:
winwrangler:
  Installed: (none)
  Candidate: 0.2.4-3
  Version table:
     0.2.4-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
emacs-window-layout:
  Installed: (none)
  Candidate: 1.1-2
  Version table:
     1.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libfreehep-swing-java:
  Installed: (none)
  Candidate: 2.0.3-3
  Version table:
     2.0.3-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinnvidiahack4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
rtwaller@ubuntu:~$ 

```

---

### Post by rtwaller on 2012-11-02
Well I really just want to play around with it a bit and see how it does for various programs. For one thing, I like Gimp, but if I could get a version of photoshop running well I would be very happy (they have CS2 in the gold category).

I said I was new to linux, not new to using computers. I have no interest in using Internet Explorer and I like the Libre Suite.

---

### Post by NikTh on 2012-11-02
Do you want the latest version of wine ? I saw you have added the **ppa:ubuntu-wine/ppa** and you running Quantal (12.10) . I'm not sure but I think this ppa has not full support (yet) for Quantal. 

Try this 

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
```

Thanks

---

### Post by rtwaller on 2012-11-02
This is what I got this time and it is true though, if this is going to be too much of a hassle, don't feel like you have to bother helping anymore. This isn't that big of a deal. I would mainly just like to be able to use Photoshop.

```
rtwaller@ubuntu:~$ sudo apt-get install ppa-purge
[sudo] password for rtwaller: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude aptitude-common libboost-iostreams1.49.0 libcwidget3 libept1.4.12
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libboost-iostreams1.49.0 libcwidget3 libept1.4.12
  ppa-purge
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,637 kB of archives.
After this operation, 10.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ quantal/main aptitude-common all 0.6.8.1-2ubuntu1 [669 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ quantal/main libboost-iostreams1.49.0 amd64 1.49.0-3.1ubuntu1 [38.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ quantal/main libcwidget3 amd64 0.5.16-3.4ubuntu1 [387 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ quantal/main libept1.4.12 amd64 1.0.9 [135 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ quantal/main aptitude amd64 0.6.8.1-2ubuntu1 [1,404 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ quantal/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,637 kB in 4s (648 kB/s)     
Selecting previously unselected package aptitude-common.
(Reading database ... 180205 files and directories currently installed.)
Unpacking aptitude-common (from .../aptitude-common_0.6.8.1-2ubuntu1_all.deb) ...
Selecting previously unselected package libboost-iostreams1.49.0.
Unpacking libboost-iostreams1.49.0 (from .../libboost-iostreams1.49.0_1.49.0-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.4ubuntu1_amd64.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.9_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.8.1-2ubuntu1_amd64.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up aptitude-common (0.6.8.1-2ubuntu1) ...
Setting up libboost-iostreams1.49.0 (1.49.0-3.1ubuntu1) ...
Setting up libcwidget3 (0.5.16-3.4ubuntu1) ...
Setting up libept1.4.12 (1.0.9) ...
Setting up aptitude (0.6.8.1-2ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rtwaller@ubuntu:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Package revert list generated:


Disabling ubuntu-wine PPA from 
/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
rtwaller@ubuntu:~$ sudo apt-get update
Ign http://linux.dropbox.com precise InRelease
Ign http://ppa.launchpad.net quantal InRelease                                 
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Ign http://archive.ubuntu.com quantal InRelease                                
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://archive.ubuntu.com quantal-updates InRelease                        
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1,029 B]           
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal Release.gpg                              
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal-updates Release.gpg                      
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://archive.ubuntu.com quantal Release                                  
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://archive.ubuntu.com quantal-updates Release                          
Hit http://archive.ubuntu.com quantal/main amd64 Packages                      
Hit http://ppa.launchpad.net quantal/main Sources                              
Ign http://linux.dropbox.com precise/main Translation-en_US                  
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Ign http://linux.dropbox.com precise/main Translation-en                     
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                  
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                
Ign http://security.ubuntu.com quantal-security InRelease                    
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://security.ubuntu.com quantal-security Release.gpg
Hit http://archive.ubuntu.com quantal/main Translation-en
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://security.ubuntu.com quantal-security Release
Hit http://security.ubuntu.com quantal-security/main amd64 Packages   
Hit http://archive.ubuntu.com quantal/multiverse Translation-en
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages
Hit http://security.ubuntu.com quantal-security/main Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-en
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit http://archive.ubuntu.com quantal-updates/main Translation-en
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal/main Translation-en_US
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US             
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal/universe Translation-en_US               
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US           
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US       
Fetched 4,121 B in 6s (589 B/s)                                                
Reading package lists... Done
rtwaller@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
rtwaller@ubuntu:~$ 

```

---

### Post by NikTh on 2012-11-02
```
sudo apt-get update --fix-missing
sudo apt-get dist-upgrade
sudo apt-get install -f
``` 
and give the results again

```
apt-cache policy wine*
``` 

> I would mainly just like to be able to use Photoshop.
I don't know if photoshop works correct in wine , but this is not related to your problem. You have to be able to install any package you want from main repositories. 

Gimp is a good alternate of photoshop if you want to try :
[http://www.gimp.org/](http://www.gimp.org/) (is in the main repositories too)

Thanks

---

### Post by rtwaller on 2012-11-02
According to Wine's website, Photoshop CS2 should work well, but as I said, I will be fine using Gimp is this is too much work to get figured out.

```
rtwaller@ubuntu:~$ sudo apt-get update --fix-missing
[sudo] password for rtwaller: 
Ign http://linux.dropbox.com precise InRelease
Ign http://security.ubuntu.com quantal-security InRelease                      
Hit http://linux.dropbox.com precise Release.gpg                               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://linux.dropbox.com precise Release                                   
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://linux.dropbox.com precise/main amd64 Packages                       
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://security.ubuntu.com quantal-security/main amd64 Packages            
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages      
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages        
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages      
Hit http://ppa.launchpad.net quantal/main Sources                              
Ign http://linux.dropbox.com precise/main Translation-en_US 
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US   
Ign http://ppa.launchpad.net quantal/main Translation-en_US 
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en    
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en_US 
Ign http://ppa.launchpad.net quantal/main Translation-en    
Ign http://archive.ubuntu.com quantal InRelease
Ign http://archive.ubuntu.com quantal-updates InRelease
Hit http://archive.ubuntu.com quantal Release.gpg
Get:1 http://archive.ubuntu.com quantal-updates Release.gpg [933 B]
Hit http://archive.ubuntu.com quantal Release                                  
Get:2 http://archive.ubuntu.com quantal-updates Release [49.6 kB]              
Hit http://archive.ubuntu.com quantal/main amd64 Packages                      
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                  
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                
Hit http://archive.ubuntu.com quantal/main Translation-en                      
Hit http://archive.ubuntu.com quantal/multiverse Translation-en                
Hit http://archive.ubuntu.com quantal/restricted Translation-en                
Hit http://archive.ubuntu.com quantal/universe Translation-en                  
Get:3 http://archive.ubuntu.com quantal-updates/main amd64 Packages [46.7 kB]  
Get:4 http://archive.ubuntu.com quantal-updates/restricted amd64 Packages [14 B]
Get:5 http://archive.ubuntu.com quantal-updates/universe amd64 Packages [19.9 kB]
Get:6 http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages [14 B]
Hit http://archive.ubuntu.com quantal-updates/main Translation-en              
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en        
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en          
Ign http://archive.ubuntu.com quantal/main Translation-en_US                   
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US             
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal/universe Translation-en_US               
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US           
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US       
Fetched 117 kB in 12s (9,079 B/s)                                              
Reading package lists... Done
rtwaller@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rtwaller@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rtwaller@ubuntu:~$ apt-cache policy wine*
libchewing3-dbg:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wxwin2.4-headers:
  Installed: (none)
  Candidate: (none)
  Version table:
libchewing3-dev:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
windows-el:
  Installed: (none)
  Candidate: 2.41-3
  Version table:
     2.41-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winff-dbg:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
arc-wine:
  Installed: (none)
  Candidate: (none)
  Version table:
libpam-winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
winefish:
  Installed: (none)
  Candidate: 1.3.3-0dl1ubuntu2
  Version table:
     1.3.3-0dl1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wxwin-i18n:
  Installed: (none)
  Candidate: (none)
  Version table:
winff-doc:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing3-data:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
kdeartwork-theme-window:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2
  Version table:
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
plplot9-driver-xwin:
  Installed: (none)
  Candidate: (none)
  Version table:
fte-xwindow:
  Installed: (none)
  Candidate: 0.50.2b6-1
  Version table:
     0.50.2b6-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-windowsbase3.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wine1.3-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.4-amd64:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
wings3d:
  Installed: (none)
  Candidate: 1.4.1-4
  Version table:
     1.4.1-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinglutils1abi1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
freepwing:
  Installed: (none)
  Candidate: 1.5-1
  Version table:
     1.5-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinactiveeffects1abi4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.0:
  Installed: (none)
  Candidate: (none)
  Version table:
wine1.2:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.3:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.5:
  Installed: (none)
  Candidate: (none)
  Version table:
libmono-system-windows-forms4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libmono-system-drawing4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
account-plugin-windows-live:
  Installed: 0.8-0ubuntu2
  Candidate: 0.8-0ubuntu2
  Version table:
 *** 0.8-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
windowlab:
  Installed: (none)
  Candidate: 1.40-1
  Version table:
     1.40-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx1-java-doc:
  Installed: (none)
  Candidate: 1:1.0-1
  Version table:
     1:1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
x-window-manager:
  Installed: (none)
  Candidate: (none)
  Version table:
x-window-system:
  Installed: (none)
  Candidate: (none)
  Version table:
ibus-chewing:
  Installed: (none)
  Candidate: 1.3.10+clean-3build1
  Version table:
     1.3.10+clean-3build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libwings-dev:
  Installed: (none)
  Candidate: 0.95.3-2ubuntu1
  Version table:
     0.95.3-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing:
  Installed: (none)
  Candidate: (none)
  Version table:
kmfl-keyboards-mywin:
  Installed: (none)
  Candidate: 2.1.1-2
  Version table:
     2.1.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
openwince-include:
  Installed: (none)
  Candidate: 0.3.2-3.1
  Version table:
     0.3.2-3.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind-setjmp0:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
q4wine-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
kde-window-manager-active:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
not+darwin:
  Installed: (none)
  Candidate: (none)
  Version table:
libswingx-java:
  Installed: (none)
  Candidate: 1:1.6.2-1
  Version table:
     1:1.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wininfo:
  Installed: (none)
  Candidate: 0.7-5
  Version table:
     0.7-5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winbind4:
  Installed: (none)
  Candidate: 4.0.0~beta2+dfsg1-3
  Version table:
     4.0.0~beta2+dfsg1-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
worldwind:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
winff:
  Installed: (none)
  Candidate: 1.4.2-3ubuntu1
  Version table:
     1.4.2-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kde-window-manager-gles:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libjswingreader-java:
  Installed: (none)
  Candidate: 0.3-1
  Version table:
     0.3-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwineffects1abi4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingworker-java:
  Installed: (none)
  Candidate: 1.1-0ubuntu3
  Version table:
     1.1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
gnome-wine-icon-theme:
  Installed: (none)
  Candidate: 5.5.1-1ubuntu1
  Version table:
     5.5.1-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind-setjmp0-dev:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
x-window-system-core:
  Installed: (none)
  Candidate: (none)
  Version table:
hwinfo:
  Installed: (none)
  Candidate: 16.0-2.2
  Version table:
     16.0-2.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin-style-skulpture:
  Installed: (none)
  Candidate: 0.2.4-0ubuntu3
  Version table:
     0.2.4-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libjenkins-winstone-java:
  Installed: (none)
  Candidate: 0.9.10-jenkins-37+dfsg-1
  Version table:
     0.9.10-jenkins-37+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing3:
  Installed: (none)
  Candidate: 0.3.3-4
  Version table:
     0.3.3-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
matchbox-window-manager:
  Installed: (none)
  Candidate: 1.2-7ubuntu1
  Version table:
     1.2-7ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libapache2-mod-auth-ntlm-winbind:
  Installed: (none)
  Candidate: 0.0.0.lorikeet+svn+801-1
  Version table:
     0.0.0.lorikeet+svn+801-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
pd-windowing:
  Installed: (none)
  Candidate: 0.1-2
  Version table:
     0.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-common:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-gecko1.4:
  Installed: (none)
  Candidate: 1.4.0-0ubuntu2
  Version table:
     1.4.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
libwind0-heimdal:
  Installed: 1.6~git20120403+dfsg1-2
  Candidate: 1.6~git20120403+dfsg1-2
  Version table:
 *** 1.6~git20120403+dfsg1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
kde-window-manager:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-system-windows-forms-datavisualization4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
kde-window-manager-common:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libsfml-window1.6:
  Installed: (none)
  Candidate: 1.6+dfsg2-2build1
  Version table:
     1.6+dfsg2-2build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing-data:
  Installed: (none)
  Candidate: (none)
  Version table:
fcitx-chewing:
  Installed: (none)
  Candidate: 0.1.2-2
  Version table:
     0.1.2-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
winetricks:
  Installed: (none)
  Candidate: 0.0+20120912
  Version table:
     0.0+20120912 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libtwin-dev:
  Installed: (none)
  Candidate: 12.04.13.17.57-g130ee5f-2
  Version table:
     12.04.13.17.57-g130ee5f-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-system-drawing-design4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
navit-graphics-gtk-drawing-area:
  Installed: (none)
  Candidate: 0.5.0~svn5126+dfsg.1-2
  Version table:
     0.5.0~svn5126+dfsg.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-windowsbase4.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
wine-bin:
  Installed: (none)
  Candidate: (none)
  Version table:
wine-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
win32-loader:
  Installed: (none)
  Candidate: (none)
  Version table:
libcsfml-window1.6:
  Installed: (none)
  Candidate: 1.6-1
  Version table:
     1.6-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libparse-win32registry-perl:
  Installed: (none)
  Candidate: 1.0-1
  Version table:
     1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
science-viewing:
  Installed: (none)
  Candidate: 0.16ubuntu2
  Version table:
     0.16ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-bin-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
libtwin0:
  Installed: (none)
  Candidate: 12.04.13.17.57-g130ee5f-2
  Version table:
     12.04.13.17.57-g130ee5f-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-dbg:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-dev:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libwin-hivex-perl:
  Installed: (none)
  Candidate: 1.3.6-2
  Version table:
     1.3.6-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind7-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
q4wine:
  Installed: (none)
  Candidate: 0.121-4
  Version table:
     0.121-4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.2-gecko:
  Installed: (none)
  Candidate: (none)
  Version table:
ucimf-chewing:
  Installed: (none)
  Candidate: 0.3-1+build1
  Version table:
     0.3-1+build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kwin-style-dekorator:
  Installed: (none)
  Candidate: 0.5.1-1ubuntu2
  Version table:
     0.5.1-1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kde-window-manager-active-gles:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu1
  Version table:
     1.4.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wing:
  Installed: (none)
  Candidate: 0.7-27.1build1
  Version table:
     0.7-27.1build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wink:
  Installed: (none)
  Candidate: (none)
  Version table:
all-knowing-dns:
  Installed: (none)
  Candidate: 1.3-1
  Version table:
     1.3-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-amd64:
  Installed: (none)
  Candidate: (none)
  Version table:
mono-winforms-a11y:
  Installed: (none)
  Candidate: 2.1-2
  Version table:
     2.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine1.4-i386:
  Installed: (none)
  Candidate: (none)
  Version table:
petitboot-twin:
  Installed: (none)
  Candidate: 12.03.29.20.47-g45e2534-2
  Version table:
     12.03.29.20.47-g45e2534-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libchewing-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
libwings2:
  Installed: (none)
  Candidate: 0.95.3-2ubuntu1
  Version table:
     0.95.3-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
worldwind-doc:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
libchewing2-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
avifile-win32-plugin:
  Installed: (none)
  Candidate: (none)
  Version table:
libswing-layout-java:
  Installed: (none)
  Candidate: 1.0.4-2
  Version table:
     1.0.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswing-layout-java-doc:
  Installed: (none)
  Candidate: 1.0.4-2
  Version table:
     1.0.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx1-java:
  Installed: (none)
  Candidate: 1:1.0-1
  Version table:
     1:1.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
not+bsd-darwin:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin4-style-bespin:
  Installed: (none)
  Candidate: (none)
  Version table:
libkwinactiveglesutils1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinglesutils1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingx-java-doc:
  Installed: (none)
  Candidate: 1:1.6.2-1
  Version table:
     1:1.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
kwin-style-qtcurve:
  Installed: (none)
  Candidate: 1.8.14-1
  Version table:
     1.8.14-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
gextractwinicons:
  Installed: (none)
  Candidate: 0.3.1-1
  Version table:
     0.3.1-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
openwince-jtag:
  Installed: (none)
  Candidate: 0.5.1-6
  Version table:
     0.5.1-6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
hime-chewing:
  Installed: (none)
  Candidate: 0.9.9+git20120619+dfsg-1
  Version table:
     0.9.9+git20120619+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wing-data:
  Installed: (none)
  Candidate: 0.7-27.1build1
  Version table:
     0.7-27.1build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libjenkins-winstone-java-doc:
  Installed: (none)
  Candidate: 0.9.10-jenkins-37+dfsg-1
  Version table:
     0.9.10-jenkins-37+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
python-strongwind:
  Installed: (none)
  Candidate: 0.9-2build1
  Version table:
     0.9-2build1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
scim-chewing:
  Installed: (none)
  Candidate: 0.3.4-4ubuntu2
  Version table:
     0.3.4-4ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
plplot11-driver-xwin:
  Installed: (none)
  Candidate: 5.9.9-5
  Version table:
     5.9.9-5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
phylowin:
  Installed: (none)
  Candidate: (none)
  Version table:
kwin-style-crystal:
  Installed: (none)
  Candidate: 2.2.0-0ubuntu1
  Version table:
     2.2.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
wine-unstable:
  Installed: (none)
  Candidate: (none)
  Version table:
winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libworldwind-java:
  Installed: (none)
  Candidate: 0.5.0-10
  Version table:
     0.5.0-10 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
gcin-chewing:
  Installed: (none)
  Candidate: 2.7.6.1+dfsg-1
  Version table:
     2.7.6.1+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
avant-window-navigator:
  Installed: (none)
  Candidate: (none)
  Version table:
winkeydaemon:
  Installed: (none)
  Candidate: (none)
  Version table:
uim-chewing:
  Installed: (none)
  Candidate: 0.1.0-2
  Version table:
     0.1.0-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libnss-winbind:
  Installed: (none)
  Candidate: 2:3.6.6-3ubuntu5
  Version table:
     2:3.6.6-3ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
winpdb:
  Installed: (none)
  Candidate: 1.4.8-2
  Version table:
     1.4.8-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind8-dev:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libkwinactiveglutils1abi1:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-uia-winforms1.0-cil:
  Installed: (none)
  Candidate: 2.1-2
  Version table:
     2.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libunwind8:
  Installed: (none)
  Candidate: 1.0.1-2ubuntu2
  Version table:
     1.0.1-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libkwinactivenvidiahack4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libswingworker-java-doc:
  Installed: (none)
  Candidate: 1.1-0ubuntu3
  Version table:
     1.1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
shiki-wine-theme:
  Installed: (none)
  Candidate: 4.6-1ubuntu2
  Version table:
     4.6-1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libmono-winforms2.0-cil:
  Installed: (none)
  Candidate: 2.10.8.1-5ubuntu1
  Version table:
     2.10.8.1-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
ttf-symbol-replacement-wine1.3:
  Installed: (none)
  Candidate: (none)
  Version table:
winwrangler:
  Installed: (none)
  Candidate: 0.2.4-3
  Version table:
     0.2.4-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
emacs-window-layout:
  Installed: (none)
  Candidate: 1.1-2
  Version table:
     1.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libfreehep-swing-java:
  Installed: (none)
  Candidate: 2.0.3-3
  Version table:
     2.0.3-3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
libkwinnvidiahack4:
  Installed: (none)
  Candidate: 4:4.9.2-0ubuntu2.1
  Version table:
     4:4.9.2-0ubuntu2.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
rtwaller@ubuntu:~$ 

```

---

### Post by NikTh on 2012-11-02
Try this and give the results 

```
sudo apt-get install wine1.4-amd64
```

---

### Post by rtwaller on 2012-11-02
```
rtwaller@ubuntu:~$ sudo apt-get install wine1.4-amd64
[sudo] password for rtwaller: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-amd64 : Depends: wine1.4-common (= 1.4.1-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
rtwaller@ubuntu:~$ 

```

---

### Post by NikTh on 2012-11-02
OK , lets examine something else here. 

Give the results of this command please 

```
[COLOR=#000000][FONT=Times New Roman]find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

[/FONT][/COLOR]

---

### Post by rtwaller on 2012-11-02
```
rtwaller@ubuntu:~$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
     2	deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
     3	deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse

/etc/apt/sources.list.d/jonoomph-openshot-edge-quantal.list

     1	deb http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu quantal main
     2	deb-src http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu quantal main

/etc/apt/sources.list.d/dropbox.list

     1	deb http://linux.dropbox.com/ubuntu precise main

/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list

     1	# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
     2	# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main

/etc/apt/sources.list.d/pidgin-ppa.list

     1	deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu quantal main
     2	deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu quantal main
rtwaller@ubuntu:~$ 

```

---

### Post by NikTh on 2012-11-02
I think you messed around with sources.list and PPAs. (?) . You have to know that your system can be corrupted very easy (especially the package manager) and especially if a release (like 12.10) is new  and you don't know if and what PPAs supported (yet). 

We will try some things . You can add all these PPAs later if you want. 

```
sudo ppa-purge ppa:jonoomph/openshot-edge
sudo ppa-purge ppa:pidgin-developers/ppa
sudo rm /etc/apt/sources.list.d/*.list 
sudo wget "http://pastebin.com/raw.php?i=ymiVFerb" -O /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade
``` 

make all the upgrades (If any, I guess they will be some) and then try again to install wine 
```
sudo apt-get install wine
``` 

Thanks

---

### Post by rtwaller on 2012-11-02
I don't know if it could matter or not, but I used Wubi to install Ubuntu a couple weeks ago and it had wine installed fine, but then just recently I used Wubi again to reinstall Ubuntu. I assumed it did a fresh install though?

Anyways this is what I got back. I also got frustrated and tried installing it again in the software center and I will show you the error message I got below the code.

```
rtwaller@ubuntu:~$ sudo ppa-purge ppa:jonoomph/openshot-edge
[sudo] password for rtwaller: 
Updating packages lists
PPA to be removed: jonoomph openshot-edge
Package revert list generated:
 openshot/quantal openshot-doc/quantal

Disabling jonoomph PPA from 
/etc/apt/sources.list.d/jonoomph-openshot-edge-quantal.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openshot is already the newest version.
openshot-doc is already the newest version.
Selected version '1.4.3-1' (Ubuntu:12.10/quantal [all]) for 'openshot'
Selected version '1.4.3-1' (Ubuntu:12.10/quantal [all]) for 'openshot-doc'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
rtwaller@ubuntu:~$ sudo ppa-purge ppa:pidgin-developers/ppa
Updating packages lists
PPA to be removed: pidgin-developers ppa
Package revert list generated:
 libpurple0/quantal libpurple-bin/quantal pidgin/quantal pidgin-data/quantal 
pidgin-ppa/quantal

Disabling pidgin-developers PPA from /etc/apt/sources.list.d/pidgin-ppa.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'quantal' for 'pidgin-ppa' was not found
Unable to find an archive "quantal" for the package "pidgin-ppa"
Unable to find an archive "quantal" for the package "pidgin-ppa"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
PPA purged successfully using aptitude fallback
rtwaller@ubuntu:~$ sudo rm /etc/apt/sources.list.d/*.list 
rtwaller@ubuntu:~$ sudo wget "http://pastebin.com/raw.php?i=ymiVFerb" -O /etc/apt/sources.list 
--2012-11-02 13:26:24--  http://pastebin.com/raw.php?i=ymiVFerb
Resolving pastebin.com (pastebin.com)... 66.252.2.46
Connecting to pastebin.com (pastebin.com)|66.252.2.46|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/etc/apt/sources.list'

    [ <=>                                   ] 595         --.-K/s   in 0s      

2012-11-02 13:26:24 (34.6 MB/s) - `/etc/apt/sources.list' saved [595]

rtwaller@ubuntu:~$ sudo apt-get update 
Ign http://us.archive.ubuntu.com quantal InRelease
Ign http://us.archive.ubuntu.com quantal-security InRelease                    
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Get:1 http://us.archive.ubuntu.com quantal Release.gpg [933 B]
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://archive.canonical.com quantal InRelease
Get:2 http://us.archive.ubuntu.com quantal-security Release.gpg [933 B]
Get:3 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Get:4 http://us.archive.ubuntu.com quantal-backports Release.gpg [933 B]       
Get:5 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Get:6 http://archive.canonical.com quantal Release.gpg [933 B]                 
Get:7 http://us.archive.ubuntu.com quantal Release [49.6 kB]                   
Get:8 http://extras.ubuntu.com quantal Release [11.9 kB]                      
Get:9 http://archive.canonical.com quantal Release [7,078 B]                   
Get:10 http://us.archive.ubuntu.com quantal-security Release [49.6 kB]         
Get:11 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]          
Get:12 http://us.archive.ubuntu.com quantal-backports Release [49.6 kB]        
Get:13 http://us.archive.ubuntu.com quantal/main amd64 Packages [1,137 kB]     
Get:14 http://archive.canonical.com quantal/partner amd64 Packages [2,981 B]   
Get:15 http://extras.ubuntu.com quantal/main amd64 Packages [745 B]            
Get:16 http://us.archive.ubuntu.com quantal/restricted amd64 Packages [8,369 B]
Get:17 http://us.archive.ubuntu.com quantal/universe amd64 Packages [5,274 kB] 
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://archive.canonical.com quantal/partner Translation-en
Get:18 http://us.archive.ubuntu.com quantal/multiverse amd64 Packages [131 kB]
Get:19 http://us.archive.ubuntu.com quantal/main Translation-en [660 kB]
Get:20 http://us.archive.ubuntu.com quantal/multiverse Translation-en [100 kB]
Get:21 http://us.archive.ubuntu.com quantal/restricted Translation-en [2,575 B]
Get:22 http://us.archive.ubuntu.com quantal/universe Translation-en [3,648 kB]
Get:23 http://us.archive.ubuntu.com quantal-security/main amd64 Packages [27.6 kB]
Get:24 http://us.archive.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Get:25 http://us.archive.ubuntu.com quantal-security/universe amd64 Packages [5,042 B]
Get:26 http://us.archive.ubuntu.com quantal-security/multiverse amd64 Packages [14 B]
Get:27 http://us.archive.ubuntu.com quantal-security/main Translation-en [10.5 kB]
Get:28 http://us.archive.ubuntu.com quantal-security/multiverse Translation-en [14 B]
Get:29 http://us.archive.ubuntu.com quantal-security/restricted Translation-en [14 B]
Get:30 http://us.archive.ubuntu.com quantal-security/universe Translation-en [3,150 B]
Get:31 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [46.7 kB]
Get:32 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [14 B]
Get:33 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [19.9 kB]
Get:34 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [14 B]
Get:35 http://us.archive.ubuntu.com quantal-updates/main Translation-en [21.5 kB]
Get:36 http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en [14 B]
Get:37 http://us.archive.ubuntu.com quantal-updates/restricted Translation-en [14 B]
Get:38 http://us.archive.ubuntu.com quantal-updates/universe Translation-en [10.3 kB]
Get:39 http://us.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]
Get:40 http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:41 http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages [1,066 B]
Get:42 http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [14 B]
Get:43 http://us.archive.ubuntu.com quantal-backports/main Translation-en [14 B]
Get:44 http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en [14 B]
Get:45 http://us.archive.ubuntu.com quantal-backports/restricted Translation-en [14 B]
Get:46 http://us.archive.ubuntu.com quantal-backports/universe Translation-en [1,265 B]
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://us.archive.ubuntu.com quantal-security/main Translation-en_US       
Ign http://us.archive.ubuntu.com quantal-security/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com quantal-security/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com quantal-security/universe Translation-en_US   
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US  
Fetched 11.3 MB in 24s (462 kB/s)                                              
Reading package lists... Done
rtwaller@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rtwaller@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
rtwaller@ubuntu:~$ 

```

> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed


---

### Post by philinux on 2012-11-02
Wubi is just meant to trial ubuntu not for a permanent install.

I would consider dual booting as you could spend ages getting wine plus apps to work and just be wasting your time.

See limitations. [http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)

From the developer > Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

### Post by NikTh on 2012-11-02
I don't know if Wubi have something to do with your problem , but if you had said that (wubi) from the start I would not answer at all. I cannot handle Wubi installations , they are virtual installations and I never used wubi and I really don't know how this installation ... behaves. (I only know that wubi is for testing Ubuntu)

Please consider to do a regular dual boot (alongside Windows) . It is very-very faster and more-more reliable (in my opinion).

Thanks

---

### Post by rtwaller on 2012-11-02
Thanks everyone for the replies. I had no clue that a wubi install was so much different. I just assumed it was another method of getting the OS.

Sorry for the confusion and thanks for the help.

---

