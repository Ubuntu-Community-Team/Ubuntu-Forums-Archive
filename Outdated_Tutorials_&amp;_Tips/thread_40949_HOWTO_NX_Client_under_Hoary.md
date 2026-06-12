---
title: "HOWTO: NX Client under Hoary"
date: 2005-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by drigloi on 2005-06-11
NX/FreeNX is the new Terminal Server system for Linux and Unix that is changing the shape of network computing (according to [www.nomachine.com)](www.nomachine.com)). Basically it's a stunningly fast tool for remote logins and remote graphical sessions.

The Hoary Backports project provides FreeNX server (the GPLed NX server) which works great. But currently the nxclient doesn't work from Backports. Here is a howto for setting up NoMachine's NX client under Hoary.

(I have "main" "restriced" "universe" "multiverse" "backports" repositories enabled described in latest ubuntuguide.org in /etc/apt/sources.list)

1. Grab the latest Debian package from here:
```
wget http://www.nomachine.com/download/nxclient/1.4.0/Debian/nxclient_1.4.0-91_i386.deb
```

2. Dpkg it:
[HTML]sudo dpkg -i nxclient_1.4.0-91_i386.deb[/HTML]

3. Grab dependencies:
[HTML]sudo apt-get install libstdc++2.10-glibc2.2[/HTML]

4. Create compatibility symlink for the Debian package:
[HTML]ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.2-2.so.3[/HTML]

5. Fire up NX Client from Applications/Internet

---

### Post by kiddyfurby on 2005-06-11
worked even without step 4!!

---

### Post by drigloi on 2005-06-11
On my Hoary I need step 4 otherwise I get a missing lib error from nxclient.

---

### Post by ubuntonista on 2005-09-12
The guide at the wiki has been updated recently to show how to change the sshd port, and also to cover installation of the client on Ubuntu systems:
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Thanks, everyone.

---

