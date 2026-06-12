---
title: "[SOLVED] Installing (new) software recommended way"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by guy.dillen on 2014-01-04
What is the recommended way of installing software on Ubuntu 12.04 (Desktop):
- using apt-get or
- e.g. for MySQL downloading the package from the dev.mysql.com site and [B]dpkg -i mysql-*MVER*-*DVER*-*CPU*.deb ?
Thanks.[/B]

---

### Post by Bucky Ball on 2014-01-04
Software Centre, Synaptics or Terminal. Then you know they are most compatible with your release. 

Generally it is if you want a very new version of something you might install from a .deb (or if not in repos). Using a PPA for your release is probably preferable if not available in repos or you want newer/newest version of app.

---

### Post by guy.dillen on 2014-01-04
Thanks for the explanation. Sorry but what do you mean with **PPA**?

---

### Post by Bucky Ball on 2014-01-04
Have a look here:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

PPAs (Personal Package Archive) are added to your software sources so you can install software from the PPA via apt-get or Synaptics. The PPA may include newer versions of software or software not available in the regular repos (which are the Ubuntu PPAs basically), like Boot Repair in the example above. ;)

---

### Post by guy.dillen on 2014-01-04
OK thanks. I'm no yet aware with Ubuntu abbreviations ;)

---

