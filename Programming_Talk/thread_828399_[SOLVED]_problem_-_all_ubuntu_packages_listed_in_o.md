---
title: "[SOLVED] problem - all ubuntu packages listed in one sqlite db"
date: 2008-06-13
forum: Programming Talk
---

### Post by forger on 2008-06-13
I'm trying to make a script that grabs all the package listings.
example:
I wget [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2) and extract it, then manage it with sed to transform it into an sqlite insert command.

But there's one problem, not all packages contain
> 
Replaces:
Provides:
Depends:
Recommends:
Suggests:
Conflicts:

and

> Task:

How can I "search" for them and add them in order, so that sed can grab them and add empty values in their place?

Attached some package listed in the above mentioned url.

---

### Post by forger on 2008-06-14
never mind, I went for a perl script :guitar:

[https://code.edge.launchpad.net/~medigeek/+junk/packages2sqlite](https://code.edge.launchpad.net/~medigeek/+junk/packages2sqlite)

---

