---
title: "Getting an Update error"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by biofuzion on 2013-03-17
Sorry if this has already been answered but here is the error i am getting..

W:Failed to fetch [http://repository.spotify.com/dists/precise/main/source/Sources](http://repository.spotify.com/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://repository.spotify.com/dists/precise/main/binary-i386/Packages](http://repository.spotify.com/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

If anyone could help me it would be greatly appreciated.

---

### Post by plucky on 2013-03-18
> W:Failed to fetch [http://repository.spotify.com/dists/...source/Sources](http://repository.spotify.com/dists/...source/Sources) 404 Not Found
, W:Failed to fetch [http://repository.spotify.com/dists/...-i386/Packages](http://repository.spotify.com/dists/...-i386/Packages) 404 Not Found

It is looking for a precise repository when there is none See [Here](http://repository.spotify.com/dists/stable/)

> , W:Failed to fetch [http://ppa.launchpad.net/pmcenery/pp...source/Sources](http://ppa.launchpad.net/pmcenery/pp...source/Sources) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/pp...-i386/Packages](http://ppa.launchpad.net/pmcenery/pp...-i386/Packages) 404 Not Found

This PPA doesn't have a repository for precise. See [Here](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/) So disable it in **Software Sources**.


Good Luck

---

### Post by schragge on 2013-03-18
As for the spotify repository, just specifying the right distribution and component (*stable non-free*) may be not enough. Those packages are for Debian squeeze released Feb 2011. They may run unchanged on Ubuntu natty (11.04), but to make them work on precise you will need to install some old libraries from the natty repository as described [here](http://www.webupd8.org/2011/12/how-to-install-native-spotify-linux.html).

---

