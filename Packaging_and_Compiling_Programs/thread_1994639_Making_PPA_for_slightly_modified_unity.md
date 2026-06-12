---
title: "Making PPA for slightly modified unity"
date: 2012-06-03
forum: Packaging and Compiling Programs
---

### Post by number2 on 2012-06-03
I'm trying to add option to unity to always show menu and buttons (LP [#789979]("https://bugs.launchpad.net/unity/+bug/789979")). I made changes to unityshell code, created deb packages, installed them on my machine, everything works fine. Link to code for curious: [https://code.launchpad.net/~anton0/ubuntu/precise/unity/lp-789979](https://code.launchpad.net/~anton0/ubuntu/precise/unity/lp-789979)

Now I want to create PPA, so that users can add it to their sources list, than make apt-get update/upgrade and start using my version of unityshell. Here it is: [https://launchpad.net/~anton0/+archive/unity](https://launchpad.net/~anton0/+archive/unity).

Unfortunately after adding this ppa system don't upgrade from my current unity version (5.12-0ubuntu1) to version from ppa (5.12-0ubuntu2~ppa1). What am I doing wrong?

---

### Post by number2 on 2012-06-03
It works now. For some reason had to wait until i386 package is built to install amd64 version.

---

