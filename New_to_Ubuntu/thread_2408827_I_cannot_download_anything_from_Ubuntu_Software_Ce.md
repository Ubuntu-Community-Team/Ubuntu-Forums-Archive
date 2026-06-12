---
title: "I cannot download anything from Ubuntu Software Center nor update packages.."
date: 2018-12-23
forum: New to Ubuntu
---

### Post by poethic on 2018-12-23
Hi Community! Complete neophyte in linux here, and I might need some guidance. I've installed a fresh 14.04 ubuntu release on dual boot with windows 7, and I can't seem to download anything from the Ubuntu Software Center: "failed to download repository information - check your internet connection" is the message I get, although here I am browsing the web normally via Firefox. I tried the sudo apt-get update, yet I receive: 
```
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe Translation-en
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I tried to go to softwares and updates, but I only find  Canonical Partners, Canonical Partners (source code), Independent and Independent (source code) in the Other softwares section; the server is set in Main.

Any clue about the issue? Thank in advance.

---

### Post by howefield on 2018-12-23
What is the output of..

```
cat /etc/*-release
```

Utopic repositories are part of the defunct Ubuntu 14.10 release.

---

### Post by poethic on 2018-12-23
Hi there, kind soul! it's as follows:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"
NAME="Ubuntu"
VERSION="14.10 (Utopic Unicorn)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.10"
VERSION_ID="14.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

---

### Post by howefield on 2018-12-23
Appears that you have installed Ubuntu 14.10 which has long since reached end of life and not the Long Term Support release 14.04 that you thought you had. Even at that, 14.04 goes end of life next April and is therefore of doubtful value for new installs.

Current Long Term Supports releases would be 16.04 or 18.04.

---

### Post by poethic on 2018-12-23
Yup, my bad, I just noticed it is 14.10. Even then, is there any possible fix for this issue?

---

### Post by howefield on 2018-12-23
> **poethic said:**
> ... Even then, is there any possible fix for this issue?

Well, depends on what you consider a fix. You could point your sources.list to the archived Utopic repositories however that means using old software that has not had security fixes for the last few years. Not very desirable but possible. The real fix is to install a currently supported release.

---

### Post by poethic on 2018-12-23
Ok, I'll follow your advice. I have an I3 with 4Go ram; will it run 18.04? is 16.04 enough? I mainly need linux for game dev and a bit of learning-linux-for-its-own-sake; so what do you suggest?

---

### Post by howefield on 2018-12-23
Both 16.04 and 18.04 should run fine on an i3 and 4GB of ram, I'd suggest 18.04, apart from 18.04 obviously being newer the main difference between the two is the desktop environment with 16.04 running the Unity environment and 18.04 a modified version of gnome. Try live media of both to make sure all hardware works and then make a choice.

---

### Post by poethic on 2018-12-23
Fine then. Thanks for your help mate, have a nice day!

---

