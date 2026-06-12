---
title: "Mirroring packages from a launchpad PPA to my own repo"
date: 2015-02-19
forum: Packaging and Compiling Programs
---

### Post by Kyle_Goodwin on 2015-02-19
Hello,

I have set up a local repository for packages using mini-dinstall which works great for my own packages which I upload using dput and scp.  My packages have some dependencies which are found in a launchpad PPA and I would like to mirror those packages into my local repository so that only the official repositories and mine are necessary to install my package and no additional PPAs must be set up.  I haven't been able to figure out how to copy packages over from the PPA to my repository since uploading them with dput needs a .changes file and I only have the binary .debs and something like dpkg-scanpackages builds the whole repository structure after scanning the packages rather than including the scanned packages into an existing repository structure as far as I can tell.  Any help would be greatly appreciated.

Thanks!

---

### Post by TheFu on 2015-02-20
Don't know if this will help, but you can run a caching server for APT packages, apt-cacher-ng.  This won't disconnect you from the internet 100%, but it will limit the bandwidth used.  Apt-Cacher-NG is very easy to install and setup.  Then just tell every client machine to use it as a proxy in /etc/apt/apt.conf.d/ with 1 line.
Very simple.

Makes reinstalling an OS here about 14 minutes because all the needed packages are already on the LAN.

---

