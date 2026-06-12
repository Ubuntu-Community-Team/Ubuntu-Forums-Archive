---
title: "dock aplets"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by garrettstarnes on 2008-05-04
I just installed the awn dock.  How do I get all of the aplets that go on it?

---

### Post by lazyart on 2008-05-04
[http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/](http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/)

It's fiesty, but it should be similar.  Google is your friend.

---

### Post by tjwoosta on 2008-05-04
i just had this problem the other day 

first i had to add these repositories to /etc/apt/sources.lst
```

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```
do that like this
```

sudo gedit etc/apt/sources.lst

```
then just copy then from above and paste them at the bottom of the list
click save
then do this to update synaptic
```

sudo apt-get update

```
then do this to install the good AWN
```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```
theres a guide here
[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive")

thats where i got all my info


now i have like 30 applets to choose from

---

