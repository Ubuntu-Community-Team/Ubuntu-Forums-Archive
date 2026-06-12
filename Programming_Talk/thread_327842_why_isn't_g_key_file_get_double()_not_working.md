---
title: "why isn't g_key_file_get_double() not working"
date: 2006-12-29
forum: Programming Talk
---

### Post by Faolan84 on 2006-12-29
Okay, I've looked it up on Google to find no reference on the subject but for some reason when I invoke g_key_file_get_double() the compiler chokes on an error.

here are the lines in question:
LINE 46: gdouble *key_frameskip; // varible declared.
LINE 86: key_frameskip = g_key_file_get_double (ini_foceus, "hacks", "frameskip", NULL); // everything is correct according to the manual

when compiled I get this error message:
main.c:86: error: incompatible types in assignment

The only reason why I would think this would happen is if this function has been depreciated, but I doubt that. Could there be something fundamentally wrong in my code?

---

### Post by llonesmiz on 2006-12-30
```
gdouble  g_key_file_get_double           (GKeyFile *key_file,
                                                                   const gchar *group_name,
                                                                   const gchar *key,
                                                                   GError **error);
```

According to the manual your code is not correct. You are trying to assign a double to a pointer to double. You need to change your variable declaration:

```
gdouble *key_frameskip; -> gdouble key_frameskip;
```

or dereference it:

```
key_frameskip = g_key_file_get_double (ini_foceus, "hacks", "frameskip", NULL); -> *key_frameskip = g_key_file_get_double (ini_foceus, "hacks", "frameskip", NULL);
```

---

### Post by Faolan84 on 2006-12-30
Hey. Thanks man that worked. But now I have a more interesting question: how come the same error doesn't show up with some similar code:

LINE 24: gint *key_video_scaling;
LINE 64: key_video_scaling = g_key_file_get_integer (ini_foceus, "video", "video_scaling", NULL);

This really seems more like an inconsistientcy and is the only datatype that does this in the g_key_file*() series, perhaps this is a bug since litterally every other function I've run across pretty much requires that the variable must be declared in reference.

---

### Post by llonesmiz on 2006-12-31
That is also wrong. You can assign an integer to a pointer but the result won't be what you desire. If you were to print the contents of the variable you would see that it's wrong. If you compile the program using -Wall you will see a warning.

```
[gint]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gint")        g_key_file_get_integer          ([GKeyFile]("file:///usr/share/gtk-doc/html/glib/glib-Key-value-file-parser.html#GKeyFile") *key_file,
                                             const [gchar]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gchar") *group_name,
                                             const [gchar]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gchar") *key,
                                             [GError]("file:///usr/share/gtk-doc/html/glib/glib-Error-Reporting.html#GError") **error);
```
The "gint" means that it returns an integer value, not a pointer. A function like this:

```
[gint]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gint")*       g_key_file_get_integer_list     ([GKeyFile]("file:///usr/share/gtk-doc/html/glib/glib-Key-value-file-parser.html#GKeyFile") *key_file,
                                             const [gchar]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gchar") *group_name,
                                             const [gchar]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gchar") *key,
                                             [gsize]("file:///usr/share/gtk-doc/html/glib/glib-Basic-Types.html#gsize") *length,
                                             [GError]("file:///usr/share/gtk-doc/html/glib/glib-Error-Reporting.html#GError") **error);
```
returns a list of integers and you need to assign its result to a pointer.

---

### Post by Faolan84 on 2006-12-31
Okay, I fixed all occurences of similar things in my program. Thanks for telling me that. By the way it does print out correct for the integer, but something tells me that since it does through up a waring with -Wall not to trust what I see. Thanks.

Also I seem to have a another problem now concerning the list of variables I created doing that. I'm trying to get them the print out to the command line for debugging purposes. Everything goes good until about the 10th or so g_print() containing a variable, where the program segfaults. I have not gotten any compiler warnings using -Wall at the lines in question. I've solved this problem by not listing all of the variables to print out but this is annoyance.

---

### Post by Faolan84 on 2007-01-01
heh. I fixed the g_print() problem. It wasn't with g_print() at all. I didn't terminate a g_build_path() with a NULL value at the end of the variable list causing a buffer overflow when I accessed variables taken from that file a certain number times. Thank the gods for the GNU Debugger.

---

