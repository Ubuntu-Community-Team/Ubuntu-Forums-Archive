---
title: "LibreOffice"
date: 2014-10-05
forum: New to Ubuntu
---

### Post by kyronlaube on 2014-10-05
Soo Hi :) I'm new to ubuntu forums and I have a question haha 

LibreOffice comes pre-installed, with writer, draw, calc and impress, soo, in order to install de metapackage (which comes with all of them) I have to uninstall the pre-installed ones to prevent any kind of errors?!

---

### Post by grahammechanical on 2014-10-05
What do you think a meta package is?

> [COLOR=#333333][FONT=Ubuntu]One of the handy features of apt (the packaging system used by Ubuntu) is the use of metapackages. These packages do not contain actual software, they simply depend on other packages to be installed. This setup allows entire sets of software to be installed by selecting only the appropriate metapackage. [/FONT][/COLOR]

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

In Ubuntu we do not have the Libreoffice meta package installed because we do not have the full set of Libreoffice components. In fact the only Libreoffice component not installed by default is Base, the database component. We can install that separately by using the Software Center.

If the Libreoffice meta package was installed as part of the default install of Ubuntu then it would also pull in all the Libreoffice components including Base. I guess that method is not used in order to reduce the size of the Ubuntu ISO image for the Base component is well over 100MB in size.

My guess is that if you installed the Libreoffice Meta package all it would do was to install Base. Once all the components in a set of software have been installed then we can usually remove the meta package without removing the set of software.

Regards.

---

### Post by deadflowr on 2014-10-05
Edit: This for post #1
No. It'll just add the other packages to the list of already installed packages.

Best to make sure that your overall system is fully up-to-date, though So that the new packages are upsetting to what packages are already installed.
(This is where people get in package trouble, because the new packages of are a newer version then the ones already installed and it causes the system a bunch of confusion)

For fun, you could run a simulation to see if any problems show up.
```
sudo apt-get install -s libreoffice
```
(-s, or --simulate = just that)

---

### Post by kyronlaube on 2014-10-05
haha thanks dude (:

---

### Post by sandyd on 2014-10-05
Hi, please mark this thread as solved (Thread Tools -> Mark As Solved) if you have found a solution.

Thanks!

---

