---
title: "Security Signature"
date: 2006-02-28
forum: Repositories &amp; Backports
---

### Post by obe1kenobi on 2006-02-28
Maybe you guys can help wih this.  Every time I do a sudo apt-get update or the reload in the update manager I get this:
```

~$ sudo apt-get update
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:5 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Get:7 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release [702B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Fetched 896B in 11s (76B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

How do I get the right signature?

---

### Post by Gcool on 2006-02-28
[http://ubuntuforums.org/showthread.php?t=128602](http://ubuntuforums.org/showthread.php?t=128602)

Follow the instructions on the second post from the bottom (Agent)

---

### Post by obe1kenobi on 2006-02-28
Thanks \\:D/

---

