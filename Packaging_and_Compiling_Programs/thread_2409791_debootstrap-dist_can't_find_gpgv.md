---
title: "debootstrap-dist can't find gpgv"
date: 2019-01-06
forum: Packaging and Compiling Programs
---

### Post by SMButler on 2019-01-06
Running pbuilder-dist bionic create and getting:
E: debootstrap failed
E: Tail of debootstrap.log:
/usr/sbin/debootstrap: 601: /usr/sbin/debootstrap: gpgv: not found
E: End of debootstrap.log
W: Aborting with an error


I have edited the /usr/sbin/debootstrap script to invoke /usr/bin/gpgv but doesn't seem to fix this.  Where else needs to be told?  Even though whereis can find gpgv.

---

