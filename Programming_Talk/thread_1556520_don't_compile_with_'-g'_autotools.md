---
title: "don't compile with '-g' autotools"
date: 2010-08-19
forum: Programming Talk
---

### Post by tbastian on 2010-08-19
I've been using autotools for a project that I've been working on, and now that I'm just about done I'd like to figure out how to generate a makefile without the '-g' option. It seems to be put in there by default.

Any ideas?

---

### Post by MadCow108 on 2010-08-19
it is set into CFLAGS/CXXFLAGS by AC_PROG_CC or AC_PROG_CXX
I don't know if this behaviour can be turned off but you can override it by setting CFLAGS/CXXFLAGS yourself.

export CFLAGS='-O2'
./configure

or in the make step:
make CFLAGS='-O2'


and you can always strip the debug symbols after build with strip --strip-debug

---

### Post by tbastian on 2010-08-19
Thanks, but I'm looking for a way of it automatically happening, because I'd like to give someone the zipped archive of my project and say just do the standard
```

./configure
make

```

---

### Post by MadCow108 on 2010-08-19
then add the strip command to your make target.

btw. that is done by the make install-strip target which is included in automake by default

you usually leave the choice of debugging symbols to the user.

---

### Post by tbastian on 2010-08-19
would I just add 'strip' to my arguments?

---

### Post by pbrane on 2010-08-20
This is what I've been doing in my configure.in script:

```

. . .
# prevent setting xFLAGS to default of -g -O2
if test x"$CFLAGS" = x""; then
  AC_SUBST(CFLAGS, [ ])
fi
if test x"$CXXFLAGS" = x""; then
  AC_SUBST(CXXFLAGS, [ ])
fi

 . . .

AC_ARG_ENABLE([debug],
              AC_HELP_STRING([--enable-debug],
              [compile with debug symbols @<:@default=no@:>@]),
              [want_debug="$enableval"], [want_debug=no])

if test "x$want_debug" = "xyes" -a $ac_cv_c_compiler_gnu != no; then
  CFLAGS="$CFLAGS -O0 -ggdb"
  CXXFLAGS="$CXXFLAGS -O0 -ggdb"
  AC_DEFINE([DEBUG], 1, [Define for debugging])
else
  CFLAGS="$CFLAGS -O2 -D_FORTIFY_SOURCE=2 -fPIE -pie"
  CXXFLAGS="$CXXFLAGS -O2 -D_FORTIFY_SOURCE=2 -fPIE -pie"
fi

```

You can change the CFLAGS and CXXFLAGS as you need to. Don't know why I need to do this. Before what I did was to do a *make install-strip* or just *strip executable_name*.

---

