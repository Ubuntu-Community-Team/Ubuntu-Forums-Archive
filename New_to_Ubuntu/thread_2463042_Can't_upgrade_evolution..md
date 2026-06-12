---
title: "Can't upgrade evolution."
date: 2021-06-02
forum: New to Ubuntu
---

### Post by maketopsite on 2021-06-02
Ubuntu 20.04 LTS

```

apt upgrade
Hit http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease
Hit http://at.archive.ubuntu.com/ubuntu focal InRelease                    
Hit http://at.archive.ubuntu.com/ubuntu focal-updates InRelease                                     
Hit http://at.archive.ubuntu.com/ubuntu focal-backports InRelease                                   
Hit http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease      
Hit http://security.ubuntu.com/ubuntu focal-security InRelease
                                         
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
The following packages will be upgraded: 
  evolution{b} evolution-common evolution-ews{b} evolution-plugin-bogofilter{b} 
  evolution-plugin-pstimport{b} evolution-plugins{b} libevolution{b} 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4&#8239;161 kB of archives. After unpacking 73,7 kB will be freed.
The following packages have unmet dependencies:
 evolution-ews : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libebackend-1.2-10 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libebook-1.2-20 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libecal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libedata-book-1.2-26 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libedata-cal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                 Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
 evolution-plugin-bogofilter : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                               Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
 evolution-plugin-pstimport : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                              Depends: libebook-1.2-20 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                              Depends: libecal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                              Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
 evolution-plugins : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                     Depends: libebook-1.2-20 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                     Depends: libecal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                     Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
 libevolution : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                Depends: libebook-1.2-20 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                Depends: libecal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
                Depends: libedataserverui-1.2-2 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
 evolution : Depends: libcamel-1.2-62 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
             Depends: libecal-2.0-1 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
             Depends: libedataserver-1.2-24 (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
             Depends: evolution-data-server (>= 3.36.5) but 3.36.4-0ubuntu1 is installed
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     evolution [3.36.4-0ubuntu1 (now)]                  
2)     evolution-common [3.36.4-0ubuntu1 (now)]           
3)     evolution-ews [3.36.4-0ubuntu1 (now)]              
4)     evolution-plugin-bogofilter [3.36.4-0ubuntu1 (now)]
5)     evolution-plugin-pstimport [3.36.4-0ubuntu1 (now)] 
6)     evolution-plugins [3.36.4-0ubuntu1 (now)]          
7)     libevolution [3.36.4-0ubuntu1 (now)]               



Accept this solution? [Y/n/q/?] 

```

What is please optimal solution ?

---

### Post by Impavidus on 2021-06-02
It appears your evolution doesn't come from the official repositories. Where did you get it?

---

### Post by maketopsite on 2021-06-02
> **Impavidus said:**
> It appears your evolution doesn't come from the official repositories. Where did you get it?

looks like from ubuntu-mate-desktop
```
apt info evolution
Package: evolution
Version: 3.36.5-0ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 456 kB
Provides: imap-client, mail-reader
Depends: libc6 (>= 2.14), libcamel-1.2-62 (>= 3.36.5), libclutter-gtk-1.0-0 (>= 0.91.8), libecal-2.0-1 (>= 3.36.5), libedataserver-1.2-24 (>= 3.36.5), libevolution (>= 3.36.5), libevolution (<< 3.37), libglib2.0-0 (>= 2.46.0), libgtk-3-0 (>= 3.0.0), libical3 (>= 3.0.0), libnotify4 (>= 0.7.0), libsoup2.4-1 (>= 2.42), libwebkit2gtk-4.0-37 (>= 2.24), libxml2 (>= 2.7.4), evolution-common (= 3.36.5-0ubuntu1), evolution-data-server (>= 3.36.5), evolution-data-server (<< 3.37), dbus, psmisc
Recommends: evolution-plugins, evolution-plugin-bogofilter | evolution-plugin-spamassassin, evolution-plugin-pstimport, yelp
Suggests: evolution-ews, evolution-plugins-experimental, gnupg, network-manager
Breaks: evolution-common (<< 3.20.4-1~)
Replaces: evolution-common (<< 3.20.4-1~)
Homepage: https://wiki.gnome.org/Apps/Evolution
Task: **ubuntu-mate-desktop**


```

---

### Post by &amp;KyT$0P# on 2021-06-02
> **Impavidus said:**
> It appears your evolution doesn't come from the official repositories. Where did you get it?

To answer this question, please post the output from running this command in Terminal -
```
apt-cache policy evolution evolution-ews
```

---

### Post by maketopsite on 2021-06-02
> **halogen2 said:**
> To answer this question, please post the output from running this command in Terminal -
```
apt-cache policy evolution evolution-ews
```

```
apt-cache policy evolution evolution-ews
evolution:
  Installed: 3.36.4-0ubuntu1
  Candidate: 3.36.5-0ubuntu1
  Version table:
     3.36.5-0ubuntu1 500
        500 http://at.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
 *** 3.36.4-0ubuntu1 100
        100 /var/lib/dpkg/status
     3.36.1-2 500
        500 http://at.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
evolution-ews:
  Installed: 3.36.4-0ubuntu1
  Candidate: 3.36.5-0ubuntu1
  Version table:
     3.36.5-0ubuntu1 500
        500 http://at.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
 *** 3.36.4-0ubuntu1 100
        100 /var/lib/dpkg/status
     3.36.1-1 500
        500 http://at.archive.ubuntu.com/ubuntu focal/universe amd64 Packages


```

