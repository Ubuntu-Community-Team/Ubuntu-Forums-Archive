---
title: "Coupple of packaging questions"
date: 2009-03-16
forum: Packaging and Compiling Programs
---

### Post by hessiess on 2009-03-16
I am interested in creating a deb package for the Quad-Ren graphics engine, but I have a few questions:

1) How do you include dependencies for programs which are provided by multiple packages (The OpenGL libs are provided by the various open/propiatery graphics drivers).

2) Where should 'example' programs be put? assuming it is the home directory, how do I represent 'current users home dir' in the package build tree.

Thanks for any advice.

---

### Post by InfinityCircuit on 2009-03-17
Use dh_installexamples in debian/rules to install examples.

If multiple packages provide the necessary dependencies, then those packages probably all have a "Provides" field. You can list what they provide in the new package. In the case that they don't have this Provides field, that probably means that they aren't in fact substitutable. But you can still do the equivalent with an OR dependency chain:

Depends: package1 | package2 | package3, libfoo1, libfoo2, xutils

for instance

---

### Post by hessiess on 2009-03-18
Thanks.

---

