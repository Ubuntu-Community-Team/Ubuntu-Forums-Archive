---
title: "What is the difference in Arch and an Ubuntu Minimal?"
date: 2009-06-18
forum: Recurring Discussions
---

### Post by gymophett on 2009-06-18
It seems as if they are both the same thing. You start off with nothing, install the desktop environment and add on. It's whatever you want, on both.
So really, what is the big difference between Ubuntu Minimal Install and an Arch Install?
Thanks. :D

---

### Post by Odemia on 2009-06-18
Ubuntu minimal is still Debian based so it uses aptitude and apt-get.  Unless you start playing around with the testing repositories Ubuntu/Debian has updates every ~6 months with some minor updates in between.

Arch uses Pacman, ABS and AUR for packagemanagement, dependancies, compiling and installing.  Arch and Gentoo are the two distros I have played with that use rolling release schedules.  I have only dabbled with arch but those would be the main things I am aware of.

PS Ubuntu forums tend to be vary forgiving with questions like this.  As you move into other distros and their forums you will get no response or get hammered for asking too many questions like this.  Try googling the question first, it has been asked and answered many times.

---

### Post by kelvin spratt on 2009-06-18
Chalk and cheese in favour of Arch its a advanced  Linux distro that does not favour any desktop.  
Its a do it your self Distro if you have the skills you can do anything with it as it uses mainly vanilla packages.
Ubuntu is not as flexible as most packages are patched Debian packages so it easier to set-up but you don't have as much control. 
That said both are very good in there own right.
Arch forums are very good but they don't like answering the same ? over and over and you need to be specific.
On the other hand it has the most comprehensive step by step Wiki that's kept up-to date

---

### Post by kerry_s on 2009-06-18
> So really, what is the big difference between Ubuntu Minimal Install and an Arch Install?

arch is more work to setup.

---

### Post by Flag on 2009-06-18
Arch took me about 2 hours from scratch to working desktop, incl. all programs I use. Most tome goes in downloading eg gnome.:D

---

### Post by XubuRoxMySox on 2009-06-18
I think the better question might be, **"What's the difference between Arch and minimal Debian?"** Other than "rolling release," file and package management, one may as well just build Debian from scratch.

-Robin

---

### Post by zolookas on 2009-06-18
I think you should compare Debian testing with Arch, because they both provide pretty recent packages.

But let's compare Ubuntu minimal to Arch.

Ubuntu:
+ More binary packages in repos
+ A lot of additional repos in launchpad
+ Excellent if you want full blown gnome desktop (but I think you are using Ubuntu minimal not for that)
- Package versions are frozen every release meaning you will probably won't get the latest and greatest packages (unless they are provided in backports)
- Building packages from source is not as easy as using Arch's pkgbuild system

Arch:
+ A lot of pkgbuilds in Arch AUR repo giving you ability to build your tweaked backages from source, build packages which are not available in repos, customize packages
+ There is a great KDE repo called [kdemod]("http://kdemod.ath.cx/") which provides much better KDE4 experience
+ Information in Arch wiki will let you build system you like 
- There are less packages in repos compared to ubuntu (but remember, you have always AUR for not so popular applications)
- Arch forums don't have such a big amount of online users, so you might not get help in 3 minutes :D (but I advice you to check [arch wiki]("http://wiki.archlinux.org"))

---

### Post by juancarlospaco on 2009-06-19
I can use Arch`s repos on Ubuntu :)

---

### Post by &#32 Greg on 2009-06-19
With an Arch system, you also are encouraged to dip into your config files, for instance rc.conf would be one of your best friends. On a minimal install, the configs are still auto generated; a minimal install is still Ubuntu/Debian in the exact same way; you just need to install programs. Arch behaves in a different manner.

---

### Post by snowpine on 2009-06-20
Try them both, the differences will be clear. :)

---

### Post by kk0sse54 on 2009-06-20
> **dixiedancer said:**
> I think the better question might be, **"What's the difference between Arch and minimal Debian?"** Other than "rolling release," file and package management, one may as well just build Debian from scratch.

-Robin

No an Arch install is still very different from a Debian minimal install as there's a way more in depth process to build Arch from ground up  i.e. editing essential config files. Also to add to what everyone else said about the differences Arch uses a BSD-style init while Debian I believe uses sysvinit.

---

### Post by juancarlospaco on 2009-06-20
Ubuntu uses Upstart, created by Canonical, better than init/sysinit.
*it has been used by Fedora too.*

---

