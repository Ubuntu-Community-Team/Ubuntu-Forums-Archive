---
title: "building upgrade deb packages"
date: 2007-08-30
forum: Programming Talk
---

### Post by Schleproque on 2007-08-30
Good Day All,

I have managed to build .deb packages that do what I want them to do but I am stuck at the next step.  I haven't been able to figure out how to specify a package as being the upgrade to a previous package.

For example:
The original package is called deb-test-1.0.0.deb. I make some changes and now I have deb-test-1.1.0.deb. How do I specify the second package as the upgrade to the first?

Thanks Bunches,
Rodney

---

### Post by nanotube on 2007-08-31
> **Schleproque said:**
> Good Day All,

I have managed to build .deb packages that do what I want them to do but I am stuck at the next step.  I haven't been able to figure out how to specify a package as being the upgrade to a previous package.

For example:
The original package is called deb-test-1.0.0.deb. I make some changes and now I have deb-test-1.1.0.deb. How do I specify the second package as the upgrade to the first?

Thanks Bunches,
Rodney

as long as it has the same name, and a higher version number, it will be detected as an upgrade automatically, i think?

---

### Post by Schleproque on 2007-09-04
Changing the version number like that does allow me to install one over the other as an upgrade but I am still having problems with apt-get functionality.

Thanks,
Schlep

---

### Post by Schleproque on 2007-09-04
I made a mistake. Changing the version number fixed the problem even with apt.

---

