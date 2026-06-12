---
title: "apt downloaded package"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by henrypradeep on 2008-09-29
Hi where can i see the downloaded packages of apt-get -d? Will this command also download all dependency files?

---

### Post by snova on 2008-09-29
Apt sticks downloaded packages in /var/cache/apt/archives.

apt-cache seems to be the program to use to query the cache, discovered by experimenting. Try "apt-cache pkgnames" and watch the list fly by...

It should probably download dependencies, but as I've never used that option, I can't say for sure.

---

