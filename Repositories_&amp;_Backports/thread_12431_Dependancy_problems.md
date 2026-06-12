---
title: "Dependancy problems"
date: 2005-01-24
forum: Repositories &amp; Backports
---

### Post by e4media on 2005-01-24
Hello,

I've just installed Linux and now I'm trying to install some packages which I've downloaded with another PC (ain't got internetconnection on my linux-px). Know, when I try to install packages I get the following error:

> sudo apt-get install xlibs-dev

Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
xlibs-dev: Depends: libice-dev but it is not going to be installed
Depends: libsm-dev but it is not going to be installed
Depends: libx11-dev but it is not going to be installed
Depends: libxext-dev but it is not going to be installed
Depends: libxi-dev but it is not going to be installed
Depends: libxmu-dev but it is not going to be installed
Depends: libxmuu-dev but it is not going to be installed
Depends: libxp-dev but it is not going to be installed
Depends: libxpm-dev but it is not going to be installed
Depends: libxrandr-dev but it is not going to be installed
Depends: libxt-dev but it is not going to be installed
Depends: libxtrap-dev but it is not going to be installed
Depends: libxtst-dev but it is not going to be installed
Depends: libxv-dev but it is not going to be installed
Depends: xlibs-static-dev but it is not going to be installed

(or something like this, copy't it from Internet (no Internet on linuxp ;))

What does this mean?

I get the same error when I try to install with this:

> sudo apt-get install xlibs-dev

(sources.list correct)

EDIT: i'm having these problems with all my packages

---

### Post by mendicant on 2005-01-24
Well, apt-get actually gets packages from the internet.  To install downloaded debs, you can use dpkg, like dpkg -i <.deb file>.   You can also set up your own repository and use that to install packages.  In the end, it will be much easier to simply give the linux box internet access. 

You can also try using CD installs instead of internet installs.

---

### Post by drasko on 2005-02-13
With out internet access insrtalling packages is a nightmare, since depandency chain can go to infinity... 
Connect the machine and do apt-get. Otherwise, you have to have all packages this package depends on, and the packages they depand on (and so on...) installed. So, basiccaly try the dpkg -i, and it will tell what to install before... and so on...

Drasko

---

### Post by mendicant on 2005-02-13
One other thing that might be useful is aptitude -s dist-upgrade or other command.  The important bit is the -s or --simulate, which will print the list of packages to upgrade, for instance.

Grab those packages on another computer, using aptitude download.  Transfer the files over via CD or whatever you want, then dpkg -i all of them.

---

