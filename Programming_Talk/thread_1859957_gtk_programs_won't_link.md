---
title: "gtk programs won't link"
date: 2011-10-14
forum: Programming Talk
---

### Post by tbastian on 2011-10-14
I upgraded to 11.10 this morning, now none of my gtk/gtkmm programs refuse to link properly! I'm sure all the proper libraries are installed (the dev versions of gtk+-2.0, gtk+-3.0 gtkmm-2.4) and pkg-config is returning the following flags:
```
trevor@deep-thought:~/src/convert/src$ pkg-config --libs gtk+-3.0 --cflags
-pthread -DGSEAL_ENABLE -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gtk-3.0  -pthread -lgtk-3 -lgdk-3 -latk-1.0 -lcairo-gobject -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0
```
```
trevor@deep-thought:~/src/convert/src$ pkg-config --libs gtk+-2.0 --cflags
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0
```

Here are the sort of errors I get:
```

trevor@deep-thought:~/src/convert/src$ gcc -Wall `pkg-config --cflags gtk+-3.0 gmodule-2.0` -g -O2 `pkg-config --libs gtk+-3.0 gmodule-2.0`  -o convert callbacks.o data.o frl_decode.o main.o merge.o  -lpthread
main.o: In function `main':
/home/trevor/src/convert/src/main.c:22: undefined reference to `gtk_init'
/home/trevor/src/convert/src/main.c:24: undefined reference to `gtk_builder_new'
/home/trevor/src/convert/src/main.c:27: undefined reference to `gtk_builder_add_from_file'
/home/trevor/src/convert/src/main.c:35: undefined reference to `gtk_widget_get_type'
/home/trevor/src/convert/src/main.c:35: undefined reference to `gtk_builder_get_object'
/home/trevor/src/convert/src/main.c:35: undefined reference to `g_type_check_instance_cast'
/home/trevor/src/convert/src/main.c:36: undefined reference to `gtk_builder_get_object'
/home/trevor/src/convert/src/main.c:36: undefined reference to `g_type_check_instance_cast'
/home/trevor/src/convert/src/main.c:37: undefined reference to `gtk_builder_get_object'
/home/trevor/src/convert/src/main.c:37: undefined reference to `g_type_check_instance_cast'
/home/trevor/src/convert/src/main.c:39: undefined reference to `g_type_check_instance_cast'
/home/trevor/src/convert/src/main.c:39: undefined reference to `g_signal_connect_data'
/home/trevor/src/convert/src/main.c:43: undefined reference to `gtk_builder_connect_signals'
/home/trevor/src/convert/src/main.c:45: undefined reference to `g_type_check_instance_cast'
/home/trevor/src/convert/src/main.c:45: undefined reference to `g_object_unref'
/home/trevor/src/convert/src/main.c:47: undefined reference to `gtk_widget_show'
/home/trevor/src/convert/src/main.c:49: undefined reference to `gtk_main'
/home/trevor/src/convert/src/main.c:29: undefined reference to `g_log'
/home/trevor/src/convert/src/main.c:30: undefined reference to `g_free'
```

any thoughts?

---

### Post by karlson on 2011-10-14
You seem to be missing all -L flags.  What does
```

pkg-config --libs-only-L <libs>

```
gives you.

---

### Post by tbastian on 2011-10-14
> **karlson said:**
> You seem to be missing all -L flags.  What does
```

pkg-config --libs-only-L <libs>

```
gives you.
A blank line
```

trevor@deep-thought:~/src/convert$ pkg-config --libs-only-L gtk+-3.0
 

```

Same deal with gtk+-2.0

edit: I just tried it on an older version of Ubuntu and I get the same thing result

---

### Post by tbastian on 2011-10-14
Hmmm, copying the flags from an older version of Ubuntu seems to work just fine. I guess my gtk+-2.0.pc and gtk+-3.0.pc files are incorrect. Has anybody else run into this issue? Should I file a bug report?

---

### Post by 23dornot23d on 2011-10-14
File a bug report as others are having problems too with gtk3

---

### Post by tbastian on 2011-10-14
> **23dornot23d said:**
> File a bug report as others are having problems too with gtk3

Have they been posting on ubuntu forums? I did a few searches before creating this thread and found nothing...

---

### Post by tbastian on 2011-10-17
So I have determined that it isn't actually gtk, but gcc. For whatever reason this command does not work:

```
gcc -Wall `pkg-config --cflags gtk+-3.0` `pkg-config --cflags gmodule-2.0` -lpthread -g -O2 `pkg-config --libs gtk+-3.0` `pkg-config --libs gmodule-2.0`  -o convert callbacks.o data.o frl_decode.o main.o merge.o
```

but this command DOES

```
gcc -o convert *.o -Wall `pkg-config --cflags gtk+-3.0` `pkg-config --cflags gmodule-2.0` -lpthread -g -O2 `pkg-config --libs gtk+-3.0` `pkg-config --libs gmodule-2.0`
```

The order of the command apparently is an issue.

How do I make that the default command in my makefile? I'm using auto-tools for my project.

---

### Post by t1497f35 on 2011-10-17
A lot of people are not aware that the tool chain defaults have changed in Oneiric, hence e.g. you have to put the "-libs" part at the end of the command line. More info here:

[https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition](https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition)

Note: the transition was scheduled for Natty but was postponed and adopted only starting with Oneiric. It's not just Ubuntu, all major distros are doing this.

---

### Post by tbastian on 2011-10-17
> **t1497f35 said:**
> A lot of people are not aware that the tool chain defaults have changed in Oneiric, hence e.g. you have to put the "-libs" part at the end of the command line. More info here:

[https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition](https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition)

Note: the transition was scheduled for Natty but was postponed and adopted only starting with Oneiric. It's not just Ubuntu, all major distros are doing this.

Thanks! It says in the article that:
> The --as-needed option also makes the linker sensitive to the ordering of libraries on the command-line. You may need to move some libraries later in the command-line, so they come after other libraries or files that require symbols from them. 
I'm using autotools and I really have no idea how to get the LDFLAGS to come after the input files... any ideas?

edit: At the moment, I don't care if its a temporary fix which simply disables the "--as-needed" option. I tried passing "-Wl, --no-as-needed" to the linker, and it didn't do anything, I'm assuming because --as-needed is also being passed, and it just picks one.

---