---

### Post by &amp;KyT$0P# on 2021-06-02
Looks like your Evolution actually is from the official repositories.

Please run this command in Terminal -
```
sudo apt-get update
```

If the issue still persists after that: for troubleshooting, please post the output from both the above command and from the following command -
```
apt-get -s --reinstall install libcamel-1.2-62
```
(This one is only a simulation, it won't actually change anything.)

---

### Post by maketopsite on 2021-06-02
> **halogen2 said:**
> Looks like your Evolution actually is from the official repositories.

Please run this command in Terminal -
```
sudo apt-get update
```

If the issue still persists after that: for troubleshooting, please post the output from both the above command and from the following command -
```
apt-get -s --reinstall install libcamel-1.2-62
```
(This one is only a simulation, it won't actually change anything.)

```
apt-get update
Hit:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease
Hit:2 http://at.archive.ubuntu.com/ubuntu focal InRelease                  
Hit:3 http://at.archive.ubuntu.com/ubuntu focal-updates InRelease                                                           
Hit:4 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease                                                     
Hit:5 http://at.archive.ubuntu.com/ubuntu focal-backports InRelease        
Get:6 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:7 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24,5 kB]
Get:8 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [7&#8239;760 B]
Get:9 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [58,3 kB]
Get:10 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Fetched 207 kB in 1s (139 kB/s)                                                 
Reading package lists... Done


```

```
apt-get -s --reinstall install libcamel-1.2-62
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Inst libcamel-1.2-62 [3.36.4-0ubuntu1] (3.36.4-0ubuntu1 Ubuntu:20.04/focal-updates [amd64])
Conf libcamel-1.2-62 (3.36.4-0ubuntu1 Ubuntu:20.04/focal-updates [amd64])


```

---

### Post by &amp;KyT$0P# on 2021-06-02
Thanks.  Now can you please post the output from running this -
```
for i in /etc/apt/sources.list /etc/apt/sources.list.d/*.list;do echo "*** $i ***"; cat "$i";echo;done
```

and this -
```
apt-cache policy
```

---

### Post by maketopsite on 2021-06-02
> **halogen2 said:**
> Thanks.  Now can you please post the output from running this -
```
for i in /etc/apt/sources.list /etc/apt/sources.list.d/*.list;do echo "*** $i ***"; cat "$i";echo;done
```

and this -
```
apt-cache policy
```

You are welcome.

```
for i in /etc/apt/sources.list /etc/apt/sources.list.d/*.list;do echo "*** $i ***"; cat "$i";echo;done
*** /etc/apt/sources.list ***
# deb http://at.archive.ubuntu.com/ubuntu/ focal main restricted

# deb http://at.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb http://security.ubuntu.com/ubuntu focal-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://at.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://at.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal universe
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://at.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://at.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

*** /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-focal.list ***
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal main

*** /etc/apt/sources.list.d/slimbook-ubuntu-slimbook-focal.list ***
deb http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal main
# deb-src http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal main
```

```
apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-slimbook-slimbook,a=focal,n=focal,l=slimbook,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-slimbook-slimbook,a=focal,n=focal,l=slimbook,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-graphics-drivers,a=focal,n=focal,l=Proprietary GPU Drivers,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-graphics-drivers,a=focal,n=focal,l=Proprietary GPU Drivers,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://security.ubuntu.com/ubuntu focal-security/multiverse i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=multiverse,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=multiverse,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/restricted i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=restricted,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=restricted,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=amd64
     origin security.ubuntu.com
 100 http://at.archive.ubuntu.com/ubuntu focal-backports/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-backports,n=focal,l=Ubuntu,c=universe,b=i386
     origin at.archive.ubuntu.com
 100 http://at.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-backports,n=focal,l=Ubuntu,c=universe,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/multiverse i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=multiverse,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=multiverse,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/restricted i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=restricted,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=restricted,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/multiverse i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=multiverse,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=multiverse,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/restricted i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=restricted,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/restricted amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=restricted,b=amd64
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=i386
     origin at.archive.ubuntu.com
 500 http://at.archive.ubuntu.com/ubuntu focal/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=amd64
     origin at.archive.ubuntu.com
Pinned packages:


```

---

### Post by &amp;KyT$0P# on 2021-06-02
I don't see any problems in those outputs.  I suggest you wait until tomorrow, then re-run [FONT=Courier New]sudo apt-get update[/FONT] and try again.  If the issue is not resolved at that point, next thing to try would be opening Software & Updates settings, Ubuntu Software tab, change "Download from:" to a different mirror.

---

### Post by maketopsite on 2021-06-04
> **halogen2 said:**
> I don't see any problems in those outputs.  I suggest you wait until tomorrow, then re-run [FONT=Courier New]sudo apt-get update[/FONT] and try again.  If the issue is not resolved at that point, next thing to try would be opening Software & Updates settings, Ubuntu Software tab, change "Download from:" to a different mirror.

it's solved, thank you.

---

