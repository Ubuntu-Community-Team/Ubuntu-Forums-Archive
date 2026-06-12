---
title: "Upgrading to versions not in the repository"
date: 2006-02-26
forum: Programming Talk
---

### Post by jackrabbit123 on 2006-02-26
I need to upgrade my version of HAL to 0.5.5 or higher.  The version of HAL currently in the repository is 0.5.3.  I was planning on just removing HAL from the package manager and compiling and installing my own.  The only things that I'm worried about is dependancy checks by the package manager.  If I later install a package that requires HAL is will reinstall HAL 0.5.3 over my newer version and break stuff.  How can I upgrade without causing dependancy problems from other packages?

---

### Post by MartinG on 2006-02-26
If you install checkinstall, and for the final stage of the installation replace the command "sudo make install" with "sudo checkinstall", then the program will build and install a deb package.  This means it will be registered in the apt database and won't be overwritten by an older version.

---

### Post by jackrabbit123 on 2006-02-26
I considered that but will that solve the dependancy problem?  Meaning, will this package be considered when looking for the HAL dependancy?

---

### Post by MartinG on 2006-02-26
[QUOTE=jackrabbit123]I considered that but will that solve the dependancy problem?  Meaning, will this package be considered when looking for the HAL dependancy?[/QUOTE]AFAIK, yes.  That's (part of) the point of the apt database.  Your new package created by checkinstall will be treated as if it came from the repositories, and will replace (not sit alongside) the currently installed one just like any downloaded upgrade, and thereafter apt-get upgrade will only replace it if it finds a newer version. If you check synaptic you will find it in the section "installed (local or obsolete)".

Once installed any apps requiring HAL will use its libraries without question.  The only snag will be if something asks for an exact version, rather than using >= or <= for dependencies.  This can happen, but not very often, and rarely with "mainstream" apps.

PS.  One thing you might find is that you will need to upgrade other packages to maintain consistency.  After the install check for broken packages, e.g. in synaptic.

---

