---
title: "newer versions of libraries"
date: 2006-06-26
forum: Repositories &amp; Backports
---

### Post by geothenes on 2006-06-26
I'm trying to install cmake 2.4.  It's not in the dapper repository, but I switched to the edgy repository and found it in there.  However, if I try to install it the request says BREAK(install).  I assume that this because cmake 2.4 requires some libraries that aren't in the repository.  Cmake requires the following versions of libraries:

-libc6 version 2.4-1 or later -- the dapper repository is at version 2.3.6
-libgcc1 version 1:4.1.0 or later -- the dapper repository is at version 1:4.03
-libstdc++6 version 4.1.0 or later -- the dapper repository is at version 4.0.3

Is there anyway I can get these libraries from the repository while still running under dapper?  Are they in the edgy repository somewhere and they just don't appear as upgrades for me since I am running dapper?

Thanks for any help,
Guy

---

### Post by geothenes on 2006-06-26
Nevermind.  I added the "main" part of the edgy repository and found the libraries I needed.

Guy

---

