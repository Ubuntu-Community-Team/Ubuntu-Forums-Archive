---
title: "Packaging question"
date: 2007-04-28
forum: Programming Talk
---

### Post by jjstwerff on 2007-04-28
When I call dpkg-buildpackage it creates a couple of files.

One of them is <package>_<version>.diff.gz

This file will contain the diff between the original clean tar-ball and the build application.

For me it contains a lot of Makefile.in files and the configuration file.
These are build by autoconf and automake and are not relevant for the resulting package.

Is it correct that those files are inside the diff.gz file or is there are way to keep it out of this file?

Greetings,

Jurjen

---

