---
title: "Gtkmm 3.0"
date: 2012-01-06
forum: Programming Talk
---

### Post by theopfor on 2012-01-06
Any way to use Gtkmm faster? I hate using multiple files. I have been trying out this one person's method that I saw on youtube. Instead of using multiple files, you just use ```
Gtk::Button button;
```

The problem is, I can't seem to edit the widgets. Any help?

---

### Post by theopfor on 2012-01-07
Please?

---

### Post by pbrane on 2012-01-07
I'm not sure what you're asking here. That code just creates a button. What does that have to do with multiple files? How are you trying to edit widgets?

And really I can't remember any Gtkmm apps that I've written in one file. I wrote a small app with 46 source files containing about 10,000 lines of code.

---

### Post by theopfor on 2012-01-07
Okay, so the code I provided, creates a simple button, like you stated. That code doesn't have to be in it's own file, with a struct.  I can't edit anything with it, when using that code alone, to create the button. So, how would I be able to use things like "pack_start" or "add" when using the code I provided, all in one file.

```
    Gtk::Window window;
    Gtk::Button     save();
    Gtk::Button     open();
    Gtk::Button     quit();
    Gtk::Notebook   tabs();
    Gtk::TextView   text();
    Gtk::Table      tbl(3, 2, false);

```

I have all those widgets in main.cpp. I don't want to have to go and create 6 files, just to create those widgets.

---

### Post by cgroza on 2012-01-07
The code that you provided does not even create widgets.
It only declares the some variable as being of a certain type.

---

### Post by theopfor on 2012-01-07
I'm very confused then. So, in that case, how would I make whole programs, all in one file?

---

### Post by pbrane on 2012-01-08
Have a look at this.
[http://developer.gnome.org/gtkmm-tutorial/stable/]("http://developer.gnome.org/gtkmm-tutorial/stable/")

---

### Post by theopfor on 2012-01-08
Thanks everyone!

---

