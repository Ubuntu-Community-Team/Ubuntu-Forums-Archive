---
title: "Glade and Java"
date: 2007-05-22
forum: Programming Talk
---

### Post by covert215 on 2007-05-22
I am using Glade to design the GUI for a program I am working on.  I have installed libgconf-java, libglade-java, libgnome-java and libgtk-java.  However, Glade does not give me the option of building in Java.  What could I be doing wrong?

---

### Post by T_W on 2007-05-22
Use the [Glade class]("http://java-gnome.sourceforge.net/4.0/doc/api/org/gnome/glade/Glade.html") to go directly from a Glade XML definition to a running Java GUI. 

No need to do code generation via Glade. You just load the Glade XML at runtime from the filesystem.

---

### Post by covert215 on 2007-05-22
edit: see below

---

### Post by T_W on 2007-05-22
Make sure the Java GTK bindings are on the CLASSPATH of your Java project.

The binding should be in a JAR file with GTK in the filename in the directory /usr/share/java.

---

### Post by covert215 on 2007-05-22
edit: see below

---

### Post by covert215 on 2007-05-22
edit: see below

---

### Post by covert215 on 2007-05-22
I've been playing around again....

IMPORTED:
import org.gnu.glade.GladeXMLException;
import org.gnu.glade.LibGlade;
import org.gnu.gtk.Gtk;

MAIN:
```
	public static void main(String[] args) {
		// running natively on
		// GNU libgcj 4.1.3 20070518 (prerelease) (Ubuntu 4.1.2-8ubuntu1
		GnomeGUI g;
		Gtk.init(args); //line 23
		try {
			g = new GnomeGUI();
		} catch (Exception e) {
			e.printStackTrace();
		}

		Gtk.main();

	}
```

LIBRARIES:
gtk2.10.jar
glade2.12.jar

ERRORS:
Exception in thread "main" java.lang.NoClassDefFoundError: org.gnu.gtk.Gtk
   at java.lang.Class.initializeClass(libgcj.so.71)
   at org.testing.GnomeGUI.main(GnomeGUI.java:23)
Caused by: java.lang.NullPointerException
   at java.lang.VMClassLoader.defineClass(libgcj.so.71)
   at java.lang.ClassLoader.defineClass(libgcj.so.71)
   at java.security.SecureClassLoader.defineClass(libgcj.so.71)
   at java.net.URLClassLoader.findClass(libgcj.so.71)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at java.lang.Class.initializeClass(libgcj.so.71)
   ...1 more

---

