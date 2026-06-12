---
title: "Installing subversion v1.5.2"
date: 2008-09-11
forum: Programming Talk
---

### Post by japtar10101 on 2008-09-11
I'm attempting to install subversion 1.5.* (apt-get grabs v1.4.*) with absolutely no luck.

When I run ./configure in the extracted folders, it tells me to grab the apr library using svn.  Then, I'm supposed to run ./apr/buildconf

When I run ./apr/buildconf, I get this:
```
/subversion-1.5.2$ ./apr/buildconf
buildcheck: checking installation...
buildcheck: autoconf version 2.61 (ok)
buildcheck: autoheader version 2.61 (ok)
buildcheck: libtool version 1.5.26 (ok)
buildcheck: local copy of find_apr.m4 does not match APR's copy.
            An updated copy of find_apr.m4 may need to be checked in.
buildcheck: local copy of PrintPath does not match APR's copy.
            An updated copy of PrintPath may need to be checked in.
Copying libtool helper files ...
buildconf: Using libtool.m4 at /usr/share/aclocal/libtool.m4.
Creating include/arch/unix/apr_private.h.in ...
Creating configure ...
configure.ac:159: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
rebuilding rpm spec file
./apr/buildconf: 89: build/get-version.sh: not found
cat: ./build/rpm/apr.spec.in: No such file or directory
```
And running ./configure gets me:
```
$ ./configure 
configure: Configuring Subversion 1.5.2
./configure: line 1840: syntax error near unexpected token `config.nice'
./configure: line 1840: `SVN_CONFIG_NICE(config.nice)'
```
This is desperately important (school project, see).  What's going on?

---

### Post by tinny on 2008-09-11
Ive personally only ever installed subversion from the repositories.

Subversion 1.5.* is now available in the hardy backports repository.

[http://packages.ubuntu.com/hardy-backports/subversion](http://packages.ubuntu.com/hardy-backports/subversion)

---

### Post by japtar10101 on 2008-09-11
> **tinny said:**
> Ive personally only ever installed subversion from the repositories.

Subversion 1.5.* is now available in the hardy backports repository.

[http://packages.ubuntu.com/hardy-backports/subversion](http://packages.ubuntu.com/hardy-backports/subversion)

"Backports"?

---

### Post by SeanHodges on 2008-09-11
I really think the backports project needs some better exposure, I often hear people trying to compile software that is in backports already.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

That should give you your explanation.

---

### Post by tinny on 2008-09-11
> **SeanHodges said:**
> I really think the backports project needs some better exposure, I often hear people trying to compile software that is in backports already.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

That should give you your explanation.

Yeah! The backports can be incredibility useful.

---

