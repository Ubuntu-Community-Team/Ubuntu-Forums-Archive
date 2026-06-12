---
title: "HOWTO Install the VMWare player with dpkg"
date: 2006-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by ijanos on 2006-01-03
Download the .rpm installer from the VMware player use alien with --scripts parameter and then run the vmware-config.pl as root:
```
$ sudo alien VMware-player-1.0.1-19317.i386.rpm --scripts
$ sudo vmware-config.pl
```
You can install the VMware player from the .tgz of course, but IMHO the smarter way is to use the package manager to make easy the uninstall for example.

---

### Post by ashrack on 2006-04-16
I did what U said. but I got .DEB file
dont have a clue where did U get
"sudo vmware-config.pl:

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=ashrack]I did what U said. but I got .DEB file
dont have a clue where did U get
"sudo vmware-config.pl:[/QUOTE]
Your supposed to get the .deb file so you can install it... '_' and I don't use VMWare player but the vmware-config is to config vmware player.

---

### Post by Alexander Grundner on 2006-05-05
[QUOTE=ijanos]Download the .rpm installer from the VMware player use alien with --scripts parameter and then run the vmware-config.pl as root:
```
$ sudo alien VMware-player-1.0.1-19317.i386.rpm --scripts
```[/QUOTE]
I'm a little lost here. When you use alien, Ubuntu will create .deb file in your home directory. 

When I try using **$ sudo apt-get install vmwareplayer_1.0.1-19318_i386.deb** I get the following error:
```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package
```

When I try using **$ sudo dpkg -i vmwareplayer_1.0.1-19318_i386.deb** I get this error:
```

(Reading database ... 87441 files and directories currently installed.)
Unpacking vmwareplayer (from vmwareplayer_1.0.1-19318_i386.deb) ...

dpkg: error processing vmwareplayer_1.0.1-19318_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 25: [: abort-install: integer expression expected
Errors were encountered while processing:
 vmwareplayer_1.0.1-19318_i386.deb
```
Where am I going wrong?

---

