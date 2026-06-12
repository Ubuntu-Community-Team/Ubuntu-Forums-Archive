---
title: "Trying to install m64py but I have dependency issues."
date: 2012-12-20
forum: New to Ubuntu
---

### Post by HunterDX77M on 2012-12-20
I was trying to install m64py as GUI for mupen64plus by using the .deb package I got from their website. But, it gave me an error about dependencies, and I am not sure how to fix such errors (n00b).

```
(Reading database ... 728955 files and directories currently installed.)
Preparing to replace m64py 0.1.0-2 (using m64py_0.1.0-2_all.deb) ...
Unpacking replacement m64py ...
dpkg: dependency problems prevent configuration of m64py:
 m64py depends on python-qt4-gl; however:
  Package python-qt4-gl is not installed.
 m64py depends on libsdl1.2-dev; however:
  Package libsdl1.2-dev is not installed.
dpkg: error processing m64py (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Errors were encountered while processing:
 m64py

```

I tried
```
sudo apt-get install python-qt4-gl
```

But that just gave me more dependencies-related errors. How can I fix this? I don't really know anything about dependencies.

---

### Post by SirGuineaPig on 2013-07-04
Download and install them via Synaptic Package Manager. It can be found on Ubuntu Software center.

---

### Post by su:bhatta on 2013-07-04
I was also compiling a application and got dependency issues.. i found out, the hard way, many applications require development packages.. that is, if there is 

python-qt4-gl-**dev **u will hav to get that installed...

Also:you can use the apt-cache search to find likely candidates for the missing packages, and you can install and use the apt-file utility...

---

