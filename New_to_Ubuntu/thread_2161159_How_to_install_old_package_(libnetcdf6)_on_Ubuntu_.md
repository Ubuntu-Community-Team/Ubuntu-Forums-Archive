---
title: "How to install old package (libnetcdf6) on Ubuntu 13.04?"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by Eleutharios on 2013-07-09
I recently upgraded to Ubuntu 13.04 from from 12.04 since I was tired of using out-of-date packages. Now I find I have the opposite problem. One of the package I need (libnetcdf6) appears to be no longer supported. When I try to install it, I get the following errors:

```
$ sudo apt-get install libnetcdf6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnetcdf6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnetcdff5:i386 libnetcdfc7:i386 libnetcdfc++4:i386 libcf0:i386 libnetcdff5
  libnetcdfc7 libnetcdfc++4 libcf0

E: Package 'libnetcdf6' has no installation candidate
```

When I try to apt-get the package it says replace libnetcdf6, I get more errors:

```
$ sudo apt-get install libnetcdff5:i386 libnetcdfc7:i386 libnetcdfc++4:i386 libcf0:i386 libnetcdff5 libnetcdfc7 libnetcdfc++4 libcf0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcf0 is already the newest version.
libcf0 set to manually installed.
libnetcdfc++4 is already the newest version.
libnetcdfc++4 set to manually installed.
libnetcdfc7 is already the newest version.
libnetcdfc7 set to manually installed.
libnetcdff5 is already the newest version.
libnetcdff5 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcf0 : Conflicts: libcf0:i386 but 1:4.1.3-6 is to be installed
 libcf0:i386 : Conflicts: libcf0 but 1:4.1.3-6 is to be installed
 libnetcdfc++4 : Conflicts: libnetcdfc++4:i386 but 1:4.1.3-6 is to be installed
 libnetcdfc++4:i386 : Conflicts: libnetcdfc++4 but 1:4.1.3-6 is to be installed
 libnetcdfc7 : Conflicts: libnetcdfc7:i386 but 1:4.1.3-6 is to be installed
 libnetcdfc7:i386 : Depends: libhdf5-7:i386
                    Conflicts: libnetcdfc7 but 1:4.1.3-6 is to be installed
 libnetcdff5 : Conflicts: libnetcdff5:i386 but 1:4.1.3-6 is to be installed
 libnetcdff5:i386 : Conflicts: libnetcdff5 but 1:4.1.3-6 is to be installed
E: Unable to correct problems, you have held broken packages.


```

What is the best way to install this package? Is it safe to just add a ppa to get it and if so, how do I find which ppa to add?

Thanks in advance for the help.

---

