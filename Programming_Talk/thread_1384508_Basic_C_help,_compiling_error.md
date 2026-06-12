---
title: "Basic C help, compiling error"
date: 2010-01-18
forum: Programming Talk
---

### Post by Gislinn on 2010-01-18
Hello,

I'm only a beginner in C, I've managed to make a 'Hello World' program :lolflag: but I've used Matlab (and Java in Matlab) alot #-o

I'm trying to compile a file called eight_ball.c, it's a Magic 8-ball plugin for Pidgin in a Pidgin Plugin Pack [(link)]("http://plugins.guifications.org/trac/wiki/eight_ball").

I wanted to translate this plugin to my native language and I'm having a lot of problem compiling it, I'm using Ubuntu and tried to put this command in terminal:

```
cc eight_ball.c -o eight_ball.so `pkg-config pidgin --cflags --libs glib-2.0`
```

That resulted in getting the following message:
```
In file included from ../common/../common/glib_compat.h:66,
                 from ../common/pp_internal.h:29,
                 from eight_ball.c:24:
/usr/include/glib-2.0/glib/gi18n-lib.h:29:2: error: #error You must define GETTEXT_PACKAGE before including gi18n-lib.h. Did you forget to include config.h?
eight_ball.c: In function ‘plugin_load’:
eight_ball.c:325: error: ‘GETTEXT_PACKAGE’ undeclared (first use in this function)
eight_ball.c:325: error: (Each undeclared identifier is reported only once
eight_ball.c:325: error: for each function it appears in.)
eight_ball.c: At top level:
eight_ball.c:381: error: ‘PP_VERSION’ undeclared here (not in a function)
eight_ball.c:385: error: ‘PP_WEBSITE’ undeclared here (not in a function)
eight_ball.c: In function ‘init_plugin’:
eight_ball.c:409: error: ‘GETTEXT_PACKAGE’ undeclared (first use in this function)

```

I have not changed the .c file at all (it's still as it was when I downloaded it. I wanted to see if I can compile it before I go on translating it).

Can anybody help me solve this problem ? What do you guys need to know to be able to help me ?

It would be really great if I can get this working, I've searched on google and on this forum and maybe I'm a bad searcher (than sorry for that) but I did not find a solution to my problem.

---

### Post by dwhitney67 on 2010-01-18
I would start off by heeding the suggestion given here:
```

/usr/include/glib-2.0/glib/gi18n-lib.h:29:2: error: #error You must define GETTEXT_PACKAGE before including gi18n-lib.h. **Did you forget to include config.h**?

```

---

### Post by Gislinn on 2010-01-18
> **dwhitney67 said:**
> I would start off by heeding the suggestion given here:
```

/usr/include/glib-2.0/glib/gi18n-lib.h:29:2: error: #error You must define GETTEXT_PACKAGE before including gi18n-lib.h. **Did you forget to include config.h**?

```

Thanks for the reply, but like I said:

> **Gislinn said:**
> I have not changed the .c file at all (it's still as it was when I downloaded it. I wanted to see if I can compile it before I go on translating it).

This plugin is out already and they compiled it and since the plugin is working it must be something I'm doing wrong :-)

Also, I've already checked for the config.h and it is in the code (did not forget to include it) so I don't understand what's going on. :-(

---

### Post by ibuclaw on 2010-01-18
When you compile you must do with the -DGETTEXT_PACKAGE=blah compile flag - but usually that should be done transparently with the ./configure && make process.

---

