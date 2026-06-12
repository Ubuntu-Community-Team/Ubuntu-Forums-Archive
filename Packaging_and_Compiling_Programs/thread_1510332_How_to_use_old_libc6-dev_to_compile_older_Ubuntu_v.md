---
title: "How to use old libc6-dev to compile older Ubuntu versions"
date: 2010-06-15
forum: Packaging and Compiling Programs
---

### Post by Lpadman on 2010-06-15
Using Lucid, I need to compile source code for old versions of Ubuntu.

Is there anyway to install the old glib dev libraries: libc6-dev on Lucid?

---

### Post by SevenMachines on 2010-06-16
the best way is probably to [use pbuilder to build on specific distributions/releases]("https://wiki.ubuntu.com/PbuilderHowto"), you may want to focus on pbuilder-dist since it simplifies much of what is needed. obviously using virtual machines is also an option.

---

