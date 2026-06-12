---
title: "How do I compile Gtk applications?"
date: 2009-05-26
forum: Packaging and Compiling Programs
---

### Post by twistor96 on 2009-05-26
Hi,

I want to start learning GTK however when I tried to compile the sample application on  [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html) I get 
```
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```

I compiled it with
```

gcc HelloWorld.c -o base `pkg-config --cflags --libs gtk+-2.0`

```

I guess I haven't got the gtk development files installed or something, but I can't find them anywhere in synaptic.


(Using ubuntu 9.04)

---

### Post by bhagabhi on 2009-05-26
Take a look for the package libgtk2.0-dev, that should do it.

---

