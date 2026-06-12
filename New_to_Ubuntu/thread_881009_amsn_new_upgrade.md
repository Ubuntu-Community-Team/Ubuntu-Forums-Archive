---
title: "amsn new upgrade"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by kahram.yoon on 2008-08-05
does anybody know where i can intall the new 0.97.2 aMSN upgrade?  i tried these sites:
[http://www.getdeb.net/release.php?id=2875](http://www.getdeb.net/release.php?id=2875)
[http://www.amsn-project.net/](http://www.amsn-project.net/)
[http://ubuntuforums.org/showthread.php?t=880839&highlight=aMSN+connection](http://ubuntuforums.org/showthread.php?t=880839&highlight=aMSN+connection)

all tried install but just messed it up even more
any easy way to install the new upgrade?

---

### Post by NESFreak on 2008-08-05
remove amsn
```
sudo apt-get remove amsn
```
install tcl/tk
```
sudo apt-get install tk8.4
```
from the amsn site download the autopackage installer for tcl/tk 8.4
now it should work (since all your setting are stored in your homedir none of them should have changed)

it worked for me

---

### Post by scradock on 2008-08-05
> **NESFreak said:**
> remove amsn
```
sudo apt-get remove amsn
```
install tcl/tk
```
sudo apt-get install tk8.4
```
from the amsn site download the autopackage installer for tcl/tk 8.4
now it should work (since all your setting are stored in your homedir none of them should have changed)

it worked for me

Tried it, and it didn't work - the autopackage gave a big red FAIL message after downloading all sorts of unknown stuff from random-looking places.

Honestly, if I was using Windows and saw that sort of behavior I'd be sure I'd been suckered into running a trojan.

---

### Post by NESFreak on 2008-08-05
> **scradock said:**
> Tried it, and it didn't work - the autopackage gave a big red FAIL message after downloading all sorts of unknown stuff from random-looking places.

Honestly, if I was using Windows and saw that sort of behavior I'd be sure I'd been suckered into running a trojan.

autopackage is a distribution independent package system, it has to be installed first. Many linux programs are distributed this way nowadays (including pidgin (or you can compile it yourself, or wait for the .deb)

no idea why it failed

---

### Post by kahram.yoon on 2008-08-05
did what u said
it seemed to be working at first but when it was finished installing
aMSN did not appear anywhere so it appears that it did not install
here is what happened in the terminal:

desktop:~$ sudo apt-get install tk8.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tcl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  tk8.4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1001kB of archives.
After this operation, 2687kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main tk8.4 8.4.16-2ubuntu1 [1001kB]
Fetched 1001kB in 2s (391kB/s) 
Selecting previously deselected package tk8.4.
(Reading database ... 218529 files and directories currently installed.)
Unpacking tk8.4 (from .../tk8.4_8.4.16-2ubuntu1_i386.deb) ...
Setting up tk8.4 (8.4.16-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Jack M. on 2008-08-05
Many people have had luck upgrading to a newer version using the file linked in [this post]("http://ubuntuforums.org/showthread.php?p=5526804#post5527433"), which seems to have fixed the issue. (To install it once it's downloaded, double-click on it and select "Install".)

EDIT: Oops, I think I posted this in the wrong thread. Nevertheless, that should still be a way to install aMSN without the tcl/tk installer.

---

### Post by scradock on 2008-08-05
The updated amsn deb is available in Hardy-proposed - no need to hunt for work-arounds. It is labeled as a ubuntu5.1 version (upgraded from ubuntu5), but it fixes the connect problem.

---

### Post by monraaf on 2008-08-05
> **scradock said:**
> The updated amsn deb is available in Hardy-proposed - no need to hunt for work-arounds. It is labeled as a ubuntu5.1 version (upgraded from ubuntu5), but it fixes the connect problem.

How long does it usually take to go from hardy-proposed to hardy-updates? 

If I enable hardy-proposed updates I will be replacing a lot of my packages with untested and unstable versions, no?

---

### Post by tuxxy on 2008-08-05
I just compiled from source but had problems with ./configure as normal, I had to point to the paths of tcl/tk, if anyone has any problem

```
./configure --with-tcl=/usr/lib/tcl8.5 --with-tk=/usr/lib/tk8.5
```

---

