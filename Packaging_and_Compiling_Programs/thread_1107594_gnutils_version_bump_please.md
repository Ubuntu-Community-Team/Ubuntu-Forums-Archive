---
title: "gnutils version bump please"
date: 2009-03-26
forum: Packaging and Compiling Programs
---

### Post by kodiakmax on 2009-03-26
I am using the jaunty repo.  But don't mind adding 3rd party repo's either.  Currently the highest version of libgnutls and libgnutls-dev that I can find a package for is 2.4.2

looking for a 2.6.2 or 2.6.3  the 2.6.4 is still too buggy from what I can find out. For x64 bit system

I tried downloading source and doing a ./configure and checkinstall however, it does not upgrade the current package it just installs along side it.  Any tips/doc/info on making an upgrade package myself if no-one is interested in doing it?  also if it is done from source are the dev files included?  If that's the case why are they two separate packages in the repos?  Sorry if these seem like noobish questions but I'm still learning.

thanks

---

### Post by Stochastic on 2009-03-27
well, the best place to ask for this is in Launchpad.net, but then you're still just asking for it and not taking care of the issue yourself (good, but not great).

To tackle this yourself, take a read through this really easy guide: [https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate](https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate)

---

