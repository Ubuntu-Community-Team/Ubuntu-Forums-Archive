---
title: "libjava-gnome-java problems"
date: 2009-04-07
forum: Programming Talk
---

### Post by Renault # on 2009-04-07
I installed libjava-gnome-java from Synaptic, but I don't know how to get it to work on Ubuntu. What I mean is that I don't know how to set it up so that import statements like

```

import org.gnome.gdk.Event;
import org.gnome.gtk.Gtk;

```

will work. 

Has anyone done this? I'm not much of a Linux boffin. :(

Thanks

---

### Post by myrtle1908 on 2009-04-07
You need to reference the relevant libraries.  Where are the gnome/gtk JAR files located?  Are you using an IDE like Eclipse?  If so you need to add the JARs to the build path.

---

### Post by HotCupOfJava on 2009-04-08
The problem isn't directly related to Linux. This would happen on any OS. You need to make sure that the .jar files containing the classes you need are added to the java classpath at compile and runtime. There are several ways to do this. The least intrusive (but most annoying due to the extra typing) is to actually set the classpath as you run the javac and java commands: 

```
javac -classpath "directoryx/directoryy/mylibrary.jar:." MySourceFile.java
```

then to run the same:

```
java -classpath "directoryx/directoryy/mylibrary.jar:." MySourceFile
```

---

