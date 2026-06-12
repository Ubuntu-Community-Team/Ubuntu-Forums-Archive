---
title: "[libusb]package manager and versions"
date: 2005-01-12
forum: Repositories &amp; Backports
---

### Post by Wim Sturkenboom on 2005-01-12
In Synaptic, I have a package libusb-0.1.4. Installed version and latest version are both displayed as version 1:0.1.8-11.
Further, if you query the properties of the packages, tab *installed files*, it lists directories with 0-1-4 in the name.
So which version is it? The version of the 'package name' or the version of the 'installed version'?

I need this info as I'm trying to get my scanner to work (HP3400C) and that requires libusb-0.1.5 and compiling fails with references to an include file that can't be found. That include file is indeed in a different directory and next the functions that are used in the c-code are not prototyped in the current include file. This might indicate an incorrect version.

If I have to upgrade the package, how to go?
1)
Removing the package does not seem a good idea, as a lot of other packages depend on it (directly or indirectly). One of them being ubuntu-desktop (sounds dangerous to remove that).
2)
Remove all the files manually and replace with newly compiled version
3)
Just copy the new ones over to the correct locations?
4)
Just add the new ones to new directories?

If I have to downgrade, what are the implications?

PS My Ubuntu machines don't have access to the internet for various reasons, so I have to download using other machines.

---

