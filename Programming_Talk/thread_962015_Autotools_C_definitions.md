---
title: "Autotools C definitions"
date: 2008-10-28
forum: Programming Talk
---

### Post by dreblen on 2008-10-28
Hi,
I'm in the process of setting up my project to use autotools and I need to make a C definition.
I would like the definition to default to
```
"${libdir}/gclassgen/modules"
```
but the problem that I'm having is that ${libdir} evaluates to
```
${exec_prefix}/lib
```
The problem with this is that C doesn't know what ${exec_prefix} should be, so my program fails.
My question then, is how I can make autotools fully expand a variable, or if there's a better way to do something like this.
Thank you...

---

### Post by cabalas on 2008-10-28
Now are you wanting this to be expanded in the autotools files or in the actual source? the question was a bit vague.  For this post I'm going to assume that you want to access it in the source code.

To be able to access it in code I would add the following to the Makefile.am for the binary.

```

AM_CFLAGS = -DVARIABLE_NAME=\"$(libdir)/gclassgen/modules\"

```

where VARIABLE_NAME is how ever you want to refer to it in code, and then just use it like a constant.

Note: The code above is just pulled off of the top of my head, while I am reasonably confident it will work there is a chance that it is wrong.

---

### Post by dreblen on 2008-10-28
Sorry for the ambiguity, I actually meant for it to be in configure.ac so that it can be set using something like
```
./configure GCG_MODULE_DIR=/module/path
```
However I'm open to suggestions on other ways to have it not be hard coded (right now, I'm trying to move away from the exact same line that you suggested).

Currently, I'm working off of this:
```
if test "$GCG_MODULE_DIR" = ""; then GCG_MODULE_DIR=${libdir}/gclassgen/modules; fi
AC_DEFINE_UNQUOTED([GCG_MODULE_DIR], ["$GCG_MODULE_DIR"], [The directory for storing codegen modules])
```

What is the standard way of doing things like this?
My thinking is to do it during the configure process (similar to --prefix), but I imagine it could be done during the make command,
is there a standard way of defining variables?

---

### Post by hod139 on 2008-10-29
I do not know the answer to your question, but may I suggest an alternative.  There are more modern build systems available, my preference being [cmake]("http://www.cmake.org/").  Cmake is cross platform (natively, windows users do not need cygwin) and much easier to use than the old autotools framework.

---

### Post by dreblen on 2008-10-30
Thanks for the suggestion hod139. I'll probably look into CMake as an alternative to autotools.
However, I solved my problem after a bit of mailing list searching.
It turns out that the problem wasn't really that it wasn't expanding everything, it was that ${exec_prefix} wasn't defined, so it had nothing to expand to.
This was solved with defining an m4 macro:
```
m4_define([EXPAND_LIBDIR],
[if test $prefix = NONE; then prefix=$ac_default_prefix; fi
if test $exec_prefix = NONE; then exec_prefix=$prefix; fi
eval $1=${libdir}
])
```
So then I just do
```
EXPAND_LIBDIR(libdir)
```
and everything works perfectly.

---

