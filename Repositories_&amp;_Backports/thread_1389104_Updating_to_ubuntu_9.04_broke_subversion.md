---
title: "Updating to ubuntu 9.04 broke subversion"
date: 2010-01-23
forum: Repositories &amp; Backports
---

### Post by bob_drive5 on 2010-01-23
I upgraded from version < 8 (sorry I didn't make a note of exactly which version) to v9.04 by following instructions I found on ubuntu.com. Prior to the upgrade I was using svn extensively with no problems. After upgrading, the svn command fails with:

svn: error while loading shared libraries: libldap_r.so.2: cannot open shared object file: No such file or directory

This:

ldd `which svn` | grep "not found" | wc -l

says there are 44 (!) shared libraries not found. I tried uninstalling and reinstalling subversion, which is about the limit of my linux expertise, but no change. I have googled and searched forums without success. Advice will be greatly appreciated.

---

