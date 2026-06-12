---
title: "arqiver doesn't want to work or be removed"
date: 2022-12-10
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2022-12-10
zipped programs, system said i needed arqiver to open. then arqiver program said it needed 7z to work.  7zip wont download an unzipped program.  garbage program right.  i go to remove arqiver, it's in my installed programs list, but when i try to remove the program it says no packages.  ya know i just want to install imgburn, that crap snap store that still doesn't work. is causing me nothing but problems. wonder if i'm going back to 18 to get this os to work propperly.  any suggestions?

---

### Post by TheFu on 2022-12-10
I'm guessing here. Don't know anything about arqiver - never heard of it before.

There are 2 different packaging systems on Ubuntu since around 2020.

APT - which is used for all the dependencies and .deb packages.

SNAPS - which is being pushed by Canonical as all-in-one, run-anywhere, packages, but with some constraints for which areas of the file system the running programs (from snap packages) can see, touch, and which other programs they can interface to.

Depending on which GUI you use, you can see 1 or the other or both sets of packages. The default "Ubuntu Software" shows both, which is confusing.

So, if the arqiver installed is a snap package, that could explain much of what has been described.  Open a terminal and run:
```
$ snap list
```
to see the list of installed, bloated, snap packages on the system.

BTW, the leading '$' isn't entered. It is the Unix method so those that a normal userid should be used for the command.  To show that sudo or root should be used, it would be a '#' character rather than the '$' to denote that elevated level is needed.  Common little hints for Unix/Linux commands.

BTW, if you didn't mispell arqiver, then the following says it isn't part of the normal Canonical APT software repos:
```
$ apt search arqiver
Sorting... Done
Full Text Search... Done

```
Nothing found.  That makes it more likely to be a snap.

Or you could have gone out and found the source code, followed the installation instructions for it and installed it manually. Then it wouldn't be seen by either APT or Snap package management systems.

---

### Post by Impavidus on 2022-12-10
```
apt search arqiver
Sorting... Done
Full Text Search... Done
arqiver/jammy 0.9.0-1 amd64
  Simple Qt5 archive manager; front-end for libarchive, gzip and 7z.

```It's available as a deb on 22.04 and 22.10. Just a GUI front-end to some archiving and compression tools, so not required, but maybe convenient for some.

---

