---
title: "Help with packaging Herwig++.  Won't build."
date: 2008-11-18
forum: Packaging and Compiling Programs
---

### Post by jsmidt on 2008-11-18
In my ppa I have uploaded a packaged version of Herwig++ that depends on ThePeg which has also been uploaded to my ppa: [https://launchpad.net/~jsmidt/+archive](https://launchpad.net/~jsmidt/+archive).

Herwig++ does not build.  Here is the error:

```
dpkg-shlibdeps: failure: no dependency information found for /usr/lib/ThePEG/libThePEG.so.6 (used by debian/herwigpp/usr/bin/Herwig++).
dh_shlibdeps: command returned error code 512
make: *** [binary-arch] Error 1

``` 

I don't know what "dh_shlibdeps: command returned error code 512" means.  Furthermore I am confused it complains about no dependency on ThePeg since I have it as a dependence in the control file.

Could someone look at my packages and point me in a direction to get this compiled.  I would really appreciate it.  Thanks.

---

