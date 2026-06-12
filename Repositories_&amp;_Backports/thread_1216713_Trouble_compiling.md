---
title: "Trouble compiling"
date: 2009-07-18
forum: Repositories &amp; Backports
---

### Post by Rainwolf on 2009-07-18
I am trying to install f-spot in to Ubuntu Studio disrto
I have updated and upgraded a ton of things yet I still can not get compile to work.

checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for mono... /usr/bin/mono
checking for gmcs... no
configure: error: No C# compiler found

Things I have upgraded/updated/installed:
sudo apt-get install libglib1.2-dev
sudo apt-get install build-essential
sudo apt-get install linux-kernel-headers
sudo apt-get dist-upgrade
sudo apt-get install gcc
sudo apt-get install intltool
sudo apt-get install automake1.9 libtool git-core
sudo apt-get upgrade
sudo apt-get update

sooo what am I missing?

---

### Post by Rainwolf on 2009-07-18
also installed
sudo apt-get install automake1.9 libtool git-core
sudo apt-get build-dep f-spot

---

### Post by directhex on 2009-07-18
If "apt-get build-dep f-spot" didn't yield anything, then that's rather odd.

Which Ubuntu version is this? Which f-spot package?

---

### Post by Rainwolf on 2009-07-18
The Unbuntu Studios disrto comes with a f-spot but it is a older version .4?
I'm trying to get the new version so I can work with the RAW PEF files that this older version does not seem to be able to do (Installed the tools for f-spot raw etc)

but unless I'm missing a big step somewhere I can not get f-spot to see/view my raw files and I can not get the newest f-spot to compile and install.

90% of my photography is in  RAW PEF format and I'd love to be able to work with them.

---

### Post by directhex on 2009-07-18
OK, I'm piecing together the missing information.

There are TWO versions of Ubuntu Studio currently available - one is based on Ubuntu 8.04, one is based on Ubuntu 9.04.

Ubuntu 8.04 shipped with F-Spot 0.4.2, Ubuntu 9.04 shipped with F-Spot 0.5.0.3

"apt-get source" only works if you have "deb-src" lines in your /etc/apt/sources.list file, and I don't know if these are enabled in Ubuntu Studio. You should check.

[http://packages.ubuntu.com/source/jaunty/f-spot](http://packages.ubuntu.com/source/jaunty/f-spot) lists the packages required to build the version in Jaunty - but they're Jaunty dependencies, and you'll need to apply common sense to work out the Hardy equivalents when they're not the same

---

### Post by Rainwolf on 2009-07-18
"Ubuntu 8.04 shipped with F-Spot 0.4.2, Ubuntu 9.04 shipped with F-Spot 0.5.0.3"

I did use the "hardy" version Ubuntu 8.04 shipped with F-Spot 0.4.2
I'm just getting back into linux and so I'm about 6 years behind :/ 
which means I basically know nothing anymore.

what is the difference between hardy vs jaunty? I was guessing it meant something like complete vs beta but I'm likely wrong lol

should I just install the Jaunty version of ubuntu studios?

---

### Post by Rainwolf on 2009-07-18
I meant stable vs beta

---

### Post by directhex on 2009-07-19
> **Rainwolf said:**
> "Ubuntu 8.04 shipped with F-Spot 0.4.2, Ubuntu 9.04 shipped with F-Spot 0.5.0.3"

I did use the "hardy" version Ubuntu 8.04 shipped with F-Spot 0.4.2
I'm just getting back into linux and so I'm about 6 years behind :/ 
which means I basically know nothing anymore.

what is the difference between hardy vs jaunty? I was guessing it meant something like complete vs beta but I'm likely wrong lol

should I just install the Jaunty version of ubuntu studios?

Hardy and Jaunty are both stable releases.

Jaunty is the current stable release.

Hardy is the current Long-Term Support release.

"Regular" releases are supported for 18 months, "LTS" releases are supported for more than twice that. Basically LTS releases are for people who don't want to worry about new apps

---

