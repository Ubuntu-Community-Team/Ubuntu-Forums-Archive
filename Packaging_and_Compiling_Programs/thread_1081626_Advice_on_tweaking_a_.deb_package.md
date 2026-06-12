---
title: "Advice on tweaking a .deb package?"
date: 2009-02-26
forum: Packaging and Compiling Programs
---

### Post by djbloc on 2009-02-26
I’ve made a few tweaks to customise an original ubuntu supplied .deb package. I would now like to repackage it up so I could distribute it to others.

I think I could do this in two ways:

1. Keep the same package name and add a suffix to the version number (similar to what ubuntu does to debian pull-through and adapted packages)

2. Create a completely new package with a new name and add the “Conflicts:” and “Replaces” tags in the control file pointing to the original ubuntu supplied package.

As a result, assuming someone has set up to automatically update their ubuntu distribution, I do not want a newer version of the ubuntu supplied .deb package to override my tweaked one. Which method would you suggest that would do this?

Thanks in advance

---

### Post by InfinityCircuit on 2009-02-27
The only way to ever prevent an upgrade with 100% reliability is to rename the package and to create a Conflict. But this is sort of ridiculous.

An easier way would just be to increment the version number (man dch, look at --local), and then pin the package higher than the normal Ubuntu packages.

---

