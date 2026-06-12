---
title: "non-repo software in synaptic"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by rattskjelke on 2012-02-21
If you install software from someplace other than a repository (if you download a .deb file) will it still show up in Synaptic Package Manger and Ubuntu Software Center?
In other words does Synaptic and Software Center show all installed software or just the ones that were installed from the repos that are listed in Software Sources?

---

### Post by yetiman64 on 2012-02-21
An example of a .deb I have installed here (not in a repository, afaik) shows up in Synaptic but under the section "Local or obsolete" within the "Status" section. ".deb" packages are installed using software center (default in 11.10) and seem to show up in Synaptic even without being in a repository. BTW the package I refer to above is simple-lightdm-manager.

<offtopic, but related> Source code built and installed (without the use of checkinstall) will not show up in Synaptic and are not registered with the package management system. Using checkinstall with source code allows the package created to be registered with the package management system.</offtopic>

---

### Post by Frogs Hair on 2012-02-21
I have a couple of examples . The Opera .deb shows up in the software center and synaptic . The pulse audio equalizer I installed shows up only in synaptic under installed local . All packages should appear in the synaptic package manager.

---

### Post by cortman on 2012-02-21
> **Frogs Hair said:**
> I have a couple of examples . The Opera .deb shows up in the software center and synaptic . The pulse audio equalizer I installed shows up only in synaptic under installed local . All packages should appear in the synaptic package manager.

I'm curious if this works for packages installed with dpkg as opposed to apt?

---

### Post by mcduck on 2012-02-22
> **cortman said:**
> I'm curious if this works for packages installed with dpkg as opposed to apt?

*Any* .deb packages installed in your system will appear in Synaptic, and in apt-cache searches etc. They are all installed using exactly the same package management tools.

---

### Post by rattskjelke on 2012-02-25
I think I understand now. Thanks!

---

