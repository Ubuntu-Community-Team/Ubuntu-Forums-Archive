---
title: "Compiling mono from source problems"
date: 2006-11-11
forum: Programming Talk
---

### Post by steven43126 on 2006-11-11
Nevermind problem solved by upgrading to automake 1.9

Hi,

Im trying to compile mono from the svn repository, iv'e checked it out and followed the guides on mono, but i get the following errors trying to run autogen:

> mono/mini/Makefile.am: mono_OBJECTS should not be defined
automake: mono/mini/Makefile.am: warning: automake does not support EXTRA_DIST being defined conditionally
mono/mini/Makefile.am:329: invalid unused variable name: `nodist_libmono_la_SOURCES'
mono/mini/Makefile.am:332: invalid unused variable name: `nodist_libmono_static_la_SOURCES'
automake: runtime/Makefile.am: unterminated conditionals: @BUILD_MCS_TRUE@
runtime/Makefile.am:142: `distdir' is target; expected variable
**Error**: automake failed.


any ideas ? anyone building mono from svn here ?

---

