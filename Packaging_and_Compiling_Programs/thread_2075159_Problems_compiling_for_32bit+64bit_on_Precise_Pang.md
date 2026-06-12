---
title: "Problems compiling for 32bit+64bit on Precise Pangolin 64bit"
date: 2012-10-23
forum: Packaging and Compiling Programs
---

### Post by outofsync on 2012-10-23
This question is more related to installation than development, but given that it affects compiling, and that maybe some users here faced this same problem, I'm asking it here hoping somebody can help.

I'm on Precise Pangolin 64bit. The problem is that I cannot install both the 32bit and the 64bit packages of some X11 libs because they're defined as incompatible. I succeeded in installing almost everything (support for executing 32bit apps is installed, and support for compiling for both 32bit and 64bit libs is also installed except for the specific ones that I mention in this thread:
[http://ubuntuforums.org/showthread.php?t=2074651](http://ubuntuforums.org/showthread.php?t=2074651)

¿Do you have any suggestion for this problem? I really need to be able to compile both 32bit and 64bit X11 apps on this machine.

---

### Post by MadCow108 on 2012-10-23
the easiest way to cross compile between 32 and 64 bit is still a chroot
pbuilder makes this easy:
[https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

cliffs:
pbuilder-dist <distribution> <architecture> create
pbuilder-dist <distribution> <architecture> login
--bindmounts for mounting a folder from the parent

---

### Post by outofsync on 2012-10-23
> **MadCow108 said:**
> the easiest way to cross compile between 32 and 64 bit is still a chroot
pbuilder makes this easy:
[https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

cliffs:
pbuilder-dist <distribution> <architecture> create
pbuilder-dist <distribution> <architecture> login
--bindmounts for mounting a folder from the parent
I never used pbuilder on previous Ubuntu releases, and it was really easy for me to build for both 32bit and 64bit. Just install all the 64bit and the 32bit support, and then you only need to call "gcc -m32" or "gcc -m64" depending on whether you wish to build for 32bit or 64bit, respectively.

I think this incompatibility which affects just "libxt-dev" and "libxp-deb" is a bug, because the 32bit/64bit versions of these packages weren't incompatible on previous Ubuntu releases. So, I'm going to look how to file a bug, hoping it can be fixed or some workaround found.

I need to have a machine that lets me build with just "gcc -m32" or "gcc -m64". If it's not possible to do it on Precise Pangolin (because of these two packages incompatibilites), I'll install an older Ubuntu release (which worked fine for me in the past), or choose another distribution that allows it.

---

### Post by MadCow108 on 2012-10-23
installing both libxt-dev:amd64 and libxt-dev:i386 is fixed in ubuntu 12.10

you can also just extract the packages to some local directory and link against that.

---

### Post by outofsync on 2012-10-23
> **MadCow108 said:**
> installing both libxt-dev:amd64 and libxt-dev:i386 is fixed in ubuntu 12.10

you can also just extract the packages to some local directory and link against that.
Thanks for the information, didn't know it's fixed on 12.10. Anyway, if possible I prefer to stay on 12.04 because an LTS release fits in my workflow better.

I found there's already a filed bug for this issue:
[https://bugs.launchpad.net/ubuntu/+source/libxt/+bug/953860](https://bugs.launchpad.net/ubuntu/+source/libxt/+bug/953860)

Unfortunately it doesn't seem to be a "soon to be fixed bug". But if it's fixed on 12.10 and considering 12.04 is an LTS, I tend to believe they'll fix it.

Problem is that I needed this working a few days ago, I need to workaround this, so I think I'll think about what's the best choice.

Thanks.

---

### Post by outofsync on 2012-10-24
Finally, the best workaround I found to this issue is to install again the 64 bit packages (which implies uninstalling the 32bit ones), and do these manual links at /usr/lib/i386-linux-gnu :

sudo ln libXt.so.6 libXt.so
sudo ln libXext.so.6 libXext.so
sudo ln libXp.so.6 libXp.so

After doing this, I've what I needed (i.e.: a working compiling machine for 64bit and for 32bit)

---

