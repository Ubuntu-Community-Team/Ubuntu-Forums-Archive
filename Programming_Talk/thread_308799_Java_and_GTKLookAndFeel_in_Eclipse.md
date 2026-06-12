---
title: "Java and GTKLookAndFeel in Eclipse"
date: 2006-11-28
forum: Programming Talk
---

### Post by Ariod on 2006-11-28
Hey guys,

I'm trying to learn Java GUI programming. The look of my application defaults to the plain Java "metal" look, I'd like it to look like other GTK applications. I followed [this guide]("hhttp://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html") but my Eclipse cannot find the following packages:

```

com.sun.java.swing.plaf.gtk.GTKLookAndFeel
com.sun.java.swing.plaf.motif.MotifLookAndFeel
com.sun.java.swing.plaf.windows.WindowsLookAndFeel

```

What can I do? Do I need some extra packages?

---

### Post by Ramses de Norre on 2006-11-28
Do you have sun's java? It's in there.

```
import com.sun.java.swing.plaf.gtk.*;
```

---

### Post by Ariod on 2006-11-29
> **Ramses de Norre said:**
> Do you have sun's java? It's in there.

I have the sun-java5-jdk package installed. But Eclipse  cannot find any packages starting with "com".

---

### Post by Ramses de Norre on 2006-11-29
Do you have eclipse set to the right jre in window > preferences > Java > Instaled JREs ?
You probably need to add a new JRE pointing to /usr/lib/jvm/java-1.5.0-sun-1.5.0.08 and make it active.

---

### Post by hod139 on 2006-11-29
See this [howto]("http://ubuntuforums.org/showthread.php?t=201378") for setting up eclipse and Sun's java.

---

### Post by Ben Sprinkle on 2006-11-29
You don't see the System L&F in the API. The GTK+, Motif, and Windows packages that it requires are shipped with the Java SDK as: 


com.sun.java.swing.plaf.gtk.GTKLookAndFeel
com.sun.java.swing.plaf.motif.MotifLookAndFeel
com.sun.java.swing.plaf.windows.WindowsLookAndFeel

Note that the path includes java, and not javax. 


--------------------------------------------------------------------------------
Note: The GTK+ L&F will only run on UNIX or Linux systems with GTK+ 2.2 or later installed, while the Windows L&F runs only on Windows systems. Like the Java (Metal) L&F, the Motif L&F will run on any platform.

---

### Post by kaamos on 2006-11-29
The Gtk+ l&f in swing is horrible atm. The next version of java should (I guess) change this though. I hope they get the theme support in shape.

If you don't need to create platform-independent programs, [java-gnome](http://java-gnome.sourceforge.net/cgi-bin/bin/view) is also an option.

---

