---
title: "No monodevelop-vala &amp; monodevelop-boo in Ubuntu 12.10 Quantal Quetzal"
date: 2013-02-19
forum: Programming Talk
---

### Post by MichiGreat on 2013-02-19
I recently upgraded my notebook from 11.04 to 12.10 and found out that packages monodevelop-vala and monodevelop-boo are missing. Does anyone know what has happend to those packages? Is there no more support for Boo and Vala in MonoDevelop? Why? Are there any other IDEs supporting those languages?

Best regards

*Michael*

---

### Post by iMac71 on 2013-02-19
it seems that there be not releases of these packages for Quantal; see here:
monodevelop-boo: [https://launchpad.net/ubuntu/quantal/+source/monodevelop-boo](https://launchpad.net/ubuntu/quantal/+source/monodevelop-boo)
monodevelop-vala: [https://launchpad.net/ubuntu/quantal/+source/monodevelop-vala](https://launchpad.net/ubuntu/quantal/+source/monodevelop-vala)

---

### Post by MichiGreat on 2013-02-20
> **iMac71 said:**
> it seems that there be not releases of these packages for Quantal; see here:
monodevelop-boo: [https://launchpad.net/ubuntu/quantal/+source/monodevelop-boo](https://launchpad.net/ubuntu/quantal/+source/monodevelop-boo)
monodevelop-vala: [https://launchpad.net/ubuntu/quantal/+source/monodevelop-vala](https://launchpad.net/ubuntu/quantal/+source/monodevelop-vala)

Yes, that's similar to what I wrote. But I still have no clue what to do in order to program Boo or Vala in MonoDevelop 3. Packages from older Ubuntus are made for MonoDevelop 2.x and they don't work in MonoDevelop 3.

---

### Post by MadCow108 on 2013-02-20
so far I know md-vala and md-boo are not released together with monodevelop anymore and were not properly maintained externally, so stuff started to break and the packages were removed.
If that has changed and the software is again in a distributable state contact the debian cli team [email]debian-cli@lists.debian.org[/email]

---

### Post by MichiGreat on 2013-02-21
> **MadCow108 said:**
> so far I know md-vala and md-boo are not released together with monodevelop anymore and were not properly maintained externally, so stuff started to break and the packages were removed.
If that has changed and the software is again in a distributable state contact the debian cli team [email]debian-cli@lists.debian.org[/email]

Okay, but how do I find out who develops (or developed) monodevelop-boo and monodevelop-vala? I searched [www.monodevelop.com](www.monodevelop.com) but got no results. Debian has currently still MonoDevelop 2.x, so it has both monodevelop-boo and monodevelop-vala in its repositories (squezze, sid and experimental). I suppose that those language bindings just haven't been upgraded to MonoDevelop 3.x.

---

