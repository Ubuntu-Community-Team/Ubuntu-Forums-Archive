---
title: "source installation"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by chaying on 2012-10-07
Hi

Does anyone know how to make ubuntu aware of an installation from sources ?

Thank you

---

### Post by chaying on 2012-10-07
I auto reply :

Usage: apt-mark [options] {auto|manual} pkg1 [pkg2 ...]

apt-mark is a simple command line interface for marking packages
as manual or automatical installed. It can also list marks.

Commands:
   auto - Mark the given packages as automatically installed
   manual - Mark the given packages as manually installed

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -s  No-act. Just prints what would be done.
  -f  read/write auto/manual marking in the given file
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-mark(8) and apt.conf(5) manual pages for more information.

Thank you :)

---

### Post by chaying on 2012-10-07
I re auto ask because it doesn't seem to work when source installation, just with packages. :(

---

### Post by oldos2er on 2012-10-07
Have you tried installing your source with [checkinstall]("https://help.ubuntu.com/community/CheckInstall")? I am unfamiliar with apt-mark, but it might work.

> Does anyone know how to make ubuntu aware of an installation from sources ?

It would help if you would give some details such as which software you compiled and installed, and any terminal output from *./configure*, *make*, or *sudo make install*

---

### Post by chaying on 2012-10-11
Hi

Very thanks for the tip ! :)
It works fine, it even builds a deb package from the sources : just great !

This was to install the last version of samba, I'm still dealing with a dependency issue (libwbclient0) but it should just do.

Thanks again. ;)

PS : apt-mark can't work as it tests if the package is installed before applying mark, the dog bites in own tail..

---

