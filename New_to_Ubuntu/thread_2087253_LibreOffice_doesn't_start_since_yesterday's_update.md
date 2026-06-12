---
title: "LibreOffice doesn't start since yesterday's update on Ubuntu 12.10"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by Houmie on 2012-11-23
Yesterday was a major update to LibreOffice on Ubuntu 12.10.  After that update, I am no longer able to start LibreOffice at all.

Any idea what I could do?

Many Thanks,

---

### Post by handaxe on 2012-11-23
You can start libreoffice in a terminal with "loffice" or writer with "lowriter". That should give any error message.

And what version? Is this an update from a PPA? If so, there was a prolem with the install of v. 1.4 from a PPA that required a force-overwrite to solve.

---

### Post by Houmie on 2012-11-23
ah thanks, It something with java:

```
[Java framework] Error in function createSettingsDocument (elements.cxx).
javaldx failed! 
Warning: failed to read path from javaldx
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
```


I dont use libre office from any ppa.  The one that comes with ubuntu 12.10.

I am using latest Java over webupdate8 ppa though

---

### Post by handaxe on 2012-11-23
Revert java to stock version and test then.

HA

---

### Post by Houmie on 2012-11-27
> **handaxe said:**
> Revert java to stock version and test then.

HA

I don't think the latest Java is the problem. I have used it all the time instead of the OpenJava and it worked. Only until the latest update of LibreOffice that am getting this problem.

---

### Post by handaxe on 2012-11-27
L-O  is very widely used. If there is no bug report on Launchpad (I have'nt looked) I  would suspect a local problem on your side. You can try 
L-O from a devs PPA, now at v. 4 alpha.

[http://ppa.launchpad.net/bjoern-michaelsen/libreoffice-quantaltest-20120601/ubuntu](http://ppa.launchpad.net/bjoern-michaelsen/libreoffice-quantaltest-20120601/ubuntu)

---

### Post by Hagar Delest on 2012-11-29
You can also try to install from the .debs of their websites and/or install Apache OpenOffice. Installing with the .debs directly allows the installation of both applications. See [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Houmie on 2012-12-01
Guys,

I downloaded the latest Deb version from their website. Uninstalled everything and installed theirs as the readme instructions.

It all worked, however I still cant start it. It doesn't find my java.

Bit java is installed:

```
java version "1.7.0_09"
Java(TM) SE Runtime Environment (build 1.7.0_09-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.5-b02, mixed mode)

```

What could have gone wrong?

So if I choose the icons from dash and run it, it fails and sends a crash report to Ubuntu.

And I can't run it from terminal neither:

```
/usr/lib/libreoffice/program/soffice: 181: exec: /usr/lib/libreoffice/program/oosplash: not found
```

because of the uninstall and new install. darn, please don;t tell me I have to reinstall Ubuntu :|

---

### Post by zombifier25 on 2012-12-01
The .deb from LibreOffice.org installs LibreOffice to a different directory. I don't know where it is though, so just launch it from the Dash.

About the Java problem, try removing ~/.config/libreoffice completely, and launch again.

---

### Post by Hagar Delest on 2012-12-01
When installed from the debs, it's located in /opt.

Try to [reset your OpenOffice user profile](http://forum.openoffice.org/en/forum/viewtopic.php?p=58403#p58403).

---

### Post by Houmie on 2012-12-03
> **zombifier25 said:**
> 

About the Java problem, try removing ~/.config/libreoffice completely, and launch again.

Hey that worked. Many thanks. At least I can start them from Dash again.

---

