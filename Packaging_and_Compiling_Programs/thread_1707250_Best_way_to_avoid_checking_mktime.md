---
title: "Best way to avoid checking mktime?"
date: 2011-03-15
forum: Packaging and Compiling Programs
---

### Post by Ibidem on 2011-03-15
I got GNU Oleo to build in my PPA (ppa:ibid-ag/oldgtk1), with the Motif GUI.
This required a hack to avoid ./configure hanging when checking for a working mktime:
I replaced it with a dummy that always returns failure.  Autoconf is thus out of sync with ./configure.
Does anyone know a better way?
Sources are here:
[https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16-10ubuntu1.3.diff.gz](https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16-10ubuntu1.3.diff.gz)
[https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16.orig.tar.gz](https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16.orig.tar.gz)
[https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16-10ubuntu1.3.dsc](https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/oleo_1.99.16-10ubuntu1.3.dsc)


If anyone is wondering about what Oleo is or why I'd bother, it's the lightest semi-modern spreadsheet around, especially with the Motif GUI.
It supports SYLK, CSV, its own format (Gnumeric can read the latter), and a couple other formats.  But it hasn't been supported in quite some time, and was last available in Jaunty.

---

### Post by gmargo on 2011-03-15
There's a one line fix for the configure script that fixes the mktime check. 
(I think you may have missed this set of patches):

[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/karmic/oleo/karmic/revision/12](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/karmic/oleo/karmic/revision/12)

---

### Post by Ibidem on 2011-03-17
OK, but that's not really the sort of fix I hoped to find (I did a dirtier hack that returned failure instead of testing, though).  I was wondering if anyone knew how to change the Autoconf part (configure.ac, I think).

---

### Post by gmargo on 2011-03-17
Seems like the "right" thing to do is patch aclocal.m4 and re-run autoconf2.13.  This works:

```

$ diff -u aclocal.m4.00 aclocal.m4
--- aclocal.m4.00       2001-03-07 23:50:09.000000000 -0800
+++ aclocal.m4  2011-03-17 08:34:06.179802371 -0700
@@ -1688,8 +1688,8 @@
  AC_CHECK_FUNCS(alarm)
  AC_CACHE_CHECK([for working mktime], am_cv_func_working_mktime,
   [AC_TRY_RUN(
-changequote(<<, >>)dnl
-<</* Test program from Paul Eggert (eggert@twinsun.com)
+changequote(<<<, >>)dnl
+<<</* Test program from Paul Eggert (eggert@twinsun.com)
    and Tony Leneis (tony@plaza.ds.adp.com).  */
 #if TIME_WITH_SYS_TIME
 # include <sys/time.h>
@@ -1826,7 +1826,7 @@
       mktime_test ((time_t) 60 * 60);
       mktime_test ((time_t) 60 * 60 * 24);
 
-      for (j = 1; 0 < j; j *= 2)
+      for (j = 1; 0 < j; j <<= 1)
         bigtime_test (j);
       bigtime_test (j - 1);
     }

```

---

### Post by Ibidem on 2011-03-17
Thanks for that.  I still have to learn the autoconf/aclocal system.
  Next I should look into a bug with the file formats:
Switching to sylk, sylk-noa0, sc, or csv formats after setting A0 will cause a crash.
But that's another topic, I think.

---

### Post by Ibidem on 2011-03-17
Wrong...it seems the crash results from building with mktime disabled.

---

