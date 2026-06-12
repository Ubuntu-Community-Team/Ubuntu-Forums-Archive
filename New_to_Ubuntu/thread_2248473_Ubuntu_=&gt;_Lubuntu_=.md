---
title: "Ubuntu =&gt; Lubuntu = ???"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by czgirb on 2014-10-15
Dear all, currently I used Ubuntu 14.04 LTS.
But until now I still confused: if I install Lubuntu DE, it also will install Lubuntu's application inside.
------------- for example: PCManFM to replace Nautilus, and bla bla bla ... but it's OK for me.
But after that, my Ubuntu is become Ubuntu with LXDE or Ubuntu=>Lubuntu ?
Cos based on what i know, Ubuntu 14.04 LTS is supported for 5-Year, but Lubuntu 14.04 LTS is supported for 3-Year only.
Thank you.

Is there anyone who installed LXDE or Lubuntu DE here?
What is your opinion about the Desktop Environment?
How it compare to Gnome Fallback?
Please share ...

---

### Post by Impavidus on 2014-10-15
There are two differences between Ubuntu and Lubuntu: the DE and the set of default applications. So if you install lubuntu-desktop on an existing Ubuntu system, you'll get the [union]("http://en.wikipedia.org/wiki/Union_%28set_theory%29") of the sets of default applications of Ubuntu and Lubuntu and both DEs to choose from at login. You can also install just the DE and stick to the default applications of Ubuntu, or just install whichever you like from both sets.

In either case your system will be a mix of Ubuntu and Lubuntu. Lubuntu 14.04 (like Xubuntu) has 3 years of support. This means that all software specific for Lubuntu or Xubuntu (including those common to Lubuntu and Xubuntu) gets 3 years of support, but the software from Ubuntu (or Kubuntu) and the software common to all flavours get 5 years of support.

A system of which only part of the core stuff is supported may suddenly fail. An upgrade to a supported component may break an unsupported component, which is not upgraded (like, kernel update breaks desktop). On a fully supported system both would be upgraded at the same time. This has happened on 10.04, as the desktop version is unsupported but the server version still is supported. So if you mix Lubuntu and Ubuntu 14.04, you get 3 years support on the combined system. After that, you have to move on to a new release or convert it back to a pure Ubuntu (or Kubuntu) system by uninstalling all Lubuntu-specific stuff.

---

