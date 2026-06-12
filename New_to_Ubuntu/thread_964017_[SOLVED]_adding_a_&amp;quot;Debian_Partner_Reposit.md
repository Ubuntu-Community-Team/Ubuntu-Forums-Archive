---
title: "[SOLVED] adding a &amp;quot;Debian Partner Repository&amp;quot; to atp"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Dr Zin on 2008-10-30
I would like to add the debian repository to my atp. I via the GUI and it is crashing. I went to the command line and open the config file and there was its there.
```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
[COLOR=SeaGreen]deb http://ftp.debian.org/debian/pool/main[/COLOR]


```so what is missing and how other repositories added. or should i down load the tar ball or the .deb what would be the easiest way to do this.

for now i will remove the line so

---

### Post by Sef on 2008-10-30
Debian repositories are often not  compatible with Ubuntu and its derivatives.

---

### Post by Dr Zin on 2008-10-30
ok thanks

---

### Post by Dr Zin on 2008-10-30
but wait!! what about sites like this [Kubuntu Members - KDE 4 Repository]("https://launchpad.net/~kubuntu-members-kde4")I how  do i add other repositories. It copying pasting the code into the config file? :confused:

---

### Post by Vadi on 2008-11-03
To add a repository, you can go to System - Administration - Software Sources, click on the Third-Party Software tab, and then 'Add Source'. Paste the deb line into there.

Be aware that you should trust whatever is in that repository though. It very well can disguise core system packages as upgradable but really break them, and you'll get a broken ubuntu :/

---

