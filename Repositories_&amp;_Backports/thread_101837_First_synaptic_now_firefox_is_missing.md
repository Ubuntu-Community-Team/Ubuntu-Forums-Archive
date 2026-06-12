---
title: "First synaptic now firefox is missing"
date: 2005-12-10
forum: Repositories &amp; Backports
---

### Post by Heretic09 on 2005-12-10
A couple of days a go I tried to install synaptic from apt sources and found out that it wasn't in universe or multiverse sections of ubuntu's official repositories. Kinda annoying but I stuck with adept. 

So I figured I may as well install freenx. Added the seveas repo and got the message that the package expect was missing. Very bizzarre since all major distros seem to have it. So I grab it from debians website install it and i'm finally able to install freenx. 

I figured the worst was over since the rest of the apps I want to use are pretty standard. So I start with a mainstream app like firefox, I get the following message: 

Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

Great so no firefox. I figure i'd install gambas and port over some of my vb apps. I get the following message:
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gambas: Depends: gambas-gb-sdl but it is not going to be installed
E: Broken packages

I never had any of these problems in hoary. I like breezy and all but the repo management has really gone downhill. Thank god for debian's website.

---

### Post by Leif on 2005-12-10
first off, synaptic wouldn't be in universe or multiverse, but in main, as would firefox. have you enabled main ? these are all in the repos, so it seems you have a different problem

---

### Post by Heretic09 on 2005-12-10
Yep main is in there. I can't figure it out at all.

---

### Post by Heretic09 on 2005-12-10
Well rewrote the sources.list, added more sources and got the same problem. Got tired of fiddeling with it so I got firefox 1.5 from the mozilla site.

---

### Post by noigeaR on 2005-12-11
if you still have the same sources.list as here [http://www.ubuntuforums.org/showthread.php?t=98949](http://www.ubuntuforums.org/showthread.php?t=98949)
then you're still missing the main section from the official ubuntu archive. you have main for breezy-updates, breezy-backports, breezy-extras, and for some unofficial repos, but you haven't got a breezy main on the list.

---

### Post by Heretic09 on 2005-12-11
nah that was my old list, this is my new one but I still get the same problem:


#Main repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

#Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates multiverse

#Security
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security multiverse

#Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports multiverse

#Extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras multiverse

#Latest KDE
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

#Misc packages
#deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main

#Freenx
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all

#Amarok
deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main

#Non free
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

#Openoffice 2.0
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

#Doomsday games
deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse

Thats ok though, I already got firefox 1.5 and probably willl compile gambas or kedit from scratch later on today.

---

### Post by mschievano on 2005-12-11
the free.fr repos, doesn't work :(

---

