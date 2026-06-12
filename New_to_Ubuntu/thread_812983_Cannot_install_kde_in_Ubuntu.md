---
title: "Cannot install kde in Ubuntu"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by lolwhites on 2008-05-30
I'm trying to install KDE4 alongside Gnome, while keeping the latter as the default. The instructions I've been trying to follow are [here]("http://www.larsen-b.com/Article/281.html") and [here]("http://ubuntu-tutorials.com/2008/01/11/how-to-install-kde-40-in-kubuntu-710/"). Whatever command I use, I run into the same problems:

1. I get an error message in terminal along the lines of > Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-data_4%3a4.0.4-0ubuntu1~hardy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

2. The update manager tells me to update kde-workspace-data. When I try, it tells me that there are three broken packages. It tries to install the software anyway, then gives me the message:
> E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.0.3-0ubuntu2_all.deb: trying to overwrite `/usr/lib/kde4/share/desktop-directories/kde-development.directory', which is also in package kdebase-runtime-data-common
It then reports that the system is up to date.

3. In spite of (2), Synaptic doesn't detect any broken pakages.

4. At the login screen, KDE doesn't appear as an option.

I've installed KDE4 before, but can't remember how I did it. I have typed in commands to remove it before installing to avoid incompatibilities but don't know how successful I've been.

---

### Post by yankee83 on 2008-05-31
Were you able to fix the problem? I have a similar one right now on upgrading KDE 4.

---

### Post by lolwhites on 2008-05-31
Nope. Tried again today but the problems remain. I tried installing then updating via *sudo aptitude update* then *sudo aptitude upgrade* but got this:
> The following packages have unmet dependencies:
  kdebase-workspace: Depends: kdebase-workspace-data (>= 4:4.0.4-0ubuntu1~hardy1) but it is not installable
  kdebase-workspace-bin: Depends: kdebase-workspace-data (>= 4:4.0.4-0ubuntu1~hardy1) but it is not installable
  libplasma1: Depends: kdebase-workspace-data (= 4:4.0.4-0ubuntu1~hardy1) but it is not installable

---

### Post by alzwded on 2008-05-31
Most likely you should wait until the repos are fixed. You could always try to build kde yourself, but that might proove to be a bit annoying and time consumind and might damage your data. (that may be why apt-get says the packages are not installable)

---

### Post by avalenc on 2008-10-23
To add to this, and to maybe bring the level down a notch to, oh, extremely basic:

Is there a difference between installing KDE and installing KDE libraries? There is a KDE program that I would like to run, and know that I need to install some (all?) KDE libraries to be able to use it. 

What I would like to know is:
a) by installing libraries, am I installing all of KDE?
b) where do I find said libraries? and,
c) how do I install them? (I poked around, and have caught on that I should use aptitude instead of apt-get, but what I want much more elementary information, as in: what is the exact line of code that I enter in the terminal to do this? I'm still at cut-n-paste in all of this.)

I am presuming that I need to install the libraries first, before installing the program that I want to use.

And, finally, would there be any advantage, or disadvantage, to installing all of KDE in addition to Gnome? 

Thanks!

---

### Post by oldos2er on 2008-10-23
avalenc, all you need to do is run the command (in a terminal) "sudo aptitude install [programname]" where [programname] is obviously the name of the KDE program you want to install. aptitude will take care of the dependencies for you.

---

### Post by zvacet on 2008-10-23
@ **avalenc**

By installing some KDE package you will install libraries,but you will not install all KDE.

> And, finally, would there be any advantage, or disadvantage, to installing all of KDE in addition to Gnome?

Advantage is that you can run both desktops on your Ubuntu.If you feel that system doesn´t work properly with both desktops installed you can uninstall one of them.

[Pure GNOME]("http://psychocats.s465.sureserver.com/ubuntu/puregnome")

[Pure KDE]("http://psychocats.s465.sureserver.com/ubuntu/purekde")

---

