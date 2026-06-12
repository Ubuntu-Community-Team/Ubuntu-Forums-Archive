---
title: "Which is the easiest to start with?"
date: 2008-02-26
forum: Recurring Discussions
---

### Post by Konnerr on 2008-02-26
I dont know which is easier to use.im tyring Ubuntu. which is the easiest to use

---

### Post by amingv on 2008-02-26
Is this a paradox/contradiction? :) Ok, I'll give it a try...

In my experience, they're all quite easy (I prefer Kubuntu (KDE) myself); buy you might like to stick to Ubuntu (Gnome). Since most people in the forums use that it will be easier to give you support (should you need it).

---

### Post by herbster on 2008-02-26
If you're coming straight from Windows, regular Ubuntu will most likely work for you. Kubuntu can be a good choice, too, though the myriad of settings may explode your noggin.

---

### Post by Pogeymanz on 2008-02-26
I agree with Herbster. KDE might have too many menu options. I still prefer Gnome or XFCE to KDE because the menus feel cluttered.

ubuntu will be easiest because more people use it and can give you very specific help.

---

### Post by zvacet on 2008-02-26
Start with Ubuntu,and if you don´t like it or you want to try Kubuntu,Xubuntu you can do it anytime.

---

### Post by Konnerr on 2008-02-26
Hmm i think ill download Kubuntu and Xubuntu for the heck of it. thanks for help =]

---

### Post by DrMega on 2008-02-26
It is a matter of personal taste.

I like the default Gnome desktop (Ubuntu). However I've tried Xubuntu and Kubuntu too. Xubuntu looks like simplified Gnome, and Kubuntu looks a bit like Windows XP to me.

EDIT: Try them all. Just install Ubuntu, then install the kubuntu-desktop and xubuntu-desktop over the top (from Synaptic). You can then switch between the three without having three separate installs.

---

### Post by Konnerr on 2008-02-26
Ill try Kubuntu. i had CDs of another version but i broke them because i never tried dual booting. because i do like windows XP =]

---

### Post by Oldsoldier2003 on 2008-02-26
> **Konnerr said:**
> Hmm i think ill download Kubuntu and Xubuntu for the heck of it. thanks for help =]

Just download one... say if you try ubuntu and want to use xubuntu all it takes is "sudo apt-get Xubuntu-desktop" no need to have cds for all flavors :)

---

### Post by Sef on 2008-02-26
Moved to Recurring Discussions.

---

### Post by Konnerr on 2008-02-26
Ok i cannot figure out how to get the kubuntu-desktop with sudo

help?

---

### Post by aysiu on 2008-02-26
> **Konnerr said:**
> Ok i cannot figure out how to get the kubuntu-desktop with sudo

help?
Read [this guide](http://www.psychocats.net/ubuntu/kde).

---

### Post by Konnerr on 2008-02-26
That didnt work
i get this

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by aysiu on 2008-02-26
Why do you have a mix of Feisty and Gutsy repositories? That's not good.

What version of Ubuntu are you using--7.04 or 7.10? Let us know, and then we can try to get you a normal sources.list.

---

### Post by Konnerr on 2008-02-26
i have 7.10

---

### Post by gletob on 2008-02-26
please post the contents of your /etc/apt/sources.list

just type in the terminal sudo gedit /etc/apt/sources.list and copy & paste it into a new post

---

### Post by Konnerr on 2008-02-26
heres what i have in my sources list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe/etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

---

### Post by gletob on 2008-02-26
ok please run these commands in this order
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo gedit /etc/apt/sources.list
```

copy and past this code to your sources.list then save and close
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe/etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

then run these two commands
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

then finally install kubuntu
```
sudo apt-get install kubuntu-desktop
```

---

### Post by aysiu on 2008-02-26
So basically you have the Ubuntu 7.10 desktop CD, which has almost nothing in it, and then a special set of Ubuntu 7.04 repositories that also have almost nothing in them.

You still haven't answered the question, though: are you using Ubuntu 7.10 or Ubuntu 7.04?

---

### Post by gletob on 2008-02-26
> **aysiu said:**
> So basically you have the Ubuntu 7.10 desktop CD, which has almost nothing in it, and then a special set of Ubuntu 7.04 repositories that also have almost nothing in them.

You still haven't answered the question, though: are you using Ubuntu 7.10 or Ubuntu 7.04?

He has stated he running 7.10,  his gutsy repos are commented out, and the CD repo is a gutsy disc
this all leads me to believe he is running gutsy and an installer problem commented out his repositories.

---

### Post by Konnerr on 2008-02-26
yes im using Ubuntu 7.10 Gusty Gibbon

---

### Post by matherians2 on 2008-02-26
I've tried Edubuntu and Ubuntu.  It seems like there was more stuff with Ubuntu.  Also, it was easier to configure.

---

### Post by gletob on 2008-02-26
did you follow my insturctions on page 2 ?

---

### Post by Konnerr on 2008-02-26
Yes i did. its setting up all that stuff now.:guitar:

---

### Post by gletob on 2008-02-26
kool :guitar:
P.S. Did you have a lot of gutsy updates to install ?
P.P.S. I voted for ubuntu for usability and support

---

### Post by Konnerr on 2008-02-26
oh yes. lots of gusty updates. i mean LOTS of them. now im doing the kubuntu-desktop one. its working now thanks for the help. =]

If anyone wants to talk to me through MSN add me [email]soulcaliber920@hotmail.com[/email]


and again thanks to all that helped..

---

### Post by gletob on 2008-02-26
ewww MicroSoft Network Instant Messenger
No Thanks

---

### Post by karthick87 on 2010-02-14
I think Ubuntu..

---

### Post by blueshiftoverwatch on 2010-02-15
[img]http://i25.photobucket.com/albums/c63/Reyalskrad/raise_thread.jpg[/img]

---

