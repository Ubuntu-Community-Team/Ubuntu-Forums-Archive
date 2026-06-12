---
title: "Gaim plugin/module compilation woes"
date: 2007-01-25
forum: Programming Talk
---

### Post by ciscosurfer on 2007-01-25
I'm having some trouble getting some modules to compile.  I am running Gaim beta 6 and would like to add [these modules]("http://svana.org/kleptog/gaim/index.html") to the mix (view the page with Google cache if the site is down).

I'm getting pkg-config errors, relating to my path.  Hopefully someone can make some sense of this.  And I've already tried looking for gaim2.pc```
make

gcc -O2 -g -Wall `pkg-config --cflags glib-2.0 gaim2` -DPLUGIN_VERSION=0.5 -DPRIVATE_TZLIB -DCUSTOM_GTK   -c -o buddyedit.o buddyedit.c
Package gaim2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gaim2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gaim2' found
buddyedit.c:30:18: error: glib.h: No such file or directory
buddyedit.c:33:20: error: notify.h: No such file or directory
buddyedit.c:34:20: error: plugin.h: No such file or directory
buddyedit.c:35:18: error: util.h: No such file or directory
buddyedit.c:36:21: error: version.h: No such file or directory
buddyedit.c:38:61: error: debug.h: No such file or directory
buddyedit.c:39:53: error: request.h: No such file or directory
buddyedit.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
buddyedit.c:44: error: expected ‘)’ before ‘*’ token
buddyedit.c:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
buddyedit.c:216: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘buddyedit_account_filter_func’
buddyedit.c:229: error: expected ‘)’ before ‘*’ token
buddyedit.c:337: error: expected ‘)’ before ‘*’ token
buddyedit.c:368: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
buddyedit.c:392: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
buddyedit.c:423: error: expected ‘)’ before ‘*’ token
buddyedit.c:427: warning: data definition has no type or storage class
buddyedit.c:427: warning: type defaults to ‘int’ in declaration of ‘GAIM_INIT_PLUGIN’
buddyedit.c:427: warning: parameter names (without types) in function declaration
make: *** [buddyedit.o] Error 1
```

---

### Post by jblebrun on 2007-01-25
> **ciscosurfer said:**
> I'm having some trouble getting some modules to compile.  I am running Gaim beta 6 and would like to add [these modules]("http://svana.org/kleptog/gaim/index.html") to the mix (view the page with Google cache if the site is down).

I'm getting pkg-config errors, relating to my path.  Hopefully someone can make some sense of this.  And I've already tried looking for gaim2.pc```
make

gcc -O2 -g -Wall `pkg-config --cflags glib-2.0 gaim2` -DPLUGIN_VERSION=0.5 -DPRIVATE_TZLIB -DCUSTOM_GTK   -c -o buddyedit.o buddyedit.c
Package gaim2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gaim2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gaim2' found
buddyedit.c:30:18: error: glib.h: No such file or directory
buddyedit.c:33:20: error: notify.h: No such file or directory
buddyedit.c:34:20: error: plugin.h: No such file or directory
buddyedit.c:35:18: error: util.h: No such file or directory
buddyedit.c:36:21: error: version.h: No such file or directory
buddyedit.c:38:61: error: debug.h: No such file or directory
buddyedit.c:39:53: error: request.h: No such file or directory
buddyedit.c:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
buddyedit.c:44: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buddyedit.c:213: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
buddyedit.c:216: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;buddyedit_account_filter_func&#8217;
buddyedit.c:229: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buddyedit.c:337: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buddyedit.c:368: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
buddyedit.c:392: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
buddyedit.c:423: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buddyedit.c:427: warning: data definition has no type or storage class
buddyedit.c:427: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;GAIM_INIT_PLUGIN&#8217;
buddyedit.c:427: warning: parameter names (without types) in function declaration
make: *** [buddyedit.o] Error 1
```

You need to install gaim-dev, glib-dev, gtk-dev, and maybe a few other dev packages, too.

---

### Post by ciscosurfer on 2007-01-25
> **jblebrun said:**
> You need to install gaim-dev, glib-dev, gtk-dev, and maybe a few other dev packages, too.They are installed.  I know where gaim.pc is located (usr/lib/pkgconfig/gaim.pc) so all I need to do is modify my PKG_CONFIG_PATH environment variable and all should work okay.  Don't know where to find this varialbe though. :-(

Thanks for the reply :-)

---

### Post by jblebrun on 2007-01-25
> **ciscosurfer said:**
> They are installed.  I know where gaim.pc is located (usr/lib/pkgconfig/gaim.pc) so all I need to do is modify my PKG_CONFIG_PATH environment variable and all should work okay.  Don't know where to find this varialbe though. :-(

Thanks for the reply :-)

try

[COLOR="Silver"]
PKG_CONFIG_PATH=<path to gaimpc> ./configure
[/COLOR]

EDIT: 

Sorry, it's 
PKG_CONFIG=<path> ./configure

---

### Post by ciscosurfer on 2007-01-25
> **jblebrun said:**
> try

[COLOR=Silver]
PKG_CONFIG_PATH=<path to gaimpc> ./configure
[/COLOR]

EDIT: 

Sorry, it's 
PKG_CONFIG=<path> ./configureThere's no ./configure file, just a make file.  Totally stuck!!!

Thanks for helping out with my situation...any other hints or suggestions?

---

### Post by ciscosurfer on 2007-01-25
I think I got it.  I went into the make file, changed GAIM_NAME ?= gaim2 to GAIM_NAME ?= gaim

I saved the file, reran make, and it compiled!  Let's see if it'll install now.  Will post back if it doesn't.  Thanks for you help!

---

### Post by ciscosurfer on 2007-01-25
Everything works now :D

---

### Post by jblebrun on 2007-01-27
> **ciscosurfer said:**
> I think I got it.  I went into the make file, changed GAIM_NAME ?= gaim2 to GAIM_NAME ?= gaim

I saved the file, reran make, and it compiled!  Let's see if it'll install now.  Will post back if it doesn't.  Thanks for you help!

This is why software packagers should use autotools!!

What plugin is this?

---

