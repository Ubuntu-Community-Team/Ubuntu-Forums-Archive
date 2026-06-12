---
title: "How to specify dependacies libwxgtk"
date: 2009-06-17
forum: Packaging and Compiling Programs
---

### Post by davenicholas on 2009-06-17
Hi 

I have made a deb package for a game I have written in c++ with dependencies on libwxgtk.

[http://www.davenicholas.me.uk/openshed_0.1-1_i386.deb]("http://www.davenicholas.me.uk/openshed_0.1-1_i386.deb") (with no deps)

I am new (complete noob) to deb packaging and would like to know how to specify the dependency in the control file as:

*Depends: libwxgtk2.6-0 (>=2.6.3.2.2-3ubuntu4)*

But this version of libwxgtk I have and restricts installation on older ubuntu's but without the above line it installs ok.

Is there anyway I can generically specify a dependency of without giving the version number of the package libwxgtk?

Thanks in advance.

Dave

---

### Post by davenicholas on 2009-06-19
I now specify a dependency of libwxgtk2.8.

:)

---

