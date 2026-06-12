---
title: "kernel patch question"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by ptn107 on 2012-01-28
Can anyone tell me how the patches:

0001-base-packaging.patch
0002-debian-changelog.patch
0003-default-configs.patch

from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) are generated? I guess they are automatic?  I need to know how to create those patches on my own.

---

### Post by Lars Noodén on 2012-01-29
You'll want to read up on [diff](http://manpages.ubuntu.com/manpages/oneiric/en/man1/diff.1posix.html) and [patch](http://manpages.ubuntu.com/manpages/oneiric/en/man1/patch.1.html).  There are lots of tutorials on the net about them since they are how updates are passed around for source code.

If possible, work from the .deb packages that have already been created for your convenience.

---

