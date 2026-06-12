---
title: "upgrading to ubuntu 11.10 beta"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andrewdonshik on 2011-09-03
I try it using update-manager -d, but I always get an error after it is done downloading packages

---

### Post by howefield on 2011-09-03
Thread moved to "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by andrewdonshik on 2011-09-03
A reply would be nice.

---

### Post by coffeecat on 2011-09-03
.... and patience is a virtue. It's been only about half-an-hour since you started the thread.

What error do you get? Post the exact error otherwise it is impossible to help.

---

### Post by andrewdonshik on 2011-09-03
Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

---

### Post by coffeecat on 2011-09-03
Question: what were you trying to upgrade from? If you were upgrading from Natty/11.04 then "sudo update-manager -d" would be correct. But if you had an Oneiric system installed when it was in alpha, a simple upgrade via Synaptic or apt-get takes you into Beta.

What output did you get when the system ran dpkg --configure -a? Is the system still usable?

---

### Post by andrewdonshik on 2011-09-03
I got no output from sudo dpkg --reconfigure -a. The system is still usable. I am on ubuntu 11.04

---

### Post by coffeecat on 2011-09-03
Puzzling. You were doing the right thing:

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1)

That's a bit out-of-date, referring to alpha1, but it's still valid now that we are in beta1.

Post the output of these two commmands:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/

```

You can highlight the terminal output with the mouse, right-click -> copy and then paste into your post. Please post that between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by andrewdonshik on 2011-09-03
```
 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

```

```

askubuntu-tools-ppa-natty.list
askubuntu-tools-ppa-natty.list.save
awn-testing-ppa-natty.list
awn-testing-ppa-natty.list.distUpgrade
awn-testing-ppa-natty.list.save
caffeine-developers-ppa-natty.list
caffeine-developers-ppa-natty.list.distUpgrade
caffeine-developers-ppa-natty.list.save
caffine-developers-ppa-natty.list
caffine-developers-ppa-natty.list.save
danielrichter2007-grub-customizer-natty.list
danielrichter2007-grub-customizer-natty.list.distUpgrade
danielrichter2007-grub-customizer-natty.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
getdeb.list
getdeb.list.distUpgrade
getdeb.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-earth.list
google-earth.list.distUpgrade
google-earth.list.save
lightdm-team-ppa-natty.list
lightdm-team-ppa-natty.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
--natty.list
--natty.list.save
natty-partner.list
natty-partner.list.distUpgrade
natty-partner.list.save
opera.list
opera.list.save
pidgin-developers-ppa-natty.list
pidgin-developers-ppa-natty.list.distUpgrade
pidgin-developers-ppa-natty.list.save
pidgin-ppa.list
pidgin-ppa.list.distUpgrade
pidgin-ppa.list.save
ppa_launchpad_net-sevenmachines-natty.list
ppa_launchpad_net-sevenmachines-natty.list.save
rye-ubuntuone-extras-natty.list
rye-ubuntuone-extras-natty.list.distUpgrade
rye-ubuntuone-extras-natty.list.save
sevenmachines-flash-natty.list.save
skype.list
skype.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.distUpgrade
tiheum-equinox-natty.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
ubuntu-tweak-stable.list.save
virtualbox-offical-source.list
virtualbox-offical-source.list.distUpgrade
virtualbox-offical-source.list.save

```

---

### Post by coffeecat on 2011-09-03
Your main sources.list file look OK - all the functional lines have been updated to the oneiric repository. A side comment first. I see that your system started life as Maverick so I guess it's your main system. It's generally recommended not to upgrade your main working system to the latest version until it's released. Even in Beta, it can be unstable. The usual recommendation is to run the pre-release testing version on a spare machine, or a spare hard drive, or at least on a spare partition. This is what I do - my testing systems are entirely disposable so it doesn't matter if they break badly. Anyway, it's probably a bit late now, but something to think about for the future.

But on to the contents of your /etc/apt/sources.list.d/ folder. You have a lot of source lists for 3rd-party and PPA repos there. When you do an update-manager -d, they *should* be disabled. But I wonder if one or more have not been and 3rd party repos are interfering with the upgrade process. Although I would have thought you'd get a more verbose error if that were the case.

Whatever... you need to check whether all those 3rd party repos are disabled. You can either open each *.list file in the /etc/apt/sources.list.d/ folder and ensure all the lines are commented; or, open Synaptic -> Settings menu -> Repositories -> Other Software tab and check that all the 3rd party repos are unticked.

---

### Post by andrewdonshik on 2011-09-03
will do when I get home tomorrow

---

### Post by andrewdonshik on 2011-09-03
Reason it had maverick sources is I couldn't get 11.04 to install without a bootloader error, so i installed 10.10 and upgraded.

---

### Post by andrewdonshik on 2011-09-04
Actually dpkg said that it couldnt reconfigure something, so installed it.

---

### Post by arm-c on 2011-09-04
I had a similar problem yesterday.  

When I ran the dpkg --configure -a, I saw the upgrade was unable to install the meta package  "ubuntu-desktop".

Using synaptic, I saw that the packages it conflicted with were preventing a newer package from installing.  I had to remove two programs I had installed... and then install the meta package "ubuntu-desktop"

Conflicting packages preventing the smooth upgrade:  gok and dasher (both input tools).

Hope that helps.

v/r
ARM-C

---

### Post by zaphod777 on 2011-09-14
This is what fixed it for me 

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/846743](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/846743)

---

### Post by kevpatts on 2011-09-16
This worked for me also:
```
sudo apt-get install python-pyatspi2
```

---

### Post by samjam86 on 2011-09-17
Worked for me too!

---

### Post by another_sam on 2011-09-18
Me too.

---

