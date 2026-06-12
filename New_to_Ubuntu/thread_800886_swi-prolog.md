---
title: "swi-prolog"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by bhoomija on 2008-05-20
Hi,
I am new to using Ubuntu 8.04, and wanted to download SWI-Prolog 5.6.55 on my system with all the standard folders like pldoc and plunit loaded in it. How do I configure this?

---

### Post by nickmeet on 2008-06-01
The following steps work on my ubuntu 8.04 :

wget [http://gollem.science.uva.nl/cgi-bin/nph-download/SWI-Prolog/binaries/pl-5.6.55-322.i586.rpm]("http://gollem.science.uva.nl/cgi-bin/nph-download/SWI-Prolog/binaries/pl-5.6.55-322.i586.rpm")
sudo apt-get install alien
sudo alien -d pl-5.6.55-322.i586.rpm
sudo apt-get install swi-prolog # to get dependencies
sudo apt-get remove swi-prolog # do not sudo apt-get auto-remove before the next command takes place
sudo dpkg -i pl_5.6.55-322_i386.deb # the package is named pl

The package that i use is JPL which just like plDoc and plUnit is compiled and included in the rpm file. To use JPL, do the following :

open netbeans -> file -> new project -> java -> give name -> right click -> properties -> run
-> VM options -> -Djava.library.path="/usr/lib/pl-5.6.55/lib/i386-linux"

The dynamic library is /usr/lib/pl-5.6.55/lib/i386-linux/libjpl.so
The file that you have to import in your project is /usr/lib/pl-5.6.55/lib/jpl.jar
Although, I didn't use the location of the prolog file for the JPL package of swi-prolog, it is /usr/lib/pl-5.6.55/library/jpl.pl

plDoc or plUnit need extra configuration?

---

