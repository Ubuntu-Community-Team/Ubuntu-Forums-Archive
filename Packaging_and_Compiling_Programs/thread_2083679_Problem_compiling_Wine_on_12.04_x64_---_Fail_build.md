---
title: "Problem compiling Wine on 12.04 x64 --- Fail building on x64, then no X devel files"
date: 2012-11-13
forum: Packaging and Compiling Programs
---

### Post by sabersong on 2012-11-13
I'm trying to build Wine from source in order to apply a patch to fix a problem caused by an update to one of my Wine applications. 

At first it wouldn't build, claiming I couldn't build a 32 bit Wine on a 64 bit system. I installed the ia32z package, but now it's saying that it can't find the X development files and will be built without X support.

I tried following the instructions at [http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37](http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37) and also the instructions at [http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37](http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37), but neither of those deals with the X devel problem. The majority of the other posts I was able to find this weekend suggest that ther'es no need to compile Wine, but from what I've read, compiling it is the only way to apply a patch, so those suggestions aren't very helpful.

I tried compiling source code from three different locations: WineHQ, ppa:ubuntu-wine and the Wine git repository. All three have the same problems, so I figure it must be something I'm doing wrong.

---

