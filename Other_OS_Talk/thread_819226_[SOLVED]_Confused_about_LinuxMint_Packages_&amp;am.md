---
title: "[SOLVED] Confused about LinuxMint Packages &amp;amp; Repositories"
date: 2008-06-05
forum: Other OS Talk
---

### Post by kpkeerthi on 2008-06-05
I googled & read mint's wiki and user guide but I can't find the information I need. 

**1. Software Portal:**
	Are the packages installed using software portal ( the .mint files ) part of repository? I mean, if a 'new' application is made available in the portal, will be I be able to search,install & upgrade it using aptitude/apt-get? 

**2. Repositories:**
The default sources.list from the Live CD looks like this:
```

## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb http://packages.linuxmint.com elyssa main upstream import

## +++ Backports (not as stable) +++
## deb http://packages.linuxmint.com elyssa backport

## +++ Community (not as stable) +++
## deb http://packages.linuxmint.com elyssa community

## +++ Romeo (unstable) +++
## deb http://packages.linuxmint.com elyssa romeo

## +++ Source Repositories +++
## deb-src http://packages.linuxmint.com elyssa main upstream import
## deb-src http://packages.linuxmint.com elyssa community
## deb-src http://packages.linuxmint.com elyssa backport
## deb-src http://packages.linuxmint.com elyssa romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.04 Hardy (stable) +++
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

## +++ Backports & Proposed (not as stable) +++
## deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
## deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## +++ Source Repositories +++
## deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
## deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu hardy partner

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ hardy free non-free

```

How is elyssa's backport repository different from ubuntu's? If I enable this line ```
deb http://packages.linuxmint.com elyssa backport
```, should I also enable ```
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
``` which is at the bottom of sources.list? Or should I not? And who is Romeo?


Better yet, is there some place where I can read about Mint's repository.

> 
Although Linux Mint isn't a rolling distribution an LTS strategy will be put in place to ensure that Linux Mint 5 Elyssa will stay up to date over the next 2 years. Users will have the choice to enable the backport repository for Elyssa in which upgrades for important desktop applications (Firefox, Thunderbird, OpenOffice..) will be made available.
... from [http://www.linuxmint.com/rel_elyssa.php](http://www.linuxmint.com/rel_elyssa.php)
In regards to the above quote, What is the recommended source.list for mint so I keep receiving updates over the next 2 years.

---

### Post by SunnyRabbiera on 2008-06-05
Well for question 1:
Yes those .mint packages are in the repositories, the mint installer works simular to click and run but installs packages right from the repositories... its just a front end, its no different then installing a .deb from packages.ubuntu.com.

For question 2: Mint shares the same repositories as Ubuntu, the most major changes is that the media repositories are enabled by default and mint comes with proprietary stuff pre installed.

the rest of the stuff you asked is answered in question 2.

---

### Post by kpkeerthi on 2008-06-06
I asked around about this in the mint forums and got a few useful replies. Marking the thread solved.

Just in case if anyone is interested, see [http://linuxmint.com/forum/viewtopic.php?f=90&t=13155](http://linuxmint.com/forum/viewtopic.php?f=90&t=13155)

**Mint Golden Rule: ** Use only mintUpdate. Do not use apt, apt-get, aptitude if you are concerned about stability. 

[COLOR="RoyalBlue"]
**(But the plethora of repositories in mint's sources.list scares the heck out of me. Will stick with Ubuntu for now.)**[/COLOR]

---

