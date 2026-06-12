---
title: "Lintian errors with Ubuntu 12.10"
date: 2013-02-11
forum: Packaging and Compiling Programs
---

### Post by fallenshadow on 2013-02-11
Hi all,

I packaged my program for Ubuntu 12.04 but the same package failed to install due to a dependency problem which has since been fixed. However, other lintian errors persist when I try to install.

This one is the most common:

> wrong-file-owner-uid-or-gid 1000/1000

How do I go about fixing this? :/

---

### Post by fallenshadow on 2013-02-13
Anyone ever come across this? :?

---

### Post by MadCow108 on 2013-02-13
well your files have the wrong uid or gid
there is only a small range which is allowed:
[http://lintian.debian.org/tags/wrong-file-owner-uid-or-gid.html](http://lintian.debian.org/tags/wrong-file-owner-uid-or-gid.html)

possibly you are missing a dh_fixperms call

---

### Post by fallenshadow on 2013-02-18
How do I use dh_fixperms?

I tried:
> dh_fixperms MyTopLevelDirectory

and I got this:

> dh_fixperms: cannot read debian/control: No such file or directory

What am I doing wrong here?

---

### Post by MadCow108 on 2013-02-18
dh_fixperms is run during the package build from the top source directory
it is included in the standard sequencers so unless you have a really manual or old rules file it may already be run, I don't know if it fixes uid's too, if not you have to fix it yourself (with chmod/chown).

---

### Post by Malsasa on 2013-02-19
Maybe you must run dh_fixperms in directory which is you can see debian/ folder there. 

I have mirrorred Lintian Tags pages (whole) and it helps me to fixing any error reported by Lintian. So, i just open my chromium and ctrl+f > paste exactly the error message, and exactly the page title found :) Maybe you can follow same way with WebHTTRACK. Install it from repo :)

---

### Post by MadCow108 on 2013-02-19
> **Malsasa said:**
> Maybe you must run dh_fixperms in directory which is you can see debian/ folder there. 

I have mirrorred Lintian Tags pages (whole) and it helps me to fixing any error reported by Lintian. So, i just open my chromium and ctrl+f > paste exactly the error message, and exactly the page title found :) Maybe you can follow same way with WebHTTRACK. Install it from repo :)

you can just use lintian-info:
```
lintian-info --tags wrong-file-owner-uid-or-gid
```

---

### Post by Malsasa on 2013-02-19
> **MadCow108 said:**
> you can just use lintian-info:
```
lintian-info --tags wrong-file-owner-uid-or-gid
```
Wow i don't know it before... Thank you for info...

---

### Post by fallenshadow on 2013-02-24
Well the UID/GID is 1000 which is my own user. dh_fixperms didn't do anything for me.

What exactly should I do to solve this? Make a new user/group with a correct value?

Also why did they make .deb packaging more difficult? It was fine in 12.04 but not in 12.10. :(

---

### Post by schragge on 2013-02-26
UID/GID=1000 is definitely wrong: pretty much all the files in your package should be owned by root.

The info you've provided is not enough to give any other help.
Please post the output of your *debian/rules* here.

---

### Post by fallenshadow on 2013-02-27
I have changed the GID to root.

Is there a command to recursively change the UID of the folder? :D

---

### Post by schragge on 2013-02-27
```

chown -R root /path/to/folder

```

BTW,
```

chown -R root: /path/to/folder

``` changes both UID and GID.

---

### Post by fallenshadow on 2013-02-27
Thanks! Sorted now! :)

---

