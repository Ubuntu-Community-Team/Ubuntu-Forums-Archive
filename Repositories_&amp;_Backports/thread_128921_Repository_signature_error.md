---
title: "Repository signature error"
date: 2006-02-12
forum: Repositories &amp; Backports
---

### Post by Barrakketh on 2006-02-12
Specifically, I'm getting a bad signature error for security.ubuntu.com.

```
$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:3 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Get:4 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:6 [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/freenx Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Fetched 192B in 23s (8B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Running apt-get update again did not correct those problems :p

Any ideas as to what the problem is?  It's been working fine since it [Kubuntu] was installed and I never have had a problem with it.

---

### Post by Turin Turambar on 2006-02-12
I have the same problem as well. Possibly some temporary error.

---

### Post by the_duce on 2006-02-12
I had the same problem which has been [solved.]("http://http://ubuntuforums.org/showthread.php?t=128602")

---

### Post by Turin Turambar on 2006-02-12
Hahaha! The duce, your link is taking straight to hell - right on Microsoft official page. ::mrgreen:

---

### Post by aysiu on 2006-02-12
There are two https in there: [http://http//ubuntuforums.org/showthread.php?t=128602](http://http//ubuntuforums.org/showthread.php?t=128602)

Use this instead:
[http://ubuntuforums.org/showthread.php?t=128602](http://ubuntuforums.org/showthread.php?t=128602)

---

### Post by Barrakketh on 2006-02-12
[QUOTE=the_duce]I had the same problem which has been [solved.]("http://http://ubuntuforums.org/showthread.php?t=128602")[/QUOTE]
That did the trick.  I'm not used to things breaking without me touching them.  That's Windows' department :D

Thanks.

---

