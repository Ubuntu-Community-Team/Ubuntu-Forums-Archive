---
title: "Installing GTK+"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by adityaharish on 2013-06-05
I'm using Ubuntu 12.04 . I am trying to install GKT+3.4.4 on my system.
I get no error when I **[SIZE=2]*configure*[/SIZE]** it , implying that it has all the required dependencies.
But when I [SIZE=2]***make***[/SIZE] it I'm getting some error.


Code :

[SIZE=2]**aditya$:make**[/SIZE]
[SIZE=2]**make  all-recursive**[/SIZE]
[SIZE=2]**make[1]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4'**[/SIZE]
[SIZE=2]**Making all in po**[/SIZE]
[SIZE=2]**make[2]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/po'**[/SIZE]
[SIZE=2]**make[2]: Nothing to be done for `all'.**[/SIZE]
[SIZE=2]**make[2]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/po'**[/SIZE]
[SIZE=2]**Making all in po-properties**[/SIZE]
[SIZE=2]**make[2]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/po-properties'**[/SIZE]
[SIZE=2]**make[2]: Nothing to be done for `all'.**[/SIZE]
[SIZE=2]**make[2]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/po-properties'**[/SIZE]
[SIZE=2]**Making all in gdk**[/SIZE]
[SIZE=2]**make[2]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**  GEN    gdkconfig.h**[/SIZE]
[SIZE=2]**make  all-recursive**[/SIZE]
[SIZE=2]**make[3]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**Making all in x11**[/SIZE]
[SIZE=2]**make[4]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gdk/x11'**[/SIZE]
[SIZE=2]**make[4]: Nothing to be done for `all'.**[/SIZE]
[SIZE=2]**make[4]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gdk/x11'**[/SIZE]
[SIZE=2]**Making all in .**[/SIZE]
[SIZE=2]**make[4]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**  GEN    gdkconfig.h**[/SIZE]
[SIZE=2]**make[4]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**Making all in tests**[/SIZE]
[SIZE=2]**make[4]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gdk/tests'**[/SIZE]
[SIZE=2]**make[4]: Nothing to be done for `all'.**[/SIZE]
[SIZE=2]**make[4]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gdk/tests'**[/SIZE]
[SIZE=2]**make[3]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**make[2]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gdk'**[/SIZE]
[SIZE=2]**Making all in gtk**[/SIZE]
[SIZE=2]**make[2]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gtk'**[/SIZE]
[SIZE=2]**make[3]: Entering directory `/home/ketan/Downloads/gtk+-3.4.4/gtk'**[/SIZE]
[SIZE=2]**  CCLD   gtk-update-icon-cache**[/SIZE]
[SIZE=2]**/usr/lib/libgio-2.0.so.0: undefined reference to `g_list_copy_deep'**[/SIZE]
[SIZE=2]**/usr/lib/libgio-2.0.so.0: undefined reference to `g_type_ensure'**[/SIZE]
[SIZE=2]**/usr/lib/libgio-2.0.so.0: undefined reference to `g_variant_check_format_string'**[/SIZE]
[SIZE=2]**/usr/lib/libgio-2.0.so.0: undefined reference to `g_spawn_check_exit_status'**[/SIZE]
[SIZE=2]**collect2: error: ld returned 1 exit status**[/SIZE]
[SIZE=2]**make[3]: *** [gtk-update-icon-cache] Error 1**[/SIZE]
[SIZE=2]**make[3]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gtk'**[/SIZE]
[SIZE=2]**make[2]: *** [gtkbuiltincache.h] Error 2**[/SIZE]
[SIZE=2]**make[2]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4/gtk'**[/SIZE]
[SIZE=2]**make[1]: *** [all-recursive] Error 1**[/SIZE]
[SIZE=2]**make[1]: Leaving directory `/home/ketan/Downloads/gtk+-3.4.4'**[/SIZE]
[SIZE=2]**make: *** [all] Error 2**[/SIZE]
[SIZE=2][B]aditya$:

[/B]I have Glib2.34 installed in my system

Code :
[/SIZE]**aditya$:pkg-config --modversion glib-2.0**
[B]2.34.0
[/B][B]aditya$:

[/B]Can  anyone Please help me in resolving this problem?. I'm badly in need of GTK+ for my project .

Thanks & Regards
Aditya



[SIZE=2][SIZE=1][/SIZE][/SIZE]

---

### Post by Cheesemill on 2013-06-05
Do you have to use 3.4.4?

Version 3.4.1 is in the repositories and can be installed with at simple...
```
sudo apt-get install libgtk-3-0 libgtk-3-bin libgtk-3-dev
```

---

### Post by adityaharish on 2013-06-05
For some reason the project isn't working with 3.4.1 . I need 3.4.4 to use Webkit.

---

