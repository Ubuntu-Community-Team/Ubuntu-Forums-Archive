---
title: "Space escape character in Debian Makefiles"
date: 2012-06-07
forum: Packaging and Compiling Programs
---

### Post by AZorin on 2012-06-07
I'm currently trying to upload a package onto Launchpad's PPA service but I'm having problems with a path name which includes a space character. I'm trying to make a file install into a directory with a space character in it. The following is an example of the kind of directory I'm trying to install files into using the Makefile:
(/usr/share/themes/Example Directory/gtk-3.0)
I've tried the \\ escape character and have tried putting the entire path name in single quotes ('/usr/share/themes/Example Directory/gtk-3.0') in the Makefile and debian/install file in the source of the package, but it's still failing to build on Launchpad's servers.
Does anyone know any escape character that I can use in order to make Launchpad successfully build the package and make it work when I'm installing the package to my computer or are spaces in directories not supported by the Debian package system?

Thanks in advance!

---

### Post by MadCow108 on 2012-06-07
you can't install files with space with dh_install (= debian/*install files)
you have to rename/install them explicitly in debian/rules with *install*, *mv* or *cp*

e.g. with dh tiny rules:

```

override_dh_install
     dh_install
     install -m 644 "fi le" "debian/tmp/usr/share/fi_le"

```

---

