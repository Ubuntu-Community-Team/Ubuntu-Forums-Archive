---
title: "Control-C during aptitude run?!"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Sarah L on 2008-10-01
Hi guys,
Today I tried to install a package using aptitude.
But then I realized (while the package was installing) that one of the packages would conflict with a package that I had installed manually. Going through with the installation would have probably broken my program, so I pressed Control-C out of desperation:

```

:~$ sudo apt-get install stardict stardict-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  stardict stardict-plugin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 109kB of archives.
After this operation, 340kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe stardict 3.0.1-3 [13.2kB]
Get:2 http://us.archive.ubuntu.com hardy/universe stardict-plugin 3.0.1-3 [96.2kB]
Fetched 109kB in 0s (131kB/s)
Selecting previously deselected package stardict.
(Reading database ... E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I went back and installed just the package "stardict-plugins" via aptitude, not stardict (which was not desired). Doing an "aptitude search" shows me that the package stardict is not marked as installed, which is good.

But might this have screwed something up on my computer? Dpkg was trying to install some software using admin-level privileges... would suddenly sending it SIGINT mess things up?

Help is appreciated!
Thanks,
Sarah

---

### Post by karlr42 on 2008-10-01
I can't see how. Good programs clean up when they get SIGTERM and then close.

---

### Post by Crafty Kisses on 2008-10-01
It shouldn't have done anything, the worse that might of happened is it broke a package somewhere, but if you're worried, run these commands:
```

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
That should solve any issues you may be experiencing with the packages.

---

### Post by Sarah L on 2008-10-01
My mistake: Control-C sends a SIGINT, not a SIGTERM as I previously stated. Sorry for any confusion.

---

