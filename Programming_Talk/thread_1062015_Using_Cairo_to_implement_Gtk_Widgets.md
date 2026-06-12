---
title: "Using Cairo to implement Gtk Widgets"
date: 2009-02-06
forum: Programming Talk
---

### Post by chanders on 2009-02-06
Is it possible to overwrite the drawing method for Gtk widgets so that the widget is now rendered using Cairo? That way you can maintain the EXACT functionality but be able to theme the controls without having to re-invent the wheel and rewrite the whole control from scratch. I'm using PyGtk.

?

---

### Post by Darkhack on 2009-02-06
As of GTK+ 2.8, all the widgets are already rendered with Cairo.  The theme is controlled by the users settings and it's not recommenced that the application override those settings.  However you can do it at start up.  Make sure that the gtkrc file exists for the theme and launch the program like so.

```
GTK2_RC_FILES=$HOME/.themes/my-custom-theme/gtkrc my-program-name
```

You can also draw your own widgets and use GTK Events to handle the user interaction.

---

### Post by chanders on 2009-02-06
I would like to code each widget/control independently. Not apply a whole theme to the app I am writing. Is there a way to overwrite the widget's drawing method?

---

### Post by Darkhack on 2009-02-06
Not that I'm aware of.  You might have to code your own custom widget for that kind of functionality.  You can always pull the code from GTK+ for the specific widget you want to modify and then edit it to suit your needs.  AFAIK, there isn't any way to override the widget that's built into GTK other than writing a new widget yourself.  Thankfully the event system in GTK+ is very nice so you won't have to duplicate too much effort.

---

