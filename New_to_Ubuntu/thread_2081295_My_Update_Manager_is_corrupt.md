---
title: "My Update Manager is corrupt"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by kinggreg on 2012-11-06
After launching Update Manager I receive this:  An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'  Help

---

### Post by ibjsb4 on 2012-11-06
Thats a easy fix  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

And welcome to the forum

---

### Post by kinggreg on 2012-11-06
Fast, efficient, accurate..............solved. Thank you for your assistance

---

### Post by ibjsb4 on 2012-11-06
Just for future reference

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en)

---

