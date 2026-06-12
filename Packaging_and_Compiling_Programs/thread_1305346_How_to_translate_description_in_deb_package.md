---
title: "How to translate description in deb package?"
date: 2009-10-29
forum: Packaging and Compiling Programs
---

### Post by cheeselee on 2009-10-29
Which is the standard way to translate description in deb packages?

Can anyone show me a related doc or how-to?

---

### Post by SevenMachines on 2009-11-02
As far as I am aware this is not done by the package itself but translations are added for package descriptions as part of the ddtp project in debian which ubuntu syncs from 
[https://launchpad.net/ddtp-ubuntu](https://launchpad.net/ddtp-ubuntu)

[EDIT] Package description translations are uploaded so that apt can use ddtp to automatically fetch a translated package description (if one exists) for the prefered language

---

### Post by cheeselee on 2009-11-08
> **SevenMachines said:**
> As far as I am aware this is not done by the package itself but translations are added for package descriptions as part of the ddtp project in debian which ubuntu syncs from 
[https://launchpad.net/ddtp-ubuntu](https://launchpad.net/ddtp-ubuntu)

[EDIT] Package description translations are uploaded so that apt can use ddtp to automatically fetch a translated package description (if one exists) for the prefered language

Thanks!

---

