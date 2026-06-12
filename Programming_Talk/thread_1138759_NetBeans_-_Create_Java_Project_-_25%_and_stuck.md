---
title: "NetBeans - Create Java Project - 25% and stuck"
date: 2009-04-26
forum: Programming Talk
---

### Post by winnomore on 2009-04-26
After installing NetBeans and Java JDK I had to fix the installation with the aptitude command I found in another post. However, when I open a new project for Java it brings up the progress bar while it is setting up the new project and hangs at 25%. Any ideas?

---

### Post by bradford.carl.smith on 2009-05-08
I'm having exactly the same problem, but I'll can add that it only appears to happen when selecting "Java->Java Application".  I can create "Java->Java Desktop Application" and "Java->Java Class Library" projects with no problem.

Furthermore, when I run the program from a terminal, I get these Gtk errors.  They're probably irrelevant, but maybe not...

```
(<unknown>:24219): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:24219): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:24219): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
```

I hope that helps figure out the problem.

Thanks,

Bradford

---

### Post by bradford.carl.smith on 2009-05-08
Oh, and I forgot to mention I'm running Ubuntu 8.04 with netbeans 6.0.1 installed from the netbeans package.

---

### Post by zimmerley on 2009-05-14
Hey There,
I had the same problems with creating new Java Projects.  I had used the applications->add/remove to download and install netbeans.  I'm pretty sure it's a bad install.  I uninstalled it using the applications->add/remove and then basically did it the long way.  Go to the netbeans website:

[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)

I selected the package with everything since I'd like to use more than just java, but I haven't tried to use the other packages.  Anyway, follow the install instructions here:

[http://www.netbeans.org/community/releases/65/1/install.html](http://www.netbeans.org/community/releases/65/1/install.html)

I can now create Java Apps!  Hope this works for you!

---

