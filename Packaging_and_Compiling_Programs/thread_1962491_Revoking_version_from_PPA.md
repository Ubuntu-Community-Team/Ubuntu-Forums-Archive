---
title: "Revoking version from PPA?"
date: 2012-04-21
forum: Packaging and Compiling Programs
---

### Post by SwedishWings on 2012-04-21
I'm trying to figure out how to remove a version from a PPA.

By mistake, I uploaded a version to the PPA with dput that failed to build. I created a fix, increased version number, and uploaded again, so the problem is fixed. However, i want to get rid of the faulty version in the PPA.  

Any ideas?

Thanks,
Mike

---

### Post by MadCow108 on 2012-04-21
you can't remove a version from a ppa. Even i you delete the package it will reject new uploads with lower versions than the deleted one.
What you usually do when a package fails to build due to a packaging error is increasing the packaging revision not the upstream version.

You can change the version to something lower by adding an epoch (epch:version-revision), but thats not recommended as you also can never remove the epoch again.

---

### Post by SwedishWings on 2012-04-21
> **MadCow108 said:**
> you can't remove a version from a ppa. Even i you delete the package it will reject new uploads with lower versions than the deleted one.
What you usually do when a package fails to build due to a packaging error is increasing the packaging revision not the upstream version.

You can change the version to something lower by adding an epoch (epch:version-revision), but thats not recommended as you also can never remove the epoch again.

Thanks for the answer. I guess i have to live with the embarrassing faulty version then :D

---

