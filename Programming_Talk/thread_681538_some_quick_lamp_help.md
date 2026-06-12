---
title: "some quick lamp help"
date: 2008-01-29
forum: Programming Talk
---

### Post by PfromD on 2008-01-29
Hi, I was going to set up a lamp environment using [_this guide_]("http://hostlibrary.com/installing_apache_mysql_php_on_linux") but ran into a problem with a missing 'make file' when time to complete the MySQL-step. I then found out that a command of ```
sudo tasksel install lamp-server
``` would do just what I wanted, and also keep me updated by automation. The question now is how I undo/uninstall the apache server applied in step 1 before running the sudo install.
And does this install include phpMyadmin or will I have to install that separately (available through apt-get/tasksel? )

---

### Post by zvacet on 2008-01-29
```
sudo apt-get --purge remove apache2
```

You can read [this](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

### Post by PfromD on 2008-01-29
just tried it, but apache weren't installed through apt-get but compiled according to the guide previously mentioned, so the reply is 
[quote=the terminal window]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libkernlib1 libgraflib1 libg2c0-dev libpacklib1 g77 libpawlib2 libxbae4
  libpawlib-lesstif3 lesstif2 cernlib-base g77-3.4 libgd2-xpm atlas3-base
  kxterm libgrafx11-1 libpacklib1-lesstif paw-common libg2c0 libgraphviz3
  libmathlib2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/quote]

The guide informs that after "#make install", apache is installed, but now I need to remove that install to avoid conflicts with the install to be done by  "sudo tasksel"

---

### Post by zvacet on 2008-01-29
Go to the folder from wich you compiled apache and type 

```
sudo make uninstall
```

---

### Post by PfromD on 2008-01-29
then terminal returns:
```
make: *** No rule to make target `uninstall'.  Stop.
```
.. do I need to run trough the configure initially again to make/run an uninstall?

---

### Post by PfromD on 2008-01-30
I assume it would be wrong of me to think that there's no chance of conflicts if just attempting to install the lamp-package without first removing the compiled version of apache that exists?
If it can clarify why [COLOR="Red"]sudo make uninstall[/COLOR] doesn't work I can post some feedback from the terminal from the process, but it's kind of lenghty

---

