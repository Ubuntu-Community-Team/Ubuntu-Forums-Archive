---
title: "DH_ALWAYS_EXCLUDE not working"
date: 2012-06-06
forum: Packaging and Compiling Programs
---

### Post by schander on 2012-06-06
Hi All,
I'm trying to generate a deb package for our shared library.
How ever the src code contains some binary files, which aren't used directly in the build, but are need in the src tree.
I have tried adding:
export DH_ALWAYS_EXCLUDE=.xdb
to the rules file, however it doesn't seem to work. I get the same errors about the xdb file, even tried *.xdb

I'm using debuild for the package build.

Anyone any ideas?

Thanks
Satpal

---

