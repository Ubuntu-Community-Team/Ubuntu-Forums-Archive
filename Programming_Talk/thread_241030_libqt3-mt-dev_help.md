---
title: "libqt3-mt-dev help"
date: 2006-08-21
forum: Programming Talk
---

### Post by garretwp on 2006-08-21
I am trying to compile to the latest kernel. But before I can do that, I need to get all the stuff to do the work. When I go to do apt-get install libqt3-mt-dev, I get an error message: 

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages

How do I get around this or fix this so I can compile to the latest kernel 2.6.17.9? I am currently running 2.6.15-26

Thanks,

- Garrett

---

