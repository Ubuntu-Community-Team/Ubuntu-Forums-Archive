---
title: "How to create Debian packages which automatically add PPAs?"
date: 2011-05-15
forum: Packaging and Compiling Programs
---

### Post by ProcuratorIncendia on 2011-05-15
Hello!
Does anyone know how to create a package which installs a PPA into the system when the package is installed?

Is it typed into the control file? If yes, what do a write into it?

I've seen it done before so I know it's possible.

Person who answers my questions get this giant imaginary box of popcorn. :popcorn:

---

### Post by MadCow108 on 2011-05-15
you probably have to do that in the postinst maintainer script.
an example I know is the package of the opera browser.

---

### Post by ProcuratorIncendia on 2011-05-16
You have told me where to do it but not how. I want to know how to do it. Can you please give me more help than just where to look?

The only packaging I know is how to create meta-packages, whose only purpose is to depend on and replace other packages. All that involves is two folders, a terminal command and a control file.

---

### Post by MadCow108 on 2011-05-16
maintainer scripts are a more advanced aspect of packaging.

The basic steps are:
- add a postinst script (don't forget the #DEBHELPER# token if you're using debhelper, it will get replaced by debhelpers maintainer scripts (e.g. py_compile, update mime types etc))
- add a debconf template to ask the user if he wants to add the repository via debconf
- check the user answer in the postinst configure call case (db_get I think)
- add an entry to /etc/apt/sources.list.d/
- load the ppa key (apt-key)
- add a postrm, remove everything again
- testing
- testing
- testing

you must read this:
[http://www.debian.org/doc/debian-policy/ch-binary.html#s-maintscripts](http://www.debian.org/doc/debian-policy/ch-binary.html#s-maintscripts)
[http://www.debian.org/doc/debian-policy/ch-maintainerscripts.html](http://www.debian.org/doc/debian-policy/ch-maintainerscripts.html)
[http://www.debian.org/doc/manuals/maint-guide/dother.en.html#maintscripts](http://www.debian.org/doc/manuals/maint-guide/dother.en.html#maintscripts)
[http://www.fifi.org/doc/debconf-doc/tutorial.html](http://www.fifi.org/doc/debconf-doc/tutorial.html)

---

