---
title: "[SOLVED] GTK UI w/ Java"
date: 2008-05-24
forum: Programming Talk
---

### Post by mevets on 2008-05-24
I am trying to start writing GUI applications with java. I found a tutorial ([http://www.linuxjournal.com/article/8111](http://www.linuxjournal.com/article/8111)) that explained I needed libgconf-java, libglade-java, libgnome-java and libgtk-java so I went ahead and installed those under hardy. My code is as follows:
```

import java.io.IOException;

import org.gnu.glade.LibGlade;
import org.gnu.gtk.Gtk;
import org.gnu.gtk.event.GtkEvent;

public class ExampleGNOME {
 private LibGlade libglade;
 private static final String GLADE_FILE =
                               "ExampleGNOME.glade";

 public ExampleGNOME () throws IOException {
  libglade = new LibGlade(GLADE_FILE, this);
 }

 public void on_noButton_released(GtkEvent event) {
  Gtk.mainQuit();
  System.exit(1);
 }

 public void on_yesButton_released(GtkEvent event) {
  Gtk.mainQuit();
  System.exit(0);
 }

 public static void main(String args[]) {
  ExampleGNOME gui;

  Gtk.init(args);
  try {
   gui = new ExampleGNOME();
  } catch (IOException e) {
   System.err.println(e);
   System.exit(1);
  }
 Gtk.main();
 }
}

```
I get this error when I run it.
```

Exception in thread "main" java.lang.NoClassDefFoundError: org.gnu.gtk.Gtk
   at java.lang.Class.initializeClass(libgcj.so.81)
   at ExampleGNOME.main(ExampleGNOME.java:29)
Caused by: java.lang.NullPointerException
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at java.security.SecureClassLoader.defineClass(libgcj.so.81)
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...1 more

```
I figure I am missing an import or I need to install more packages. In any cases, does anyone know where things are going wrong?

---

### Post by luisromangz on 2008-05-25
If the errors are at runtime, check that the JRE you are using to run your program is the same the libraries where installed into.

---

### Post by xlinuks on 2008-05-25
"I am trying to start writing GUI applications with java."
Java has built-in GUI libraries which are no longer slow, and in some cases are way better (for instance there are useful Java GUI classes like JTable which aren't present by default in Gnome's GTK), so I would suggest using them unless you have a special reason for using those you mentioned.
Thus you'd only need to install Java SDK to start developing, "sudo apt-get install sun-java6-jdk" and you're done.
If you need help on starting using Java's Swing libraries just ask.
A very good resource (and large) is "The Java Tutorial", google for it and you'll quickly find it online and for offline browsing, it's free.

PS: I hope you also know the drawbacks/problems of using and porting Java applications that use bindings to other GUI libraries.

---

### Post by Zugzwang on 2008-05-25
> **mevets said:**
> 
I figure I am missing an import or I need to install more packages. In any cases, does anyone know where things are going wrong?

Can you please tell us how you compiled your program and how you try to run it? It looks quite suspicious to me that the compiler doesn't have problems finding the class but the runtime environment has it.

I second xlinuks comment although this is certainly not the answer you wanted. ;-)

---

### Post by NormR2 on 2008-05-25
> Exception in thread "main" java.lang.NoClassDefFoundError: 
org.gnu.gtk.Gtk
The java program is telling you it can't find the definition to the class listed in the error message on the classpath. The missing class is probably in a jar file. Find the jar file with that class in it and add it to the classpath for the java command:

```
java -classpath <pathtojar>:. <rest of stuff>
```

---

### Post by geirha on 2008-05-25
Are you using gcj or sun java?

I tried compiling and running your code with a simple ExampleGNOME.glade-file, using [sun-java6-jdk](apt://sun-java6-jdk) and it seems to work:
```

$ javac -classpath /usr/share/java/gtk2.10.jar:/usr/share/java/glade2.12.jar ExampleGNOME.java
Note: ExampleGNOME.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
$ LD_LIBRARY_PATH=/usr/lib/jni java -classpath /usr/share/java/gtk2.10.jar:/usr/share/java/glade2.12.jar:/usr/share/java/glib0.4.jar:. ExampleGNOME

```

---

### Post by mevets on 2008-05-25
I am compiling it within eclipse. I am usiing java.1.5.0-gcj-4.2-1.5.0.0 as my JRE. The external jars I added were from /usr/share/java and were gtk2.10 and glade2.12. I'm thinking this was the wrong place to add jars from?

---

### Post by geirha on 2008-05-25
Does it have to be gcj? If not, try with [sun-java6-jdk](apt://sun-java6-jdk). And run ```
sudo update-java-alternatives --set java-6-sun
``` in a terminal, after installing the jdk.

I've programed a bit java using sun's java, but never gcj. And I can't figure out how to compile it with gcj, (not even a simple "Hello, World!" seems to compile for me)

---

### Post by kknd on 2008-05-25
Hi

> **xlinuks said:**
> 
Java has built-in GUI libraries which are no longer slow, and in some cases are way better (for instance there are useful Java GUI classes like JTable which aren't present by default in Gnome's GTK),

WHat can the JTable can do that a GtkTreeView + GtkTreeModel can't?

> **xlinuks said:**
> 
 so I would suggest using them unless you have a special reason for using those you mentioned.


Well, a Swing hello world can take 20mb of memory, while a GTK one take less than 2mb. 

> **xlinuks said:**
> 
Thus you'd only need to install Java SDK to start developing, "sudo apt-get install sun-java6-jdk" and you're done.
If you need help on starting using Java's Swing libraries just ask.
A very good resource (and large) is "The Java Tutorial", google for it and you'll quickly find it online and for offline browsing, it's free.

PS: I hope you also know the drawbacks/problems of using and porting Java applications that use bindings to other GUI libraries.


That's true. There is some fine documentation, and its much more easy to use Swing, to avoid other dependencies.

For ease, I would use Swing, but for performance / better UI (GTK have a lot more features than plain Swing) I would use GTK too.

**mevets**, the libraries must be in your classpath, and the native library must be loaded too (I think thats not your case, since there are errors on the initial "imports".

---

### Post by mevets on 2008-05-25
thanks for that tip geirha. I installed sun's jdk. When I switched JRE's it was java-6-sun not sun-6-sun, that was probably a typo but it compiles now.

---

