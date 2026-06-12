---
title: "rpm .so depency issue"
date: 2008-06-19
forum: Packaging and Compiling Programs
---

### Post by mandrews58 on 2008-06-19
running rpm 4.3.3 on RHEL4 u5
Noob question: I've written a spec file which installs several subpackages. One of these, mypackage, installs 3 shared objects: A.so, B.so and C.so   Both B.so and  C.so depend on A.so. rpmbuild builds rpms from the spec file successfully. however upon running rpm --test mypackage.rpm i get an error about failed depencies - A.so required by mypackage. 
Since A.so is in fact installed as part of mypackage, everything works if i use rpm -U mypackage.rpm --nodeps, but that seems lame. Isn't there a way to specify a package which installs shared libraries B.so and A.so where B.so depends on A.so without getting a failed dependency during install?

thx, mark

:confused:

---

