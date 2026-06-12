---
title: "Avant Window Navigator BZR (0.3.1) Install issues"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by uhoh_zombies on 2008-04-23
I'm trying to install Avant Window Manager 0.3.1 [bzr] onto Gutsy, and I'm running into some issues.

First of all, updating the repositories.

My source is:
[http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/)

And for my binary and source repositories, I have:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy avant-window-navigator
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy avant-window-navigator

And when I reload them, it'll get to 68/69 installed packages and I'll get this:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences-
[http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:) 404 Not Found
[http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/avant-window-navigator/source/Sources.gz:](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/avant-window-navigator/source/Sources.gz:) 404 Not Found


Anybody else hit this issue?
If so, how can I fix it, or, is there an easier way?

And sudo apt-get for the awn bzr doenst work.

---

### Post by nicedude on 2008-04-23
Here is a link to a guide on installing that on Ubuntu [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) 

Also I am not possitive but I think your repository listings for this have an extra character in them

This is how yours are
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy avant-window-navigator
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy avant-window-navigator

I think they should look like this
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy avant-window-navigator
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy avant-window-navigator

No "/" after ubuntu

---

### Post by Ub1476 on 2008-04-23
I use those found on this link:

[https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

It's the trunk build of AWN though, which means, more features but more unstable (even though things works okay for me except for some plugins).

---

