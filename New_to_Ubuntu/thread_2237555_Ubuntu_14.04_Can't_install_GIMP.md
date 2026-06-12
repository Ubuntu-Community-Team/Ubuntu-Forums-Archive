---
title: "Ubuntu 14.04: Can't install GIMP"
date: 2014-08-02
forum: New to Ubuntu
---

### Post by tn88test on 2014-08-02
I tried to install gimp on Ubuntu Software Center, but it always gave me this error.

[B]Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/B]

[B]The following packages have unmet dependencies:

gimp: Depends: libgdk-pixbuf2.0-0 (>= 2.24.1) but 2.30.7-0ubuntu1 is to be installed
      Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed
      Depends: libfontconfig1 (>= 2.9.0) but 2.11.0-0ubuntu4.1 is to be installed
      Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
      Depends: libgs9 (>= 8.61.dfsg.1) but 9.10~dfsg-0ubuntu10.2 is to be installed
      Depends: libgtk2.0-0 (>= 2.24.10) but 2.24.23-0ubuntu1.1 is to be installed
      Depends: libgudev-1.0-0 (>= 146) but 1:204-5ubuntu20.3 is to be installed
      Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed
      Depends: libtiff5 (>= 4.0.3) but 4.0.3-7ubuntu0.1 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
      Depends: python:any (>= 2.7.1-0ubuntu2) but it is a virtual package[/B]

---

### Post by mooreted on 2014-08-02
Open a terminal and post the output of the following command:

cat /etc/apt/sources.list

---

### Post by tn88test on 2014-08-02
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty main restricted
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates main restricted
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty universe
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty universe
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates universe
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty multiverse
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty multiverse
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates multiverse
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-backports main restricted universe multiverse
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-backports main restricted universe multiverse

deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security main restricted
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security main restricted
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security universe
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security universe
deb [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security multiverse
deb-src [http://mirrors.digipower.vn/ubuntu/archive/](http://mirrors.digipower.vn/ubuntu/archive/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

---

### Post by grier-devon on 2014-08-02
Not sure if this will work but anytime I cannot install an app because of unmet dependencies I just run
```
sudo apt-get install -f
```
Then the world is right again.

---

### Post by tn88test on 2014-08-02
> **grier-devon said:**
> Not sure if this will work but anytime I cannot install an app because of unmet dependencies I just run
```
sudo apt-get install -f
```
Then the world is right again.

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

I still can not install GIMP :sad:

---

### Post by tn88test on 2014-08-02
I also tried this command (found on the askubuntu).

```
sudo apt-get install gimp
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgegl-0.2-0 (>= 0.2.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by sandyd on 2014-08-02
> **tn88test said:**
> I also tried this command (found on the askubuntu).

```
sudo apt-get install gimp
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgegl-0.2-0 (>= 0.2.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Few things to check 

1. Have you tried switching mirrors in software sources? (Ubuntu Software Center)
2. Post the output of
```

sudo apt-get install libgegl-0.2-0 gimp
```

---

### Post by s-l-425434 on 2014-08-02
If you have gedit, disregard first step.

1
```
sudo apt-get install gedit
```

2. 
```
gksudo gedit /etc/apt/preferences 
```

a sheet will open. add these lines.

Package: *
Pin: release a=oneiric*
Pin-Priority: 1001


Substitute the * with the package you want, in this case gimp.

Then run ```
sudo apt-get install gimp
```

If gimp still doesn´t run go to synaptics package manager, search for libgegl-0.2-0 install the packages that show up, if not any, search for ibgegl-0.0 and install those packages. 

Fire up gimp again.

Edit: You might want to do this as root. 
just type ```
sudo -s
``` as the first thing in your terminal.

---

### Post by tn88test on 2014-08-02
Thank you all! The problem is soved after switching mirrors to the main server. :p

---

