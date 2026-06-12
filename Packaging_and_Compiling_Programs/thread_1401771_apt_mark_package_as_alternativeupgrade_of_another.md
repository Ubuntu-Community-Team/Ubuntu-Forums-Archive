---
title: "apt: mark package as alternative/upgrade of another"
date: 2010-02-08
forum: Packaging and Compiling Programs
---

### Post by alphaniner on 2010-02-08
I built and installed the latest version of glib after removing the one from the repos with dpkg.  Of course, aptitude is displeased.  If I name my package differently from the one in the repo, aptitude wants to install the repo version.  If I name my package the same, aptitude wants to *upgrade* my version to the old version.  Is there any way to fix this?

---

### Post by Bachstelze on 2010-02-08
You should either give your package a higher version number than the one in the repos, or lock the package in your package manager to prevent upgrades.

---

### Post by alphaniner on 2010-02-08
I thought having a newer version number would work.  The reason it didn't was because I had actually built/installed an *older* version of the library.  2.6 !> 2.12 #-o.  All I needed was the -dev package.

Thanks for the help, marking solved.

---

