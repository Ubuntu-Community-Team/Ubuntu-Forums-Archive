---
title: "Error installing a self-made .deb package"
date: 2005-12-10
forum: Packaging and Compiling Programs
---

### Post by z-vet on 2005-12-10
Hi all.
I created a package using checkinstall and set an 'architecture' flag to i686, since my machine **is** i686, i have an i686 kernel installed and use compiler flags for P4. Well, when trying to install a new package dpkg responds with the following:
```
package architecture (i686) does not match system (i386)
```
What i am doing wrong?

---

### Post by kairu0 on 2005-12-10
Type "dpkg --print-architecture" to double-check that you are specifying the correct architecture.

---

