---
title: "I have 14 - any good reasons to upgrade to 15?"
date: 2015-11-18
forum: New to Ubuntu
---

### Post by GreysonB on 2015-11-18
I have always been a proponent of "If it works, don't fix it."

14 is working pretty well (...except for Firefox constantly crashing Adobe Flash  - I just avoid Firefox for video ...).

Should I upgrade to 15 or just keep a working system, well, working ?

---

### Post by QIII on 2015-11-18
Hello!

14.04 or 14.10?

---

### Post by sudodus on 2015-11-18
I'm also a  proponent of "If it works, don't fix it." :-)

You may need the latest and greatest

1. in a new computer to manage some new piece of hardware,

2. if you need a new version of an application program, that is only available in a newer version of Ubuntu.

-o-

Ubuntu promises support of 14.04.1 LTS until April 2019. If you start update/upgrading it to new point releases ...2, ...3, ...4, you should continue until 14.04.5 LTS, which will also be supported until April 2019. Ubuntu 14.10 has passed end of life and should not be used.

I don't think that the problems with Adobe Flash depend on the version of the Ubuntu operating system (as long as the version is still supported and receives updates).

***Edit:*** See this link

[LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

But it is risky. ***Best is to stay with 14.04.1 LTS*** until April 2019 (or to do-release-upgrade to a future LTS version). In other words, avoid upgrading the LTS enablement stack, do only regular updates/dist-upgrades.

---

### Post by GreysonB on 2015-11-18
Ubuntu System Settings - Details say 14.04

And, yes, I understand Adobe is not supporting Firefox anymore.  Not a problem as it works fine, so far, in Chrome.

---

### Post by QIII on 2015-11-18
For the moment, I'd recommend staying with 14.04.  It's an LTS (Long Term Support) release and will be supported until 2019. Anything you upgrade to now will be a non-LTS version -- which will only be supported for 9 months.  In April, 16.04 will be released and it will also be an LTS.

It ain't broke ...

---

### Post by Skaperen on 2015-11-18
i am staying on 14.04 LTS.  i might upgrade to 16.04 LTS when the time comes, or maybe 18.04. _it ain't broke_.

---

### Post by GreysonB on 2015-11-18
Thanks all!

I'm gonna stick with what works.  Good to know Ubuntu still has a vibrant community.

):P

---

### Post by tgalati4 on 2015-11-18
I use the 1-year rule.  When 16.04 comes out in April 2016, I wait 1 year (April 2017) and then find another computer, or build one, and install the next LTS.  That way I still have my working 14.04 LTS, and now I have a newer, 16.04 system with 1 year of updates and bug fixes.  Unfortunately, new users will take whatever is the latest and install it and find a less-than-polished experience.  Waiting 1 year seems like a long time, and it is, but that seems to be the time it takes to "crisp up" the LTS release.  I prefer my roast chicken to be fully crisp.

If you don't have a spare computer to devote to a 2nd Ubuntu machine, then you could set up dual-boot, or set up a virtual machine to test the next LTS version.

---

### Post by jdeca57 on 2015-11-18
Some input from a neutral source might be useful, and I don't mean mine but that of distrowatch (.com) where the feeling seems to be that recent changes are more like a (slow) evolution. I follow the changes in an Virtualbox VM and have 15.10 running under 14.04. There is no compelling reason for me to change anything. Possibly - if the planned changes like a new version of unity aren't ready for 16.04 that reasoning will hold. If you want the latest versions of software like LibreOffice 5 (but why?) then a VM is all you need.

---

### Post by Bucky Ball on 2015-11-18
> **tgalati4 said:**
> I use the 1-year rule.  When 16.04 comes out in April 2016, I wait 1 year (April 2017) and then find another computer, or build one, and install the next LTS.  That way I still have my working 14.04 LTS, and now I have a newer, 16.04 system with 1 year of updates and bug fixes.  Unfortunately, new users will take whatever is the latest and install it and find a less-than-polished experience.  Waiting 1 year seems like a long time, and it is, but that seems to be the time it takes to "crisp up" the LTS release.  I prefer my roast chicken to be fully crisp.

If you don't have a spare computer to devote to a 2nd Ubuntu machine, then you could set up dual-boot, or set up a virtual machine to test the next LTS version.

> **jdeca57 said:**
> If you want the latest versions of software like LibreOffice 5 (but why?) then a VM is all you need.

+1 to both of these. I'll just throw in that 14.04 LTS is also upgradeable to 16.04LTS via the net. Some avoid that method but I've used it a lot and always been fine for me (but I run a basic system with no added PPAs). :)

---

### Post by tgalati4 on 2015-11-18
Yes, an in-place LTS-to-LTS upgrade is a convenient feature and works 80% of the time.  It's the 20% that we see in the forums.  

Things that trip it up:

Was running 32-bit and 32-bit is no longer available or some specific library is not built anymore in 32-bit.

Motherboard can't handle the newer kernel in the latest LTS.  Either wait for a patch, or discover that your motherboard has been dropped from support.

Was running a proprietary graphics card AMD/ATI, or nVidia, and the new LTS either doesn't support the older proprietary drivers or the new drivers don't work, or they don't exist.  Take your pick.

You have installed 3rd party PPA's so you can run the latest version of Gnome3 or MATE or XFCE.  Incompatibilities between the new LTS and your current, customized desktop environment are bound to occur.  So, turn off the PPA's in /etc/apt/sources.list and hope your system boots.

You run out of disk space during the in-place upgrade.  Really?  It happens more than you think.  Recovery is difficult.  Or, the disk starts to fail because of the excessive writes during an installation, which now takes out your previously-working system.  Since LTS-to-LTS is on older hardware, the stress of an in-place upgrade can push some older hardware over the edge.

I'm sure there are a few other Use Cases that I have missed.

---

### Post by sudodus on 2015-11-18
> **tgalati4 said:**
> Yes, an in-place LTS-to-LTS upgrade is a convenient feature and works 80% of the time. It's the 20% that we see in the forums.
...
I'm sure there are a few other Use Cases that I have missed.

Conclusion: you should always ***back up everything that you want to keep*** before upgrading to a new version.

---

