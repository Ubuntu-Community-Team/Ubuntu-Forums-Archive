---
title: "vim: symbol lookup error: /usr/lib/libperl.so.5.14: undefined symbol: l_pp_list"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by jemofthewest on 2013-03-19
So, I haven't sshed into my server in awhile.  Just did an upgrade, and now whenever I try to use vim I get the error in the title.  I don't know if vim worked beforehand, but I'm honstely clueless here.  Tried purging and reinstalling vim and perl to no avail.  I'm running Ubuntu Server, 3.2.0-33-generic-pae.

---

### Post by jemofthewest on 2013-03-22
Do I need to provide more information?  I'm not really even sure to look for this.  Thanks.

---

### Post by steeldriver on 2013-03-22
I don't think /usr/lib/libperl.so.5.14 is part of the main perl package, it seems to be in libperl5.1.4:

```
$ apt-file search libperl.so.5.14
libperl5.14: /usr/lib/libperl.so.5.14
libperl5.14: /usr/lib/libperl.so.5.14.2
perl-debug: /usr/lib/debug/usr/lib/libperl.so.5.14.2
```

My 32-bit 12.04 server (3.2.0-38-generic-pae) doesn't even have that package installed (but vim works) - maybe it's required for perl plugins? You could try reinstalling that maybe.

```

$ apt-cache show libperl5.14
Package: libperl5.14
Priority: optional
.
.
.
Description-en: shared Perl library
 This package is required by programs which embed a Perl interpreter to
 ensure that the correct version of `perl-base' is installed.  It
 additionally contains the shared Perl library on architectures where the
 perl binary is linked to libperl.a (currently only i386, for performance
 reasons).  In other cases the actual library is in the `perl-base' package.
```

---

### Post by jemofthewest on 2013-03-23
Thanks for the answer.  You brought up a good point, I had just added my laptop's .vimrc.  However, that didn't fix it.  I think it had something to do with installing vim-nox, because I removed vim and libperl5.14 and then just reinstalled vim and that worked.  Thanks!

---

