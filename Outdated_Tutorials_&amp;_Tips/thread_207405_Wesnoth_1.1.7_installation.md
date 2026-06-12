---
title: "Wesnoth 1.1.7 installation"
date: 2006-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Nikos_M on 2006-07-01
The following applies also for later than the mentioned Wesnoth versions.

Well after searching a bit I found out that only the sources of wesnoth 1.1.7 exist for ubuntu. The problem is that for me (for some weird reason) they did not work.So I decided to get the debian packages from [http://packages.debian.org/unstable/games/wesnoth](http://packages.debian.org/unstable/games/wesnoth)
and install them from there with dpkg -i --force-depends  .Well that did seem to work but then synaptic complained all the time that i have a broken package and it refused to update the system.So in the end I decided to get the sources from a more Wesnoth friendly distribution (good old Debian) and compile them for the ubuntu environment.
So here it is.The following are done as root so do a "su" if you are not.

1.add in your /etc/apt/sources.list:
deb-src [http://ftp.nl.debian.org/debian/](http://ftp.nl.debian.org/debian/) sid main
(you can always change the "nl" to your local mirror - e.g."http://ftp.de.debian.org/debian/" )
2.apt-get update
3.apt-get source wesnoth
4.apt-get build-dep wesnoth
5.cd wesnoth-<version>
6.apt-get install fakeroot build-essential (just in case you dont have them)
7.dpkg-buildpackage -rfakeroot

Wait for a couple of minutes ...

Now you have the .debs that run on your ubuntu!
8.cd ..
9.dpkg -i wesnoth*.deb
and you are basically done.

You might not want to install the server but that is up to you.Install whatever package you want from the ones you created with dpkg -i

---

