---
title: "Kdevelop in jaunty"
date: 2009-04-26
forum: Programming Talk
---

### Post by ResilientBiscuit on 2009-04-26
I have been using KDevelop for awhile and it has been working great.

However, I upgraded to Jaunty last night and now, when trying to compile a simple hello world program I get the following error

cd '/home/jdwolford/programs/hiworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
make all-recursive
Making all in src
compiling hiworld.c (gcc)
mv -f .deps/hiworld.Tpo .deps/hiworld.Po
linking hiworld (CC)
libtool: Version mismatch error. This is libtool 2.2.4 Debian-2.2.4-0ubuntu4, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.4 Debian-2.2.4-0ubuntu4
libtool: and run autoconf again.
make[2]: *** [hiworld] Error 63
make[2]: Target `all' not remade because of errors.
make[2]: Nothing to be done for `all-am'.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

Anyone know what might be going on here? Is there a way to fix this? Kdevelop seems to have a bunch of problems that crop up every time a new release of Ubuntu comes out so it may just be time to find a new development environment.

Thanks
Justin

---

### Post by SadaraX on 2009-05-23
The error is from the libtool program, which is used by KDevelop at the end of the compilation process.

The bug you are experiencing is a symptom of a known bug with a version conflict between recent libtool builds and Kdevelop. I have no suggestion for a solution, though I believe google has a few workaround.

---

### Post by gmatt on 2009-05-24
Its pretty dumb that kdev is broken in the newer ubuntus but it works fine in previous versions. feels like a step backwards.

---

### Post by dishmanw on 2009-07-20
It was broken in the previous version, Intrepid Ibis 8.10.  I thought that they'd have fixed it in this version.

---

### Post by JordyD on 2009-07-20
> **gmatt said:**
> Its pretty dumb that kdev is broken in the newer ubuntus but it works fine in previous versions. feels like a step backwards.

Scribes broke in the newer version, too. That's why I only suggest that people upgrade if they are not supported anymore or they are not happy with their current version.

---

