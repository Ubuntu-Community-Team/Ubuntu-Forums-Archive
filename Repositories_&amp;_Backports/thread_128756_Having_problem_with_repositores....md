---
title: "Having problem with repositores..."
date: 2006-02-12
forum: Repositories &amp; Backports
---

### Post by mmcmonster on 2006-02-12
Things were working a month ago with the following sources.list:
```

deb http://us.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

#backports
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

# DigiKam
deb http://www.mpe.mpg.de/~ach/kubuntu/breezy ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/breezy ./

#Opera web browser
deb http://deb.opera.com/opera/ etch non-free

# Penguin Liberation Front
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

#Wine
deb http://wine.sourceforge.net/apt/ binary/

```

Now I get the following error when I do a 'sudo apt-get update'.
```

Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://wine.sourceforge.net binary/ Release.gpg
Get:2 http://us.archive.ubuntu.com breezy-security Release.gpg [189B]
Ign http://www.mpe.mpg.de ./ Release.gpg
Ign http://deb.opera.com etch Release.gpg
Get:3 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://www.mpe.mpg.de ./ Release
Ign http://deb.opera.com etch Release
Get:4 http://us.archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://wine.sourceforge.net binary/ Release
Ign http://www.mpe.mpg.de ./ Packages
Ign http://deb.opera.com etch/non-free Packages
Hit http://us.archive.ubuntu.com breezy Release
Hit http://us.archive.ubuntu.com breezy-security Release
Ign http://www.mpe.mpg.de ./ Sources
Ign http://wine.sourceforge.net binary/ Packages
Hit http://deb.opera.com etch/non-free Packages
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://www.mpe.mpg.de ./ Packages
Hit http://us.archive.ubuntu.com breezy-backports Release
Hit http://wine.sourceforge.net binary/ Packages
Hit http://www.mpe.mpg.de ./ Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-security/universe Packages
Hit http://us.archive.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy-security/restricted Packages
Hit http://us.archive.ubuntu.com breezy-security/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://packages.freecontrib.org breezy Release.gpg
Ign http://packages.freecontrib.org breezy Release
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Ign http://packages.freecontrib.org breezy/free Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://packages.freecontrib.org breezy/non-free Packages
Hit http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://packages.freecontrib.org breezy/free Sources
Ign http://packages.freecontrib.org breezy/non-free Sources
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://packages.freecontrib.org breezy/free Packages
Hit http://us.archive.ubuntu.com breezy-backports/restricted Packages
Get:5 http://us.archive.ubuntu.com breezy/main Packages [767kB]
Hit http://packages.freecontrib.org breezy/non-free Packages
Hit http://packages.freecontrib.org breezy/free Sources
99% [5 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/main Packages
  Sub-process gzip returned an error code (1)
Hit http://packages.freecontrib.org breezy/non-free Sources
Fetched 5B in 3s (1B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Is one of the main repositories down (us.archive.ubuntu.com), or was there a change made that I didn't pay attention to?

---

### Post by aysiu on 2006-02-12
Forget the US repositories.
See the first link of my signature.

---

### Post by mmcmonster on 2006-02-14
Solved by following the instructions in the following post. :-)

[http://www.ubuntuforums.org/showpost.php?p=727056&postcount=9](http://www.ubuntuforums.org/showpost.php?p=727056&postcount=9)

---

