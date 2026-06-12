---
title: "compiling gtk+-3.0 (C++/glade/eclipse)"
date: 2014-02-11
forum: Packaging and Compiling Programs
---

### Post by DeKugelschieber on 2014-02-11
Hi there,

I've got a (in my opinion) strange problem.
I'm trying to compile a simple C++/GTK+ application in eclipse on ubuntu 13.10. The UI itself was created in glade and is loaded from xml.
Everything works fine, until I try to use some functions (don't know which are affected exactly), in my case gtk_window_close() in a signal handler:

```

extern "C" void saveSettings(GtkWidget* widget, gpointer data){
    gtk_widget_close(settingsWindow);
}

```

I've set up gcc and g++ with the pkg-config tool:

```

`pkg-config --cflags gtk+-3.0` -export-dynamic // compiler
`pkg-config --libs gtk+-3.0` -export-dynamic // linker

```

As I said it works fine as long as i keep out that function... else the linker throws "function was not defined in this scope" (related to extern "C"?).
I've installed libgtk 3 and 2 (dev), glade, glade-gnome and maybe a few more.
Full code: [http://pastebin.com/Sq3JTbxz](http://pastebin.com/Sq3JTbxz)

The error message I get:

```

g++ -std=c++11 `pkg-config --cflags gtk+-3.0` -export-dynamic -D__GXX_EXPERIMENTAL_CXX0X__ -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -I/usr/include/gtk-3.0 -I/usr/include/glib-2.0 -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/main.d" -MT"src/main.d" -o "src/main.o" "../src/main.cpp"
../src/main.cpp: In function &#8216;void saveSettings(GtkWidget*, gpointer)&#8217;:
../src/main.cpp:22:33: error: &#8216;gtk_widget_close&#8217; was not declared in this scope
  gtk_widget_close(settingsWindow);

```

Greetings Marvin

---

### Post by spjackson on 2014-02-13
Welcome to the forums.
 gtk_widget_close is not the same as gtk_window_close. I don't program with gtk, but it appears to me that your code should read
```

extern "C" void saveSettings(GtkWidget* widget, gpointer data) {
         gtk_window_close(settingsWindow);
}

```

---

### Post by DeKugelschieber on 2014-02-13
No, does not work neither.
But I switched to gtkmm anyway and now use

```

window->hide();

```

instead. Works.

But thanks for your help :)

---

