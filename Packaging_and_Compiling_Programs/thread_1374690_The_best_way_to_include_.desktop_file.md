---
title: "The best way to include .desktop file?"
date: 2010-01-07
forum: Packaging and Compiling Programs
---

### Post by Umang on 2010-01-07
Hi,
I have a .deb package that I'm trying to get a .desktop file for and am not sure about how to go about doing this.

Quickly, before I continue, the source code and debian directories are on lp. You most probably won't need this to help me. To get the source:
```
$ bzr branch lp:pynagram
$ bzr branch lp:~umang/pynagram/debian
```

I have a pynagram.desktop file that I would like installed along with the rest of the package. Here's my problem:

The .desktop file is meant only for Linux distributions. setup.py is for all OSs. Therefore, the .desktop file should not be installed by setup.py. Maintaining separate .desktop files for each OS will defeat the point of having distutils. How else I do get the .desktop file to install? Is there anything I need to add to the debian dir or my debian/rules file so that pynagram.desktop gets installed? (BTW: I haven't uploaded the .desktop file, so don't look for it as yet). 

Similarly, how do I copy my icons into the correct folder, without doing it in setup.py (because setup.py should not be installing those either).

Thanks

Umang

---

### Post by Umang on 2010-01-08
SOLVED. Thanks to guys at #debian-python.

If I put a debian/install file that contains
```
debian/filename.desktop /usr/share/applications
```
Then debian/filename.desktop installs as /usr/share/applications/filename.desktop 
I guess this solves my second problem too! :)

---

