---
title: "Problems upgrading PHP"
date: 2016-11-03
forum: New to Ubuntu
---

### Post by Mic6 on 2016-11-03
I am currently running Ubuntu 10.04.4 with php 5.3.2 and would like to upgrade php to version 5.5

When I try to run  sudo apt-get update
I keep getting errors like 
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
and
[http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  404  Not Found [IP: 91.189.88.161 80]

Same type of errors when I then try a agp-get upgrade

My /etc/apt/sources.list are using
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted

Any suggestions on how I can upgrade my php version?

---

### Post by QIII on 2016-11-03
Hello!

10.04 is long past End Of Life (EOL) and the repos have been moved.  That explains the 404 errors.  10.04 is no longer supported.

Before you spend the time trying anything, I would recommend upgrading to or installing a supported release.

---

### Post by Mic6 on 2016-11-04
And to much trouble upgrading since it's a pretty old server anyway... guess its time to move on to another solution.

---

