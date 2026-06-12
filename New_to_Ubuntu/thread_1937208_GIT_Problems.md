---
title: "GIT Problems"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by dkeeper09 on 2012-03-07
Hey everyone.

I am trying to install Sparkleshare on Ubuntu 10.04.

The problem is when it gets to git. The command line says:

The following packages have umet dependencies:
sparklshare: Depends: git (>= 1.7.1) but it is not installable
E: Broken Packages

But, when i run git --version it says the version is 1.7.9.3

I am not sure what to do next with this. Any help is greatly appreciated. Thank you very much.

---

### Post by jerrrys on 2012-03-08
Try to fix broken package

sudo apt-get install -f

---

