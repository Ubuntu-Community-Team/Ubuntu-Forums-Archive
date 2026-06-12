---
title: "Awn Dock workspace Switcher"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Raistlin82 on 2008-07-20
Hi all, I installed awn dock from synaptic and it seems to be working fine, but I cant figure out how to add the desktop switcher to it, can anyone help me out? :)

---

### Post by jjocsak on 2008-07-20
> **Raistlin82 said:**
> Hi all, I installed awn dock from synaptic and it seems to be working fine, but I cant figure out how to add the desktop switcher to it, can anyone help me out? :)

Try this.
[http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)


Jeff

---

### Post by Raistlin82 on 2008-07-20
not had much luck with that, when i tried to add the additional repository from reacocard to sources.list it denied me permission so i did sudo gedit and it saved.  so i carried on to the next step and typed 

$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr

into the terminal i got the message

E: Type &#8216;/etc/apt/sources.list&#8217; is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.

its probly something really simple but not having much joy figuring it out

---

### Post by jjocsak on 2008-07-20
How about, "awn-extras-applets-trunk" in synaptic manager?

Jeff

---

### Post by tjwoosta on 2008-07-20
the reason the repository you tried to add from that link wont work is probably becasue its for ubuntu gutsy

you probably need the ubuntu hardy repository

look here
[https://launchpad.net/~reacocard-awn/+archive]("https://launchpad.net/~reacocard-awn/+archive")

then after adding the repository do this

```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

here is a link to a thread i made a long time ago when trying to get the awn show desktop button 
[http://ubuntuforums.org/showthread.php?t=776240]("http://ubuntuforums.org/showthread.php?t=776240")

---

### Post by Raistlin82 on 2008-07-20
all i am getting when i try to access synaptic is the following

E: Type &#8216;/etc/apt/sources.list&#8217; is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

so i'm guessing i've done something wrong to sources list :(

i've deleted line 51 and synaptic is now working again so will have a look there!

---

### Post by tjwoosta on 2008-07-20
> all i am getting when i try to access synaptic is the following

E: Type &#8216;/etc/apt/sources.list&#8217; is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

so i'm guessing i've done something wrong to sources list

i've deleted line 51 and synaptic is now working again so will have a look there! 

open the sources.list with gedit and remove the old gutsy repository that you tried adding

if you still need help just post you sources.list and we can help you straighten it out

---

### Post by Raistlin82 on 2008-07-21
Hi guys, thanks for the help so far!  Sorry for late reply, encountered the Blue Ring of Death on my phone, so just got it sorted:mad:  Anyways....  I've got synaptic manager running fine again, but not had any luck with adding the repository :( keep getting a message saying:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

my source list is below:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

many thanks for all your help so far!

---

### Post by Raistlin82 on 2008-07-21
update - i came across [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml) which has helped quite alot.  the only part i have an issue with here is step 2.... i get the following message in terminal


No build script available.  You have two choices:
1. You need to install the gnome-common module and make
   sure the gnome-autogen.sh script is in your $PATH.
2. You need to install the following scripts:
   * intltool
   * glib-gettextize (usually installed with glib-2.0)
   * gtk-doc
   * libtool
   * automake
   * autoconf
   Additionally, you need to make
   sure that they are in your $PATH.

what should i do here??

---

### Post by Raistlin82 on 2008-07-22
bump! :-({|=

---

### Post by MedellinManDem on 2008-07-27
> **tjwoosta said:**
> the reason the repository you tried to add from that link wont work is probably becasue its for ubuntu gutsy

you probably need the ubuntu hardy repository

look here
[https://launchpad.net/~reacocard-awn/+archive]("https://launchpad.net/~reacocard-awn/+archive")

then after adding the repository do this

```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

here is a link to a thread i made a long time ago when trying to get the awn show desktop button 
[http://ubuntuforums.org/showthread.php?t=776240]("http://ubuntuforums.org/showthread.php?t=776240")

When I try and enter: 
```

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main


```

It just says
```

bash: deb: command not found
```

Any ideas why?

---

### Post by Raistlin82 on 2008-07-27
Hi there, try following the instructions i found here [http://news.softpedia.com/news/Insta...on-82611.shtml](http://news.softpedia.com/news/Insta...on-82611.shtml) I never did get the 2nd stage to work, but skipped it and went to stage 3 and everything seems to have worked fine, i've got all the applets i need and a dock that i'm now pretty happy with, would still like to know what stage 2 does tho!

---

