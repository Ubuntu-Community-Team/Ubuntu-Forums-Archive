---
title: "dependencies"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Queram_Onog on 2013-10-14
While I'm here I might well ask about another thing:
There is this Salome, a CAE software, that I wanted to try out, installed one using the Software centre, piece of cake, played with the soft, got some tutorials, decided to  upgrade to newer version - not in Soft Centre, so installed manually - HELL, took me two evenings! Zillion of unresolved dependencies! G++ compiler and the likes - I bet the older version uses all of those too - so how come the installation process could not see/find them???

---

### Post by ian-weisser on 2013-10-14
Because you installed it manually.
If you install manually, then you must also install the dependencies manually.

That's why the Software Center and the Ubuntu Repositories are recommended. The packagers work hard to do all the dependency troubleshooting for you.

---

### Post by mastablasta on 2013-10-15
or find a PPA repository for latest version and install. or a .deb file.

---

### Post by Queram_Onog on 2013-10-15
Is it just me who comes across interesting softwares that are provided as .gz of binaries? No repository, no installer....

Anyway, the obvious academic question: I've a software v.5 installed via software centre and v.6 manually, bth with all dependencies, working just fine. When the time comes and I'll be installing v.7 manually / through soft centre will I have to install those dependencies again or not?

---

### Post by ian-weisser on 2013-10-15
If manually, it depends entirely upon what the dependencies are, what versions of those dependencies are required, and how many of those specific dependency versions are in the Ubuntu repositories.

You do know, of course, that packages get updated? software v.6 may be in the Ubuntu repositories in 13.10 or 14.04, and that upgrading will overwrite your package-installed v.5?
Will you then manually uninstall the manually installed v.6?
Or do you really need two or three different versions of the same software concurrently?

If there is demand for a more-recent version of software, community members are encouraged to package it and publish PPAs. Stable PPAs and backports make recent releases (and fixes) available to everyone.

You create your own installer for a .gz. A Debian installer is different from a Red Hat installer. Of course, an "installer" is quite old mindset, and expecting somebody else to create an installer for your specific system is quite unrealistic. Package management is much more than a simple install/uninstall mechanism. It's also security, bugfixes, reliability, and simplicity.

---

### Post by sandyd on 2013-10-16
> **ian-weisser said:**
> If manually, it depends entirely upon what the dependencies are, what versions of those dependencies are required, and how many of those specific dependency versions are in the Ubuntu repositories.

You do know, of course, that packages get updated? software v.6 may be in the Ubuntu repositories in 13.10 or 14.04, and that upgrading will overwrite your package-installed v.5?
Will you then manually uninstall the manually installed v.6?
Or do you really need two or three different versions of the same software concurrently?

If there is demand for a more-recent version of software, community members are encouraged to package it and publish PPAs. Stable PPAs and backports make recent releases (and fixes) available to everyone.

You create your own installer for a .gz. A Debian installer is different from a Red Hat installer. Of course, an "installer" is quite old mindset, and expecting somebody else to create an installer for your specific system is quite unrealistic. Package management is much more than a simple install/uninstall mechanism. It's also security, bugfixes, reliability, and simplicity.
the 6.x version is in debian experimental

backports can easily be made to ubuntu if someone feels the need

---

### Post by elliotn on 2013-10-16
basically to avoid headaches and heartaches just find a PPA or wait until there us an update in the software center

---

### Post by squakie on 2013-10-16
And if worse comes to worse........sudo apt-get build-dep <package-name>  can be your best friend, but this also assume that the repositories contain your software.

---

### Post by sandyd on 2013-10-17
Afaik, backporting and upgrading to 7.2 is broken until someone fixes a patch that makes it install in the right place -patch in 6.x is not compatible
[https://launchpad.net/~sandyd/+archive/salome-backports-updated/+build/5109461](https://launchpad.net/~sandyd/+archive/salome-backports-updated/+build/5109461)

---

