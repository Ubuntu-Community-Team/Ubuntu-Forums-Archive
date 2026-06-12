---
title: "path search problem"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by JoseJesus on 2012-07-16
Hello, I'm a newbie to linux programming. I want to program in C with GTK.
 Working with CodeBlocks, libgtk2.0-dev installed.
 When compiling a test code I get a error message:  <gtk / gtk.h> file or directory does not exist.
 By manually search for this file, I find that at <user/include/gtk-2.0/gtk/gtk.k>, because that, i enter the directory <gtk-2.0> in search paths list from CodeBlocks
 New build, new error, now within <gtk.h>,   # include<gio/gio.h>. I found this file in <user/include/glib-2.0/gio/gio.h>.
 My solution does not solve the problem, there must be another way. Can anyone help? thank you

---

### Post by black veils on 2012-07-17
not sure i know what you mean, but could you be making an error here: 
```
/home/yourusername/is/the/path/to/file
```

---

