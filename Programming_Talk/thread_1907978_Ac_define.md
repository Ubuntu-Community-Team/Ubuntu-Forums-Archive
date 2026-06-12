---
title: "Ac_define"
date: 2012-01-12
forum: Programming Talk
---

### Post by tbastian on 2012-01-12
I'm trying to make a program I wrote more easily portable by actually compiling my glade files into my executable.

My plan is to do something like the following in my configure.ac file:

```

path=`pwd`
AC_DEFINE_UNQUOTED(DMT_GLADE_STR, "`cat ${path}/data/decode_DMT_options.glade`")

```

then use the macro DMT_GLADE_STR in my C code for the "gtk_builder_import_from_string" function call. Whenever I try to do an autoreconf, I get the following error

```

autoheader: warning: missing template: DMT_GLADE_PATH
autoheader: Use AC_DEFINE([DMT_GLADE_PATH], [], [Description])

```

All the documentation I find on the internet uses the exact same syntax as I'm using. What am I doing wrong? I'm using autoreconf 2.68

---

