---
title: "apt-get -f install wants to remove almost everything"
date: 2006-01-24
forum: Repositories &amp; Backports
---

### Post by ]Nbx*cmD[ on 2006-01-24
Hi all!
Everything started when i tried to install gdesklets from a .deb package.
I did dpkg --install but i got a message saying there where unsatisfied dependencies. I downloaded and dpkg-installed the next pakages:

libncurses5_5.4-9ubuntu4_i386.deb
libasound2_1.0.9-3ubuntu3_i386.deb
libc6_2.3.5-1ubuntu12_i386.deb

Everything seemed to go right, but when i tried again to install gdesklets i got again lots of dependencies problems.

Now the problem is apt-get doesn't let me to install nothing, and when i try apt-get -f install i get the following:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  build-essential freeglut3-dev g++ g++-3.3 gtk2-engines-dev language-pack-ca language-pack-ca-base
  language-pack-en language-pack-en-base libartsc0-dev libasound2-dev libatk1.0-dev libc6-dev
  libc6-i686 libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev
  libglib1.2-dev libglib2.0-dev libglut3-dev libgnutls11-dev libgpg-error-dev libgtk2.0-dev
  libice-dev libicu28-dev libjack0.80.0-dev libjpeg62-dev libncurses5-dev libpango1.0-dev libsane-dev
  libsm-dev libstdc++5-3.3-dev libungif4-dev libusb-dev libx11-dev libxext-dev libxft-dev libxi-dev
  libxmu-dev libxmuu-dev libxp-dev libxpm-dev libxrandr-dev libxrender-dev libxt-dev libxtrap-dev
  libxtst-dev libxv-dev locales lsb ubuntu-base ubuntu-desktop xlibmesa-dev xlibmesa-gl-dev
  xlibmesa-glu-dev xlibs-dev xlibs-static-dev zlib1g-dev
0 upgraded, 0 newly installed, 60 to remove and 13 not upgraded.
Need to get 0B of archives.
After unpacking 148MB disk space will be freed.
Do you want to continue [Y/n]?

Obviously, i don't want to continue ;)
Does anybody have a solution? Thanks a lot!


]Nbx*cmD[

---

### Post by frodon on 2006-01-24
A LOT of packages depends on libc6, it's one of the most important libraries, so if you change the version of libc6 to a version which is higher than the one in the repositories then all the packages you installed from the repositories and which depends on libc6 will be removed, so here there's no solution, if you install a newer version of libc6 you will have to re-install o lot of packages by hand.
The best solution is to install the repository version of gdesklet or to install drapper drake which will use the new version of libc6 i think.

---

### Post by az on 2006-01-24
The packages that apt want's to remove are -dev packages.  You do not need them to run stuff, only to compile.  Did you try to compile gdesklets yourself?

Anyway, one of the -dev packages you installed is not in sync with the rest of them (libc6-dev?)  try running a dist-upgrade to fix this (breezy, not dapper)

If that persists, look in synaptic for a flagged package.  Also try
sudo apt-get -f install and see what it wants to do.


Avoid dpkg -i to install stuff and use apt when you can.  You would have avoided this problem.

---

### Post by ]Nbx*cmD[ on 2006-01-24
This is what i get when i try dist-upgrade:

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libasound2-dev: Depends: libasound2 (= 1.0.8-1) but 1.0.9-3ubuntu3 is installed
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is installed
  libncurses5-dev: Depends: libncurses5 (= 5.4-4) but 5.4-9ubuntu4 is installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14 but it is not installable
E: Unmet dependencies. Try using -f.

You are right, i should have installed it by apt-get :'(
I guess upgrading my hoady to breezy should fix that problem but... i also can't run apt-get upgrade!!

---

### Post by ]Nbx*cmD[ on 2006-01-24
Removing and reinstalling these pakages should work right?
But... can i uninstall pakages like ubuntu-base and ubuntu-desktop without getting big problems?

---

### Post by ]Nbx*cmD[ on 2006-01-24
Solved, just did apt-get -f install, uninstalled all these pakages and then updated to breezy badger.
Now everything works well and... i have the last Ubuntu =D>

---

