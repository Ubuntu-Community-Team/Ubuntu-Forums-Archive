---
title: "Upgrading causes problems?"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by wwwho on 2014-01-20
Hi,

I am new to Linux. AS a newbie I am using a book to become familiar with the subject. The book I am using (Kofler: Linuxhandbuch; It is in German:-))mentions that upgrading from one version of a distribution to a more recent one is prone to introduce problems and thus recommends to reinstall instead of doing upgrades.

I wonder what your experience is. 

A funny thing I noticed is: I was somehow to disappointed to hearing that. However, when I come to think of it going from one version of Windows to another is working the same way. You way upgrade but ... well I have never done it because I just expect too many issues. So interestingly I ws expecting more from Linux/ubunte than I would from Windows right from the start. Not entirely fair ;-)

---

### Post by Leo_Massey on 2014-01-20
Im new too :p What i personaly will do is partition my drive so the root and home partitions are separate  This means that you can do a clean install of a new Ubuntu version without loosing anything in the home folder,as it is separate from the root directory :p

---

### Post by ibjsb4 on 2014-01-20
Fresh install gets my vote.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=fresh+install+vs+version+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=fresh+install+vs+version+upgrade&sa=Search&cof=FORID:9)

---

### Post by wwwho on 2014-01-20
Ouch! That makes the non-LTS versions somewhat unatractive ...

Is it possible to install some components from the non-LTS distros on top of the LTS ones?

---

### Post by sandyd on 2014-01-20
> **wwwho said:**
> Ouch! That makes the non-LTS versions somewhat unatractive ...

Is it possible to install some components from the non-LTS distros on top of the LTS ones?

You can install them through PPAs - a few of which contain newer versions of software that may be backported from more recent versions of Ubuntu to older versions of ubuntu

---

### Post by ian-weisser on 2014-01-20
> **wwwho said:**
> I wonder what your experience is. 

Upgrading from one release of Ubuntu to the next is extensively tested, and is a supported migration path.
I have upgraded (instead of reinstalling) for seven years -14 releases!- without problems.
Upgrade vs. Reinstall is a matter of opinion and personal preference, not technical advice. They both work well.


> **wwwho said:**
> Is it possible to install some components from the non-LTS distros on top of the LTS ones?

It may be possible, but not supported nor encouraged. 
Generally, if you need to install newer software versions, you should be running the non-LTS release of Ubuntu.
If you find yourself installing PPAs and upstream tarballs to get newer kernels and software, then you should not be running an LTS.

All releases of Ubuntu include a Backports repository, where newer versions of software that are compatible with older releases are available for optional install. Backports are created, tested, and uploaded by volunteers, so availability of your favorite software is not guaranteed. Ubuntu-Backports software is not supported.

A common myth is that LTS is somehow "more stable" or "less buggy" than an interim release of Ubuntu, or that interim releases are less tested or somehow experimental. But the myths are untrue. LTS is merely intended for users who consider upgrade-every-six-months to be an annoying treadmill. The same bugfixes and testing go into both LTS and interim releases.

---

### Post by newb85 on 2014-01-20
I do a clean install every few releases as a means of de-cluttering.  I've done many upgrades on multiple machines with no problems.

---

