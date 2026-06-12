---
title: "unmet dependencies on libgbm1 and xorg - Ubuntu 16.04.3 LTS"
date: 2018-03-04
forum: New to Ubuntu
---

### Post by lpc2018 on 2018-03-04
unmet dependencies on libgbm1 and xorg - Ubuntu 16.04.3 LTS


Hello Everyone, 


Looking for some help with this;


A couple of days ago I was trying to fix a VM Workstation issue affecting my ability to go full screen by upgrading my video drivers or so I thought and now I keep getting the following unmet dependencies.  I've tried various commands that others have used to solve this issues but none seem to work.  Below I'm including the dependency error message as well as a list of most of the commands I've used as I tried to solve this issue.   


:~$ uname -r    4.10.0-38-generic
:~$   lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial




The following packages have unmet dependencies:


libegl1-mesa: Depends: libgbm1 (>= 17.4~git1801031930.ad2187~oibaf~x) but 17.4~git1801031930.ad2187~oibaf~x is installed
              Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-2ubuntu4.1 is installed
              Depends: libgl1-mesa-dri (= 17.4~git1801031930.ad2187~oibaf~x) but it is not installed
libgbm1: Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-2ubuntu4.1 is installed
         Depends: libgl1-mesa-dri (= 17.4~git1801031930.ad2187~oibaf~x) but it is not installed
libgl1-mesa-glx: Depends: libglapi-mesa (= 17.4~git1801031930.ad2187~oibaf~x) but 17.4~git1801031930.ad2187~oibaf~x is installed
                 Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.6.3-1ubuntu2 is installed
                 Depends: libxdamage1 (>= 1:1.1) but 1:1.1.4-2 is installed
                 Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-2ubuntu4.1 is installed
                 Depends: libgl1-mesa-dri (>= 7.2) but it is not installed
xorg: Depends: xserver-xorg (>= 1:7.7+13ubuntu3) but it is not installed
      Depends: libgl1-mesa-dri but it is not installed


Commands Used:


sudo dpkg --force-depends --purge libgl1-mesa-dri


sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade




sudo apt-get remove libgl1-mesa-dri
sudo apt-get -f install


sudo apt-get autoclean
sudo apt-get clean


sudo dpkg -configure -a


sudo apt-get --purge autoremove
sudo apt-get --purge remove


sudo apt-get remove libdrm-amdgpu1


sudo apt-get install --fix-broken


sudo apt-get ppa-purge ppa:oibaf/graphics-drivers


sudo apt-get update




sudo add-apt-repository ppa:oibaf/graphics-drivers

---

### Post by monkeybrain20122 on 2018-03-04
You have installed some components from the oibaf ppa and then later disabled it, but the versions have been bumped so the standard packages are not compatible. So either reactivate oibaf, sudo apt update and install what you need and get a higher version, or use ppa-purge to purge the oibaf ppa (need to reactivate oibaf first for ppa-purge to work) and downgrade the packages you installed from there consistently. 

Sudo apt-get -f should be avoided as you would be left with a broken system if the underlying causes are not addressed.

---

### Post by lpc2018 on 2018-03-04
Thank you for the prompt response.  Considering I'm not running an AMD graphics card, how do you recommend I approach this issue.  Your probably wondering why I was trying to install and AMD driver in the first place...lets just say it was late at night and I forgot what laptop I was using. 

Vendor ID:             GenuineIntel
Model name:            Intel(R) Core(TM)
description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation

---

### Post by monkeybrain20122 on 2018-03-04
So I take it that I was correct that you have installed from oibaf's ppa at one point and then disabled it? If that is the case read on.

Well oibaf does provide bleeding edge mesa packages which are used by  intel cards, the catch is that these are betas and a bit unstable (a  better option IMO is [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa) if you need more up to date mesa than Ubuntu's official repository provides)

 If you don't want oibaf anymore, then use ppa-purge to consistently downgrade the  packages you installed from there. First reactivate oibaf from your  sources list (easy way: in the dash search software, then choose  software update & install > Other software and check the box for  oibaf and then reload, close) Install ppa-purge

```
sudo apt install ppa-purge
```

Now purge oibaf and downgrade the packages you have installed

```
sudo ppa-purge ppa:oibaf/graphics-drivers
```

and follow the prompt.

---

### Post by cntrl on 2018-03-04
I applied purge functions losing the desktop control for terminal and applications, just basic functions since terminal commands and continuous fetch 404 error related to i386 and  sources.list not found

Finally I solved yesterday 03.03.18 downloading and installing libglib2.0-tests_2.48.0-1ubuntu4_i386.deb; this package contains all required repositories to run ubuntu 16.04 for 32 bits as just installed

sudo dpkg -i libglib2.0-tests_2.48.0-1ubuntu4_i386.deb 

after input your key and installed

sudo apt-get update 

and later

sudo apt-get upgrade

later restart you computer

---

