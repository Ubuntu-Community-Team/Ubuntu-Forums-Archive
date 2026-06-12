---
title: "Patch dependency after install"
date: 2009-05-12
forum: Packaging and Compiling Programs
---

### Post by arich57 on 2009-05-12
Hello,
  I have created a package that downloads and installs my development environment and tools to try to make my life easier when changing systems. One of the dependencies I have are the boost libraries. The problem I have is that I have to apply a patch to the libraries after getting them from the repository before I'm able to build against them.

Is a way for me to have to patch be applied as part of the package install?

right now I have to do this:

gdebi myPackage
sudo patch /usr/include/boost/numeric/ublas/traits.hpp ./adl_problem.patch


Thanks for the help.

-Aaron

---

