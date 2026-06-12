---
title: "Some issues with Ubuntu 13.10 on Android"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by MetroidJunkie2008 on 2013-11-01
I used "Complete Linux Installer" to get Ubuntu 13.10 onto Android, using the small image. It installed just fine and I managed to get it running into the desktop but I'm having some problems getting things installing. 

It started with missing dependencies then, when I tried to use the update, it gave me failed to fetch and 404 errors.  I read to use software source as a fix but it doesn't appear to have been included in it and "software-source" isn't recognized as a command.

A sample of the terminal issues:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-armhf/Packages)  404  Not Found [IP: (withheld)]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@localhost:/#"

---

