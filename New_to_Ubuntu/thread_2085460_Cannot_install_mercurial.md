---
title: "Cannot install mercurial"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by vimothy on 2012-11-18
Hi all,

I'm having a lot of trouble trying to install Mercurial on my system. (I'm running 32 bit Ubuntu 12.04.)

When I try to install Mercurial using the command, 

> sudo apt-get install mercurial

I get a message saying, 

> Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package mercurial

I looked around online and people suggested first doing an update, and then trying to install the package. So I tried this, but I get the same error.

Another suggestion was to make sure that "universe" settings were switched on or un-commented. I checked this and they appear to be.

Can anyone help? Thanks!

EDIT: Also tried running,

> sudo add-apt-repository ppa:mercurial-ppa/releases
sudo apt-get update
sudo apt-get install mercurial

But get the same error.

---

### Post by Gster4 on 2012-11-18
you can manually download debs(from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) or the ppa) and use
```
dpkg -i <package name>.deb
```

---

### Post by ibjsb4 on 2012-11-18
It looks to me that should be:

ppa:mercurial-ppa/stable-snapshots

If that does not work, you can add it manually:

deb [http://ppa.launchpad.net/mercurial-ppa/stable-snapshots/ubuntu](http://ppa.launchpad.net/mercurial-ppa/stable-snapshots/ubuntu) precise main

[https://launchpad.net/~mercurial-ppa/+archive/stable-snapshots](https://launchpad.net/~mercurial-ppa/+archive/stable-snapshots)

---

### Post by vimothy on 2012-11-18
Managed to sort this out. Did a comprehensive install of python and it corrected whatever was missing / wrong / not enabled. Thanks anyway.

---

### Post by ibjsb4 on 2012-11-18
Got it fixed, that's what counts  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

