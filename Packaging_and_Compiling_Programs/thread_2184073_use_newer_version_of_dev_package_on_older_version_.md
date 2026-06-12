---
title: "use newer version of dev package on older version of ubuntu"
date: 2013-10-27
forum: Packaging and Compiling Programs
---

### Post by danoctavian91 on 2013-10-27
Concrete case:
I need to use libxen-dev 4.2.2 on Ubuntu 12.04, and the binary repositories only contain lower versions. This version of libxen-dev is only in 13.04.

If there exists a more general  approach to these kind of problems which is that?

Thank you,
Dan

---

### Post by Bachstelze on 2013-10-27
What do you mean by "general approach" ? You have several options, among which are upgrading to 13.04, installing the 13.04 packages on your 12.04 system, or looking for a 12.04 package of this version of libxen if you can find one.

---

### Post by danoctavian91 on 2013-10-27
ok, when i try to do install the 13.04 package on 12.04, it seems i need to solve dependencies manually. normally those are handleded by the package manager.

So if I try to run dpkg -i xen-dev4.2.2whatever.deb i get another dependency that i need to install and is not in the 12.04 repos so this goes on and on. 

How do I do this automatically? What is the best way to do this (least work possible)? Will those packages even work on 12.04?

(I would upgrade if it wasn't such a pain in the a**)t

Thanks!

---

### Post by ian-weisser on 2013-10-27
> **danoctavian91 said:**
> ok, when i try to do install the 13.04 package on 12.04, it seems i need to solve dependencies manually. normally those are handleded by the package manager.

So if I try to run dpkg -i xen-dev4.2.2whatever.deb i get another dependency that i need to install and is not in the 12.04 repos so this goes on and on. 

How do I do this automatically? What is the best way to do this (least work possible)? Will those packages even work on 12.04?


The package manager is not meant to be used that way. You are proposing an unsupported use of packages.
The only supported and tested method if using 13.04 packages is by using  a 13.04 system.
Lots of unsupported and/or untested methods exist. You can install just about anything any way you like...but you must really know what you are doing.

There is no way to easily estimate how much work may be needed to get a 13.04 package working on 12.04.
It may work right away, or it may take hours of dependency work, or it may not work at all.

There is no way for the 12.04 package manager to install 13.04 dependencies automatically for you unless you add a 13.04 repository. WARNING: *Don't do it* - it may work, or it may promptly break your system causing data loss and requiring a complete reinstall.

If you really need the latest-and-greatest version of software, look for a 12.04 PPA or look into installing it manually.
Remember to document any installation - you may need to uninstall the software, reinstall, or reinstall from a different source next time you upgrade.

---

### Post by danoctavian91 on 2013-10-27
Thanks, this is the answer i was looking for.

---

