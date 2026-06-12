---
title: "Packages classified as &quot;depends&quot; or &quot;recommends&quot;"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by vasa1 on 2012-04-22
What's the difference between *depends* and *recommends*?
In [http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop), packages are marked either "*depends*" or "*recommends*".
In 11.04, cups, cups-bsd, and cups-client are marked as *depends*. In 11.10 and 12.04, the same packages are marked as *recommends*.

---

### Post by Cheesemill on 2012-04-22
A dependency is a package that must be installed for the application to work.

A recommendation is a package that doesn't have to be installed but usually provides extra functionality for the application.

---

### Post by vasa1 on 2012-04-22
I get that **A** may need something else, **B**, in order to function. In other words, package **A** may depend on **B** to function in which case **A** would depend on **B** and **B** would be a dependency (requirement) for **A**.
In the link, things like eog, evince, and gedit  are marked as "depends". Why? What does "depends" mean in the context of the link?

---

### Post by ajgreeny on 2012-04-22
It means that the **ubuntu-desktop** package ( a metapackage which is really just a list of dependencies) has to install **eog, evince, gedit**, etc etc, in order for it to be installed itself.  ie, you can't have ubuntu-desktop without those packages as well, and if you should remove one of those dependencies it will also remove ubuntu-desktop.

---

### Post by vasa1 on 2012-04-22
> **ajgreeny said:**
> It means that the **ubuntu-desktop** package ( a metapackage which is really just a list of dependencies) has to install **eog, evince, gedit**, etc etc, in order for it to be installed itself.  ie, you can't have ubuntu-desktop without those packages as well, and if you should remove one of those dependencies it will also remove ubuntu-desktop.

Got it now. Thanks :)

---

