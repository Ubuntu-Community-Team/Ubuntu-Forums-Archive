---
title: "how to correct this error message"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-07-15
what command to run to fix. just getting old and forgot

E: Type 'main' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

tks

---

### Post by rburkartjo on 2011-07-15
here is output
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports restricted main multiverse universe
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

---

### Post by Rubi1200 on 2011-07-15
Post the output of the following please:

```
cat /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
```

---

### Post by VinDSL on 2011-07-15
> **rburkartjo said:**
> what command to run to fix. just getting old and forgot

E: Type 'main' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list

blah... blah... blah...
AFAIK, there is no such PPA, e.g. tualatrix-ppa-oneiric

Tualatrix is working in league with Canonical for inclusion in "Official" PPAs.

I don't think he's turned loose an Oneiric version.  It would be stupid if he did.

Thus changing: tualatrix-ppa-**oneiric** ->> tualatrix-ppa-**natty** should do the deed.  ;)

---

### Post by VinDSL on 2011-07-15
Okay... here you go... this works in UbuOO...  :)

```

$ cat /etc/apt/sources.list.d/tualatrix-ubuntu-natty.list
deb http://ppa.launchpad.net/tualatrix/ubuntu natty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu natty main

```

I'm assuming, you've been around the track a few times, and I don't need to spell it out for you.  ;)

---

### Post by VinDSL on 2011-07-15
Sigh...  You know... I started thinking...

Just because you know what you're doing, doesn't mean other ppl (reading this thread) know what they're doing, so...

Here's a mini HOWTO.  :D

In CLI:
```

$ sudo add-apt-repository ppa:tualatrix/ppa

```

Then:
```

$ sudo apt-get update

```

Look!  Pesky errors:
```
Fetched 13.9 MB in 35s (388 kB/s)

W: Failed to fetch
http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/**[COLOR="Red"]oneiric[/COLOR]**/main/source/Sources  404  Not Found

W: Failed to fetch
http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/**[COLOR="Red"]oneiric[/COLOR]**/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Let's be lazy now and use Synaptic ->> Settings ->> Repositories ->> Other Software

Oh, there it is:
```

Type: Binary
URL: http://ppa.launchpad.net/tualatrix/ppa/ubuntu
Distribution: **[COLOR="Red"]oneiric[/COLOR]**
Components: Main
Comments:

and...

Type: Source
URL: http://ppa.launchpad.net/tualatrix/ppa/ubuntu
Distribution: **[COLOR="Red"]oneiric[/COLOR]**
Components: Main
Comments:

```

Let's change them to:
```

Type: Binary
URL: http://ppa.launchpad.net/tualatrix/ppa/ubuntu
Distribution: **[COLOR="Red"]natty[/COLOR]**
Components: Main
Comments:

and...

Type: Source
URL: http://ppa.launchpad.net/tualatrix/ppa/ubuntu
Distribution: **[COLOR="Red"]natty[/COLOR]**
Components: Main
Comments:

```

Reload the repositories in Synaptic and close.

In CLI again...
```

$ sudo apt-get update

```

Bingo!
```

Reading package lists... Done

```

One last time:
```
$ cat /etc/apt/sources.list.d/tualatrix-ubuntu-natty.list
deb http://ppa.launchpad.net/tualatrix/ubuntu natty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu natty main

```

You're ready to rock n' roll!  ;)

---

### Post by rburkartjo on 2011-07-15
here is output

ray@ray-GC660AA-ABA-SR5123WM:~$ cat /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
# deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) oneiric main #Ubuntu Tweak Stable Source disabled on upgrade to oneiric
 main
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by rburkartjo on 2011-07-15
easy fix if someone could past their output from the 
/etc/apt/sources.list.d/
i could just delete mine and replace or am open to suggestions
unable to do what vin suggested

---

### Post by rburkartjo on 2011-07-15
yea really messed up what is new. at this stage only getting copy of etc file and replacing is probably only answer. note: i looked on internet and was unable to find an output etc file for 11.10a2 on the net.

---

### Post by dino99 on 2011-07-15
i suppose you know about synaptic repo tab, right ?

---

### Post by rburkartjo on 2011-07-15
dino when i try to do that spm crashes so unless you have a better idea let me know. i know that if i replace the /etc it will work done it before

---

### Post by dino99 on 2011-07-15
sudo gedit /etc/apt/sources.list

---

### Post by mc4man on 2011-07-15
Post 5 showed you what the .list file should look like
Or just delete tualatrix-ppa-oneiric.list and tualatrix-ppa-oneiric.save if it exists

---

### Post by rburkartjo on 2011-07-15
dino yes but all i get when i open spm is this error message 

E: Type 'main' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and cant access the repo tab
tried to click on the error message and then spm crashes
and if dont click on i have no access to the repo tab

---

### Post by rburkartjo on 2011-07-15
also tried this but of course didnt work


ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for ray: 
E: Type 'main' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
E: The list of sources could not be read.
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by rburkartjo on 2011-07-15
i need something like this for 11.10a2

[http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/](http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/)

---

### Post by mc4man on 2011-07-15
Not sure why you don't just edit /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list as shown in post 5 or go ahead and delete it (and the .save if there

Anyway here is an almost default /etc/apt/sources.list - disabled the always worthless extra repo, note this has nothing to do with your improper /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list file
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha i386 (20110705.1)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

---

### Post by rburkartjo on 2011-07-15
mc tks to you all all others
you of course were write that adding the sources would not by itself fix the problem

first a ran

sudo rm -rf /etc/apt/sources.list.d/*
deleted old source list
then install the sources you gave me. tks for the clean version.

i had to do this years ago just couldnt remember how

---

### Post by rburkartjo on 2011-07-15
mc just realized that ubuntu tweak keeps a copy of the basic source list. my bad

---

