---
title: "How to setup debian/control to force updating a library?"
date: 2012-12-16
forum: Packaging and Compiling Programs
---

### Post by YannBuntu on 2012-12-16
**This question is aimed at PPA/packages maintainers.**

I have a PPA with 2 packages:

[LIST]
[*]mypackage (currently version 1~ppa1~quantal)
[*]    mypackagelib (currently version 1~ppa1~quantal)
[/LIST]

Currently, the control file of mypackage has:

```
Depends: mypackagelib
```

I want to update the 2 packages to version '2' (mypackage version 2 and mypackagelib version 2).

How can I make sure that 'mypackagelib' will also be updated when the user updates 'mypackage' ?

FYI, changing the 'Depends' field to:

```
Depends: mypackagelib (>= 2)
```

does NOT work, and returns the following error:

```
mypackage : Depends: mypackagelib (>= 2) but mypackagelib-2~ppa1~quantal is to be installed
```



Please see [http://askubuntu.com/questions/229725/how-to-setup-debian-control-to-force-updating-a-library](http://askubuntu.com/questions/229725/how-to-setup-debian-control-to-force-updating-a-library)

---

### Post by mc4man on 2012-12-16
in the control file using
Package: boot-repair
Architecture: all
Depends: boot-sav (>= ${binary:Version}),
 ${misc:Depends}
....ect
seems to work fine (or Depends: boot-sav (= ${binary:Version}),

Also don't know why not upping the version in /debian/changelog like
 3.198 or whatever

---

### Post by YannBuntu on 2012-12-17
Thanks Mcman for having looked at this.

The problem is the '~' of the ppa version.
See [http://askubuntu.com/questions/229725/how-to-setup-debian-control-to-force-updating-a-library](http://askubuntu.com/questions/229725/how-to-setup-debian-control-to-force-updating-a-library)

Depends: boot-sav (>= ${binary:Version}) is a good workaround.

[SOLVED]

---

### Post by Bachstelze on 2012-12-17
Just to clarify: the problem basically is that when comparing package verison numbers, X~Y is considered LOWER than X. This is why you get

```
mypackage : Depends: mypackagelib (>= 2) but mypackagelib-2~ppa1~quantal is to be installed
```

because you want >= 2, but what you have is 2~something, which is < 2.

---

### Post by mc4man on 2012-12-17
Well good it's back - when i decide to set up my new laptop (lenovo 580y, win7, some interesting partitioning, hdd + a cache ssd) I figure I'll likely end up needing your app

---

