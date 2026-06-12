---
title: "Can't install packages for kernel recompiling"
date: 2006-06-13
forum: Repositories &amp; Backports
---

### Post by PingunZ on 2006-06-13
Well I guess the console says more then I do 
```
kristof@Desktop:~$ sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
bin86 is already the newest version.
kernel-package is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libxcursor-dev but it is not going to be installed
                 Depends: xlibmesa-gl-dev but it is not installable or
                          libgl-dev
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
kristof@Desktop:~$

```


And This is my sources.list

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://be.archive.ubuntu.com/ubuntu dapper main restricted
deb http://be.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://be.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://be.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://be.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://be.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://be.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror2.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror.ubuntulinux.nl dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

```


Plz Help me out !! :p

Grtz PingunZ

---

### Post by PingunZ on 2006-06-14
nobody ? :s

---

### Post by xtknight on 2006-06-21
I had the same problem.  Apparently I had somehow gotten newer versions of libgl1-mesa, libglu1-mesa, and mesa-common-dev (XGL?)

I did:
sudo dpkg --force-all -r libgl1-mesa
sudo dpkg --force-all -r libglu1-mesa
sudo dpkg --force-all -r libgl1-mesa-dri

(You may need to uninstall mesa-common-dev as well.)

sudo apt-get dist-upgrade

To restore the old versions.  Then libqt3-mt-dev installed properly with a standard apt-get install libqt3-mt-dev.  Now 'make xconfig' works correctly.

---

