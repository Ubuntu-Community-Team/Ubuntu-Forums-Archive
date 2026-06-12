---
title: "can't add any new programs.."
date: 2012-05-14
forum: New to Ubuntu
---

### Post by scottr99 on 2012-05-14
Hi, wasn't sure where to put this, so...

I installed recently Ubuntu 12-.  When I try to download, or install, a new program to it -- for example Google Chrome -- a window pops up with the header: Ubuntu Software Center.  Then I get a box that states: System program problem detected; and then another box: Crash Report with the following text: could not determine the package or source package name.

It doesn't install anything after I cancel all of these boxes.

Any ideas?

Thanks!

---

### Post by sudodus on 2012-05-14
You have found a bug, that will probably be fixed soon. But there are other ways to install programs. If you want to go the GUI way, use ***Synaptic***, otherwise use apt-get from a terminal window. For example, to install ***htop***, type
```
sudo apt-get install htop
```
or
```
sudo apt-get install chromium-browser
``` which is the free version of Chrome.

---

### Post by bruno9779 on 2012-05-14
There are several ways to install programs in ubuntu, direct download being the least common.

In your case, try and open the Ubuntu software center and install something from there to see if it works properly.

then download the desired program again, but save it to disk.
Go to terminal and navigate to the destination folder.
Now type:

```
sudo dpkg -i programname.deb
```

and post back eventual errors

---

### Post by scottr99 on 2012-05-14
> **sudodus said:**
> You have found a bug, that will probably be fixed soon. But there are other ways to install programs. If you want to go the GUI way, use ***Synaptic***, otherwise use apt-get from a terminal window. For example, to install ***htop***, type
```
sudo apt-get install htop
```

Hi, thanks!  I am familiar with the terminal approach, but would you mind telling me more about the Synaptic approach pls.  Is that a GUI, program, needed to be downloaded?

Actually, just tried the following and got the following:

scottr99@scottr99-HP-Pavilion-dm4-Notebook-PC:~$ sudo apt-get install synaptic
[sudo] password for scottr99: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

---

### Post by scottr99 on 2012-05-14
Actually that "E:" line I get with any terminal add-apt command.

---

### Post by sudodus on 2012-05-14
> **scottr99 said:**
> Hi, thanks!  I am familiar with the terminal approach, but would you mind telling me more about the Synaptic approach pls.  Is that a GUI, program, needed to be downloaded?
I think Synaptic is included in most versions and flavours of Ubuntu. It is a GUI application, and there should be a menu entry for it (or in HUD). But you can also start it with
```
gksudo synaptic
```

---

### Post by scottr99 on 2012-05-14
> **sudodus said:**
> I think Synaptic is included in most versions and flavours of Ubuntu. It is a GUI application, and there should be a menu entry for it (or in HUD). But you can also start it with
```
gksudo synaptic
```

This comes up with nothing.

---

### Post by scottr99 on 2012-05-14
I may have been adding the following when you were responding..  so here it is again.  it appears i cannot download via term either...

scottr99@scottr99-HP-Pavilion-dm4-Notebook-PC:~$ sudo apt-get install synaptic
[sudo] password for scottr99: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

---

### Post by bruno9779 on 2012-05-14
> **scottr99 said:**
> Actually that "E:" line I get with any terminal add-apt command.

It is apt-get, not add-apt.
Still, something could be wrong with your sources.list if you can't install anything from terminal.

Please post the contents of /etc/apt/sources.list

---

### Post by cortman on 2012-05-14
If you just recently installed, have you updated the repository lists?

```
sudo apt-get update
sudo apt-get install synaptic
```

Most problems I've seen with the Ubuntu Software Center are fixed by simply reinstalling it:

```
sudo apt-get install software-center --reinstall
```

---

### Post by bruno9779 on 2012-05-14
> **sudodus said:**
> I think Synaptic is included in most versions and flavours of Ubuntu. It is a GUI application, and there should be a menu entry for it (or in HUD). But you can also start it with
```
gksudo synaptic
```

Synaptic isn't included in ubuntu by default anymore

---

### Post by scottr99 on 2012-05-14
> **bruno9779 said:**
> It is apt-get, not add-apt.
Still, something could be wrong with your sources.list if you can't install anything from terminal.

Please post the contents of /etc/apt/sources.list

Forgive me I was just being careless, I do know the correct string.  Anyways here's sources.list:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100318)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ch.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

# Gerris flow solver
   deb http://download.opensuse.org/repositories/home:/popinet/ precise
#  deb http://download.opensuse.org/repositories/home:/popinet/xUbuntu_9.10 precise

# Remastersys
deb http://www.geekconnection.org/remastersys/repository precise

deb http://www.openfoam.com/download/ubuntu precise main




# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by bruno9779 on 2012-05-14
Sources.list seems fine.

Try to follow cortman's advice and :

```
sudo apt-get update
```

---

### Post by sudodus on 2012-05-14
> **scottr99 said:**
> This comes up with nothing.
Which flavour are you running?
- 'vanilla' Ubuntu or Kubuntu, Lubuntu, Xubuntu ...

Please post your flavour of Ubuntu, it makes it easier to help :-)

You might try to clean your install setup and wait for the response between each command line.
```
sudo apt-get update
sudo apt-get upgrade
# and if problems
sudo apt-get check
sudo apt-get --fix-broken
sudo apt-get --fix-missing
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```
Also read the apt-get manual pages ```
man apt-get
```

---

### Post by oldos2er on 2012-05-14
Moved to Absolute Beginner Talk.

---

### Post by pydsigner on 2012-05-14
> **sudodus said:**
> 
- 12.04 or 12.10?

His sources would indicate 12.04.

---

