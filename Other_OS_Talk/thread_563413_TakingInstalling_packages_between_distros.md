---
title: "Taking/Installing packages between distros"
date: 2007-09-29
forum: Other OS Talk
---

### Post by talikarng on 2007-09-29
Out of sheer curiousity I am wondering if it is possible to take packages from other distros repositories (eg. Fedora, Debian, Opensuse etc) and install them in Ubuntu?

And can this occur the other way around? (Ubuntu packages  to another distro)

---

### Post by tbroderick on 2007-09-30
Yes and yes.

---

### Post by miggols99 on 2007-09-30
No. They use different package types, so you won't be able to install them. You might get some luck with Debian, because they use .deb packages. But if you want loads of packages, try Debian :)

---

### Post by fwojciec on 2007-09-30
There is an app called alien (should be in the repos) that converts between different package formats.  Their website is [here]("http://kitenet.net/~joey/code/alien/").

---

### Post by exploder on 2007-09-30
You can convert rpm packages to deb's using alien.

---

### Post by talikarng on 2007-10-01
Thankyou

---

### Post by jrusso2 on 2007-10-02
Some will work and others will not because different distros put files in different places and the libraries might be different versions.

---