### Post by dino99 on 2013-07-09
[https://bugs.launchpad.net/ubuntu/+source/netcdf/+bug/1169597](https://bugs.launchpad.net/ubuntu/+source/netcdf/+bug/1169597)

check that all main/universe/multiverse repos are activated (glance at either synaptic or /etc/apt/sources.list) because netcdf packages are still there : libnetcdf6 inside the precise archive; on newer ubuntu versions, due to the bug fix, only 5 & 7 versions are available. But i cant see changes inside 7 that make you saying 6 is needed.
[https://launchpad.net/ubuntu/+source/netcdf](https://launchpad.net/ubuntu/+source/netcdf)

you can download the packages inside an empty folder, then running "sudo dpkg -i *" on them (without the quotes)

---

### Post by DeathByDenim on 2013-07-09
Just to clarify the errors you are getting: You didn't need to install all of the suggestions. You have libcf0 conflicting with libcf0:i386 for example. I'm guessing you are running a 32-bit version of Ubuntu? In any case, you can get rid of these: "libnetcdff5:i386 libnetcdfc7:i386 libnetcdfc++4:i386 libcf0:i386".
If there is still trouble with apt-get, you can get it to fix itself by running
```
sudo apt-get -f install
```

---

### Post by Eleutharios on 2013-07-09
So I checked /etc/apt/sources/list and all the sources appear to be uncommented. I also downloaded netcdf (netcdf_4.1.3.orig.tar.gz) and extracted it. when i try to run "sudo dpkg -i" from inside the folder. netcdf_4.1.3, it says it needs a file argument. What should I use for this?

The reason I need libnetcdf6 is so that I can run [this]("http://solvcon.readthedocs.org/en/latest/install.html") software.

Lastly, I'm running a fresh install of 13.04 64-bit. I've only installed a few things which should be unrelated (LaTex, Gvim, etc).

---

### Post by DeathByDenim on 2013-07-09
"sudo dpkg -i" needs the debian packages as the argument. You missed the asterisk * in dino99's command. But for that you need to download the *.deb packages first in the link that dino99 gave.

Regarding solvon, you can try using this
```
sudo apt-get install build-essential gcc gfortran scons \
liblapack-pic liblapack-dev libnetcdf-dev libnetcdfc++4  libnetcdfc7    libnetcdff5 netcdf-bin \
libscotch-dev libscotchmetis-dev libscotch-5.1 \
python2.7 python2.7-dev cython python-numpy python-nose gmsh python-vtk
```
instead of what they suggest on the website you linked to. After that follow the instructions they gave. It may just compile with the newer version of netcdf (but maybe not).

---

### Post by Eleutharios on 2013-07-10
Thanks - silly oversight on my part. Sorry, I'm a kind of a newbie. After clicking on dino99's link, which file do I need? I tried getting the following files from under the the Precice Pangolin dropdown and it came up with errors.

```
~/Downloads$ ls
libnetcdf6_4.1.1-6_amd64.deb     netcdf-bin_4.1.1-6_amd64.deb
libnetcdf-dev_4.1.1-6_amd64.deb  netcdf-dbg_4.1.1-6_amd64.deb
~/Downloads$ sudo dpkg -i *
(Reading database ... 333916 files and directories currently installed.)
Preparing to replace libnetcdf6 1:4.1.1-6 (using libnetcdf6_4.1.1-6_amd64.deb) ...
Unpacking replacement libnetcdf6 ...
Replaced by files in installed package libcf0 ...
Replaced by files in installed package libnetcdff5 ...
dpkg: warning: downgrading libnetcdf-dev from 1:4.1.3-6 to 1:4.1.1-6
Preparing to replace libnetcdf-dev 1:4.1.3-6 (using libnetcdf-dev_4.1.1-6_amd64.deb) ...
Unpacking replacement libnetcdf-dev ...
dpkg: warning: downgrading netcdf-bin from 1:4.1.3-6 to 1:4.1.1-6
Preparing to replace netcdf-bin 1:4.1.3-6 (using netcdf-bin_4.1.1-6_amd64.deb) ...
Unpacking replacement netcdf-bin ...
Selecting previously unselected package netcdf-dbg.
Unpacking netcdf-dbg (from netcdf-dbg_4.1.1-6_amd64.deb) ...
dpkg: dependency problems prevent configuration of libnetcdf6:
 libnetcdf6 depends on libhdf5-serial-1.8.4 | libhdf5-1.8.4; however:
  Package libhdf5-serial-1.8.4 is not installed.
  Package libhdf5-1.8.4 is not installed.
 libcf0 (1:4.1.3-6) breaks libnetcdf6 (<< 1:4.1.1-7~) and is installed.
  Version of libnetcdf6 to be configured is 1:4.1.1-6.
 libnetcdfc7 (1:4.1.3-6) breaks libnetcdf6 (<< 1:4.1.1-7~) and is installed.
  Version of libnetcdf6 to be configured is 1:4.1.1-6.
 libnetcdfc++4 (1:4.1.3-6) breaks libnetcdf6 (<< 1:4.1.1-7~) and is installed.
  Version of libnetcdf6 to be configured is 1:4.1.1-6.
 libnetcdff5 (1:4.1.3-6) breaks libnetcdf6 (<< 1:4.1.1-7~) and is installed.
  Version of libnetcdf6 to be configured is 1:4.1.1-6.

dpkg: error processing libnetcdf6 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnetcdf-dev:
 libnetcdf-dev depends on libnetcdf6 (= 1:4.1.1-6); however:
  Package libnetcdf6 is not configured yet.

dpkg: error processing libnetcdf-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of netcdf-bin:
 netcdf-bin depends on libhdf5-serial-1.8.4 | libhdf5-1.8.4; however:
  Package libhdf5-serial-1.8.4 is not installed.
  Package libhdf5-1.8.4 is not installed.
 netcdf-bin depends on libnetcdf6; however:
  Package libnetcdf6 is not configured yet.

dpkg: error processing netcdf-bin (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of netcdf-dbg:
 netcdf-dbg depends on libnetcdf6 (= 1:4.1.1-6); however:
  Package libnetcdf6 is not configured yet.

dpkg: error processing netcdf-dbg (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libnetcdf6
 libnetcdf-dev
 netcdf-bin
 netcdf-dbg
```

---

### Post by mc4man on 2013-07-10
Did you actually try the app you want to run with the 4.1.3 version of netcdf in raring & if so what was the error?

(the app's page just says it needs netcdf 4+ which is what both precise (4.1.1) & raring have.

I would not try to use the precise packages in raring

---

### Post by Eleutharios on 2013-07-10
I tried runnung nosetests and one of the tests failed. I suppose it could be due to another issue though.

---

### Post by Eleutharios on 2013-07-11
Well, I'm still getting the same error, but the examples are running.

---

### Post by mc4man on 2013-07-11
> **Eleutharios said:**
> Well, I'm still getting the same error, but the examples are running.

Without seeing the error, (and may be meaningless to me anyway), I'd say it's not the version of libnetcdf* you have, typically an issue with a required .so would cause a segfault

---

