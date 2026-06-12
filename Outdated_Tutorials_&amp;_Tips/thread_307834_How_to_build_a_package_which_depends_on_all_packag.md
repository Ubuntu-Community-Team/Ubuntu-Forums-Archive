---
title: "How to build a package which depends on all packages installed on your system"
date: 2006-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Grishkin on 2006-11-27
**prerequests:** you need equivs package installed

[LIST=1]
[*]Create a template configuration file:
```
equivs-control meta
```
[*]Create a list of all packages installed on your system
```
aptitude search -F %p ~i | sed 's/$/,/' > packages.list
```
[*]Open the file 'packages.list' in gedit or any other text editor and replace all space symbols (' ') to void strings and all '\n' symbols (new string) to ','. Save the file.
[*]In any text editor open the file 'meta' from 1, add to it the contents of the file "packages.list" after the word "Depends:". Also change package name, version and description to appropriate.
[*]Build the package
```
equivs-build meta
```
[*]The package can be installed by
```
dpkg -i package_name
```
[/LIST]

---

### Post by gimfred on 2007-03-25
I'm not sure why you would want to do this. Could you explain?

---

### Post by Grishkin on 2007-03-25
To remember the package selection in the system (similar to packages like ubuntu-desktop, kubuntu-desktop, xubuntu-desktop).

---

### Post by xfile087 on 2007-03-25
Nice tip!

---

### Post by K.Mandla on 2007-03-29
Excellent. Thanks for this.

---

