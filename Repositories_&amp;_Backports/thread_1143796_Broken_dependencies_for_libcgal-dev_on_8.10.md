---
title: "Broken dependencies for libcgal-dev on 8.10?"
date: 2009-04-30
forum: Repositories &amp; Backports
---

### Post by jazzgossen on 2009-04-30
I'm trying to install libcgal-dev from the repository on Unbuntu 8.10 with all essential updates. It seems that the dependencies on libatlas and liblapack are broken. Should I file a bug report (or upgrade to 9.04)?

```

> sudo apt-get install libcgal-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcgal-dev: Depends: libatlas-base-dev but it is not going to be installed or
                        libatlas.so.3gf
               Depends: liblapack-dev but it is not going to be installed
E: Broken packages

```

---

