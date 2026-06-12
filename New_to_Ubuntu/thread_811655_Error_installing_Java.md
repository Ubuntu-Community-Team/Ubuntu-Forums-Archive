---
title: "Error installing Java"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Cront on 2008-05-29
Hi guys,

New to Linux and I'm trying to install Java but I get the following error

sudo rpm -iv jre-6u6-linux-i586.rpm
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_06-fcs.i586
	/bin/cat is needed by jre-1.6.0_06-fcs.i586
	/bin/cp is needed by jre-1.6.0_06-fcs.i586
	/bin/gawk is needed by jre-1.6.0_06-fcs.i586
	/bin/grep is needed by jre-1.6.0_06-fcs.i586
	/bin/ln is needed by jre-1.6.0_06-fcs.i586
	/bin/ls is needed by jre-1.6.0_06-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_06-fcs.i586
	/bin/mv is needed by jre-1.6.0_06-fcs.i586
	/bin/pwd is needed by jre-1.6.0_06-fcs.i586
	/bin/rm is needed by jre-1.6.0_06-fcs.i586
	/bin/sed is needed by jre-1.6.0_06-fcs.i586
	/bin/sort is needed by jre-1.6.0_06-fcs.i586
	/bin/touch is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_06-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_06-fcs.i586
	/bin/sh is needed by jre-1.6.0_06-fcs.i586

---

### Post by quelx on 2008-05-29
try the java from Ubuntu ```
sudo apt-get install sun-java6-jre
```

---

### Post by tigerplug on 2008-05-29
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

That should do the trick for ya! ;)

---

### Post by FuturePilot on 2008-05-29
Ubuntu does not use RPM. It uses deb instead since it is based on Debian. The easiest way to install Java is to
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by Cront on 2008-05-29
Thanks guys, worked just fine

---

### Post by tigerplug on 2008-05-29
> **Cront said:**
> Thanks guys, worked just fine


No problem!

---

### Post by sumanc on 2008-06-12
In Hardy I get the following error: :(

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

Any suggestion?

---

### Post by sumanc on 2008-06-12
> **FuturePilot said:**
> Ubuntu does not use RPM. It uses deb instead since it is based on Debian. The easiest way to install Java is to
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```


Yes, but the binary installation shows the same error as well. :confused:

---

