---
title: "Why we do not have the newest BOOST library?"
date: 2008-08-23
forum: Programming Talk
---

### Post by MagiSu on 2008-08-23
Currently, the newest version of boost is 1.36, however in the source there is only boost 1.34. It is possible that people need time to package some files but the version number should not be too late!:(

---

### Post by Majorix on 2008-08-23
I don't think software on Ubuntu is updated often. You can instead try your luck at getdeb.net.

---

### Post by dribeas on 2008-08-23
> **MagiSu said:**
> Currently, the newest version of boost is 1.36, however in the source there is only boost 1.34. It is possible that people need time to package some files but the version number should not be too late!:(

Binary compatibility. As it is now boost libraries are not version qualified (not the binary libs, not the include directories). That means that only one version can be installed in debian/ubuntu at a time. 1.34 and 1.35 are not compatible and changing the current version would mean recompiling and redistributing all packages that depend on it.

I would really like the packager to solve this problem but that is a major change, as it is not only boost packages, but all depending packages, both in debian and ubuntu.

You can always install another version locally and use it, just not as simple as installing a package.

   David

---

### Post by StOoZ on 2008-08-24
just install it from source , I did that , works like a charm

---

### Post by MagiSu on 2008-08-30
> **dribeas said:**
> Binary compatibility. As it is now boost libraries are not version qualified (not the binary libs, not the include directories). That means that only one version can be installed in debian/ubuntu at a time. 1.34 and 1.35 are not compatible and changing the current version would mean recompiling and redistributing all packages that depend on it.

I would really like the packager to solve this problem but that is a major change, as it is not only boost packages, but all depending packages, both in debian and ubuntu.

You can always install another version locally and use it, just not as simple as installing a package.

   David

Thanks for your explanation!

---

