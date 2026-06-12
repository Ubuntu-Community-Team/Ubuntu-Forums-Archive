---
title: "How to change compiler parameter of dpkg-buildpackage"
date: 2009-07-06
forum: Packaging and Compiling Programs
---

### Post by carfield on 2009-07-06
My currently setup is 

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2


How can I change that? BTW, I think, using -O3 / -O4 is better , right?

---

