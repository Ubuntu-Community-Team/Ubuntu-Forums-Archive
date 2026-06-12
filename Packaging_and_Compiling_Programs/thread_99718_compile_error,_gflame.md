---
title: "compile error, gflame"
date: 2005-12-06
forum: Packaging and Compiling Programs
---

### Post by fourchannel on 2005-12-06
i'm trying to install glame 0.4 for gkrellm, and just fixed the ./configure probs with

gcc

GTK (1.2 - didn't know 2.0 wouldn't work lol)


so i finally get a green light on the congifure, and then i proceed on to make and it gives me this:  From what I can tell it hit the fan when it came to popt.

```
$ make
make  all-recursive
make[1]: Entering directory `/home/limewire/tmp/gflame-0.4'
Making all in intl
make[2]: Entering directory `/home/limewire/tmp/gflame-0.4/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limewire/tmp/gflame-0.4/intl'
Making all in po
make[2]: Entering directory `/home/limewire/tmp/gflame-0.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limewire/tmp/gflame-0.4/po'
Making all in src
make[2]: Entering directory `/home/limewire/tmp/gflame-0.4/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../intl      -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include         -g -O2 -Wall -c main.c
main.c:24:18: error: popt.h: No such file or directory
main.c: In function ‘main’:
main.c:47: error: ‘poptContext’ undeclared (first use in this function)
main.c:47: error: (Each undeclared identifier is reported only once
main.c:47: error: for each function it appears in.)
main.c:47: error: syntax error before ‘optCon’
main.c:50: error: array type has incomplete element type
main.c:51: error: ‘POPT_ARG_INT’ undeclared (first use in this function)
main.c:57: error: ‘POPT_ARG_VAL’ undeclared (first use in this function)
main.c:61: error: ‘POPT_ARG_STRING’ undeclared (first use in this function)
main.c:66: error: ‘POPT_AUTOHELP’ undeclared (first use in this function)
main.c:66: error: syntax error before ‘{’ token
main.c:67: error: syntax error before ‘}’ token
main.c:50: warning: unused variable ‘optionsTable’
main.c:48: warning: unused variable ‘rc’
main.c:41: warning: unused variable ‘rgb’
main.c:40: warning: unused variable ‘range_adjustment’
main.c:39: warning: unused variable ‘range’
main.c:38: warning: unused variable ‘drawing_area’
main.c: At top level:
main.c:70: error: syntax error before string constant
main.c:70: warning: type defaults to ‘int’ in declaration of ‘bindtextdomain’
main.c:70: error: conflicting types for ‘bindtextdomain’
/usr/include/libintl.h:86: error: previous declaration of ‘bindtextdomain’ was here
main.c:70: warning: data definition has no type or storage class
main.c:71: error: syntax error before string constant
main.c:71: warning: type defaults to ‘int’ in declaration of ‘textdomain’
main.c:71: error: conflicting types for ‘textdomain’
/usr/include/libintl.h:81: error: previous declaration of ‘textdomain’ was here
main.c:71: warning: data definition has no type or storage class
main.c:74: warning: type defaults to ‘int’ in declaration of ‘gtk_set_locale’
main.c:74: error: conflicting types for ‘gtk_set_locale’
/usr/include/gtk-1.2/gtk/gtkmain.h:76: error: previous declaration of ‘gtk_set_locale’ was here
main.c:74: warning: data definition has no type or storage class
main.c:78: error: syntax error before ‘&’ token
main.c:78: warning: type defaults to ‘int’ in declaration of ‘gtk_init’
main.c:78: error: conflicting types for ‘gtk_init’
/usr/include/gtk-1.2/gtk/gtkmain.h:72: error: previous declaration of ‘gtk_init’ was here
main.c:78: warning: data definition has no type or storage class
main.c:81: warning: type defaults to ‘int’ in declaration of ‘gdk_rgb_init’
main.c:81: error: conflicting types for ‘gdk_rgb_init’
/usr/include/gtk-1.2/gdk/gdkrgb.h:42: error: previous declaration of ‘gdk_rgb_init’ was here
main.c:81: warning: data definition has no type or storage class
main.c:82: error: syntax error before ‘(’ token
main.c:83: error: syntax error before ‘(’ token
main.c:85: error: syntax error before string constant
main.c:85: warning: type defaults to ‘int’ in declaration of ‘add_pixmap_directory’
main.c:85: error: conflicting types for ‘add_pixmap_directory’
support.h:51: error: previous declaration of ‘add_pixmap_directory’ was here
main.c:85: warning: data definition has no type or storage class
main.c:86: error: syntax error before string constant
main.c:86: warning: type defaults to ‘int’ in declaration of ‘add_pixmap_directory’
main.c:86: error: conflicting types for ‘add_pixmap_directory’
support.h:51: error: previous declaration of ‘add_pixmap_directory’ was here
main.c:86: warning: data definition has no type or storage class
main.c:88: warning: type defaults to ‘int’ in declaration of ‘optCon’
main.c:88: warning: implicit declaration of function ‘poptGetContext’
main.c:88: error: ‘argc’ undeclared here (not in a function)
main.c:88: error: ‘argv’ undeclared here (not in a function)
main.c:88: error: ‘optionsTable’ undeclared here (not in a function)
main.c:88: error: initializer element is not constant
main.c:88: warning: data definition has no type or storage class
main.c:90: error: syntax error before string constant
main.c:90: warning: type defaults to ‘int’ in declaration of ‘poptSetOtherOptionHelp’
main.c:90: warning: data definition has no type or storage class
main.c:95: error: syntax error before numeric constant
main.c:95: warning: type defaults to ‘int’ in declaration of ‘exit’
main.c:95: error: conflicting types for ‘exit’
main.c:95: warning: data definition has no type or storage class
main.c:108: error: syntax error before numeric constant
main.c:108: warning: type defaults to ‘int’ in declaration of ‘exit’
main.c:108: error: conflicting types for ‘exit’
main.c:108: warning: data definition has no type or storage class
main.c:111: warning: type defaults to ‘int’ in declaration of ‘poptFreeContext’
main.c:111: warning: parameter names (without types) in function declaration
main.c:111: warning: data definition has no type or storage class
main.c:122: warning: type defaults to ‘int’ in declaration of ‘gflame’
main.c:122: error: conflicting types for ‘gflame’
main.c:31: error: previous declaration of ‘gflame’ was here
main.c:122: warning: initialization makes integer from pointer without a cast
main.c:122: error: initializer element is not constant
main.c:122: warning: data definition has no type or storage class
main.c:123: warning: type defaults to ‘int’ in declaration of ‘drawing_area’
main.c:123: warning: passing argument 1 of ‘lookup_widget’ makes pointer from integer without a cast
main.c:123: warning: initialization makes integer from pointer without a cast
main.c:123: error: initializer element is not constant
main.c:123: warning: data definition has no type or storage class
main.c:126: warning: type defaults to ‘int’ in declaration of ‘new_gflame’
main.c:126: warning: parameter names (without types) in function declaration
main.c:126: error: conflicting types for ‘new_gflame’
gflame.h:44: error: previous declaration of ‘new_gflame’ was here
main.c:126: warning: data definition has no type or storage class
main.c:128: error: syntax error before ‘if’
main.c:133: error: syntax error before ‘|’ token
main.c:135: warning: type defaults to ‘int’ in declaration of ‘gtk_widget_set_events’
main.c:135: error: conflicting types for ‘gtk_widget_set_events’
/usr/include/gtk-1.2/gtk/gtkwidget.h:546: error: previous declaration of ‘gtk_widget_set_events’ was here
main.c:135: warning: data definition has no type or storage class
main.c:137: warning: type defaults to ‘int’ in declaration of ‘gtk_widget_show’
main.c:137: warning: parameter names (without types) in function declaration
main.c:137: error: conflicting types for ‘gtk_widget_show’
/usr/include/gtk-1.2/gtk/gtkwidget.h:449: error: previous declaration of ‘gtk_widget_show’ was here
main.c:137: warning: data definition has no type or storage class
main.c:140: warning: type defaults to ‘int’ in declaration of ‘gflame_about’
main.c:140: error: conflicting types for ‘gflame_about’
main.c:33: error: previous declaration of ‘gflame_about’ was here
main.c:140: warning: initialization makes integer from pointer without a cast
main.c:140: error: initializer element is not constant
main.c:140: warning: data definition has no type or storage class
main.c:143: warning: type defaults to ‘int’ in declaration of ‘gflame_configuration’
main.c:143: error: conflicting types for ‘gflame_configuration’
main.c:32: error: previous declaration of ‘gflame_configuration’ was here
main.c:143: warning: initialization makes integer from pointer without a cast
main.c:143: error: initializer element is not constant
main.c:143: warning: data definition has no type or storage class
main.c:144: warning: type defaults to ‘int’ in declaration of ‘range’
main.c:144: warning: passing argument 1 of ‘lookup_widget’ makes pointer from integer without a cast
main.c:144: warning: initialization makes integer from pointer without a cast
main.c:144: error: initializer element is not constant
main.c:144: warning: data definition has no type or storage class
main.c:145: warning: type defaults to ‘int’ in declaration of ‘range_adjustment’main.c:145: warning: passing argument 1 of ‘gtk_range_get_adjustment’ makes pointer from integer without a cast
main.c:145: warning: initialization makes integer from pointer without a cast
main.c:145: error: initializer element is not constant
main.c:145: warning: data definition has no type or storage class
main.c:146: error: syntax error before ‘(’ token
main.c:153: warning: type defaults to ‘int’ in declaration of ‘gflame_animate’
main.c:153: warning: parameter names (without types) in function declaration
main.c:153: error: conflicting types for ‘gflame_animate’
gflame.h:41: error: previous declaration of ‘gflame_animate’ was here
main.c:153: warning: data definition has no type or storage class
main.c:164: warning: type defaults to ‘int’ in declaration of ‘gtk_main’
main.c:164: error: conflicting types for ‘gtk_main’
/usr/include/gtk-1.2/gtk/gtkmain.h:85: error: previous declaration of ‘gtk_main’ was here
main.c:164: warning: data definition has no type or storage class
main.c:167: error: syntax error before ‘return’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/limewire/tmp/gflame-0.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/limewire/tmp/gflame-0.4'
make: *** [all-recursive-am] Error 2
``` 
according to synaptic i have:

libpopt0 1.7-5
libpopt-dev 1.7-5

_______________________________
i dont have libcppopt installed.

any suggestions?

thanks

---

### Post by gord on 2005-12-07
have you tryed just using an older version of gcc? that will fix 90% of the make time bugs in my experiance. gcc-3.4 comes pre-installed on ubuntu if i remeber so just typing 
```

export CC=gcc-3.4

```
before ./configure will set it to use gcc-3.4 instead of whatever else.

of course if 3.4 is the only version you have installed then thats all useless ;)

---

### Post by fourchannel on 2005-12-09
installed 3.4 with synaptic and tried the export, but it still gives the error. :(

---

