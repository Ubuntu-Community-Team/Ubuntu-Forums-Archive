---
title: "Compiling in KDevelop"
date: 2006-07-08
forum: Programming Talk
---

### Post by CodeMonkeyX on 2006-07-08
Hi everyone,
I am new to Ubuntu but have been using Linux for a long time. I recently installed KDevelop on a standard Kubuntu installtion, and I am having problems compiling C++ applications in KDevelop.

First I got errors for missing automake, and configure. I fixed that after checking the ubuntuguide and installing the "build-essentials" package. But now I am getting messeages about missing basic development things like X11 Headers, and I expect I will be missing every library required to actually compile a application.

My question is does Kubuntu have an easy way to set up a development workstation like other distros?

I used Slackware a couple of years ago and they had a very simple method where you simple say I am using this install for C++ Development, and I want to make X11 applications, and QT applications etc. It then went ahead and installed the required stuff.

Please do not say I have to use apt-get and install every single library and tool needed to build an standard application.

---

### Post by CodeMonkeyX on 2006-07-08
I saw in another post someone said to install "x-window-system-dev" which I assume is a virtual package with all the required headers and libs for X11 development.

But I can not find the package in adept for Dapper.

---

### Post by asimon on 2006-07-08
> **CodeMonkeyX said:**
> I saw in another post someone said to install "x-window-system-dev" which I assume is a virtual package with all the required headers and libs for X11 development.

But I can not find the package in adept for Dapper.
The equivalent package in Dapper is [xorg-dev](http://packages.ubuntu.com/dapper/x11/xorg-dev). That was changed during the move to the modular x server.

---

### Post by Randomskk on 2006-07-08
Try installing kde-devel, this should contain some of the stuff needed for development. If that's not enough, kde-devel-extras has some more stuff.

Not sure if that'l help you out completely, but may be useful.

---

### Post by CodeMonkeyX on 2006-07-08
Thanks.
I was looking through the list of dependent packages that kdebase-dev installs and it seems like pretty much everything does get installed.

But now when I select it it says "BREAK(install)" next to it. I guess that is more of a ubuntu support question though.

---

### Post by umuro on 2006-08-17
This is the problem while installing kde-devel
> 
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.2-0ubuntu18.1) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: kdelibs-bin (= 4:3.5.2-0ubuntu18.1) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: libarts1-dev (>= 1.5-rc1) but it is not going to be installed



---

### Post by mycelo on 2006-08-17
Firstly I suggest that you install KDevelop from the latest kubuntu repositories, that you can find [here]("http://kubuntu.org/announcements/kde-354.php"). Latest stable KDevelop is 3.3.4. You may need to run:
```
$ sudo apt-get dist-upgrade
```
Install from Synaptic, and when selecting the very KDevelop package, also select all recommended and suggested packages. You'll be going to download quite a few things, but you'll have everything that you may need (except docs). You'll also download KDE desktop in the process.

When it complains about some library/compiler version, you're likely to have it already, but you're just pointing to the wrong version. Use the update-alternatives command to choose the correct version. You should be able to design, compile and debug powerful C++/Qt3 applications.

Hope it helps.

mycelo

---

