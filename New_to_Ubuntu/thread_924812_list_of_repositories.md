---
title: "list of repositories"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by da.tiger on 2008-09-19
Could someone please link me to a list of repositories available for ubuntu Hardy, which are not included in the package manager and other managers,?

thanks

also, when ubuntu moves from one stable to another, do we have to completely reinstall? or just update

---

### Post by unutbu on 2008-09-19
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Although it is possible to upgrade your distribution, I would not recommend doing it that way. 

It is better to use a partition editor like GParted to create a new 10GB partition and install the new distro there. This way, you can look before you leap.

---

### Post by kostkon on 2008-09-19
> **da.tiger said:**
> Could someone please link me to a list of repositories available for ubuntu Hardy, which are not included in the package manager and other managers,?

thanks

also, when ubuntu moves from one stable to another, do we have to completely reinstall? or just update
For what repositories are you specifically looking for?

---

### Post by da.tiger on 2008-09-20
i love exploring new apps, so any repositories having apps and such which i can search from my adept manager

---

### Post by Paqman on 2008-09-20
I've had all my upgrades work fine. If you're worried at all, just back up beforehand (a good thing to do anyway). 

It's a good idea to disable any weird repos you're using before upgrading, and obviously the more non-standard your setup is, the less likely you are to have a successful upgrade. For example, installing from source is a common way to create a system that won't upgrade smoothly, because it breaks the dependency system that upgrades rely on.

---

### Post by kostkon on 2008-09-20
> **da.tiger said:**
> i love exploring new apps, so any repositories having apps and such which i can search from my adept manager
You can find some PPAs [here]("http://ubuntuforums.org/showthread.php?t=871935"). Prefer to use only the official ones, not the personal. For example, the PPAs for *Deluge*, *AWN*, etc. are really handy.

Also, some other:

Official Skype repo
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

*Wine* repo [here]("http://www.winehq.org/site/download-deb").
*Miro* repos [here]("http://www.getmiro.com/download/ubuntu.php").

You can also check [*Playdeb*]("http://www.playdeb.net/").

These repos will rarely cause any problems during an upgrade.

It is better that you don't use personal repos from other sources that usually offer a variety of apps. In most cases these repos will mess your dependencies and create problems in general.

But, it's perfectly OK if you want to use project repos (like the above) from Launchpad (i.e. PPAs) or from the projects directly.

---

### Post by da.tiger on 2008-09-20
thanks for all those, My ubuntu is really great now. I ve added so much stuff that it works way better than windows, yet there are no performance related issues. 

I havent opened windows for a long time ;)

---

### Post by Perfect Storm on 2008-09-20
## Viewizard Games repository
deb [http://viewizard.com/linux](http://viewizard.com/linux) debian/

## 465 Free Fonts
deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main

## Ubuntu Tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main


and: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

Some I uses.

---

