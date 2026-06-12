---
title: "Creating user in Pbuilder environment before configure?"
date: 2008-02-02
forum: Packaging and Compiling Programs
---

### Post by Jingo on 2008-02-02
Hi,

Trying to package simscan for my qmail install.

The ./configure needs the simscan user and group.

How do I add a user and group inside the pbuilder environment?

I have been trying "adduser simscan" inside the debian/rules file, but it is run with fakeroot at most!
Where should I add the lines so debhelper/dpkg-buildpackage/pbuilder runs with "root" privileges?

Help mostly appreciated!

---

### Post by dholbach on 2008-02-04
Is the simscan user necessary during the build? Or is it a useless safety check that just needs to be patched out of the source and 'replaced' by the usual setup of user/group during the postinst?

---

### Post by Jingo on 2008-02-04
You're right...

Simscan user was just an safety check... moving user setup to pre-/postinst

But anyway, would it be possible?

---

### Post by dholbach on 2008-02-04
I don't think it makes much sense. You will add a user on the build daemon for nothing. (If it's possible at all...)

---

