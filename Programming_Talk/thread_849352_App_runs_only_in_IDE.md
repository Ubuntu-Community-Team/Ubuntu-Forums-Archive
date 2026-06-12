---
title: "App runs only in IDE"
date: 2008-07-04
forum: Programming Talk
---

### Post by hannehomuth on 2008-07-04
Hello Everybody,

I've a question which might be very simple but I didn't find anything. I've written an Java App and it runs well when I start it out of my IDE (Netbeans 6.1, if you wanna know). But when I want to start it from the command line I get an error which I can't resolve by myself. Here it is.

```

java -jar /home/jhomuth/projekte/LDAP/dist/LDAP.jar 
Exception in thread "main" java.lang.NoClassDefFoundError: de.sourcepark.ldap.JNDI_GUI
   at java.lang.Class.initializeClass(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: javax.swing.RowSorter not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/jhomuth/projekte/LDAP/dist/LDAP.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)

```

I mean, I can think what is wrong, because I'am able to read, but what shall I do here? I've tried to Comment all Lines where the javax.swing.rowSorter is in, but then he throw the next Error, the same like that only with  org.jdesktop.layout.GroupLayout. Does anyone has a Solution?

Sorry about my bad english :-)

---

### Post by henchman on 2008-07-04
Perhaps the IDE starts the java application launcher with additional arguments, eg. 
> 
-cp classpath
         Specify a list of directories, JAR archives, and ZIP archives  to
         search  for  class  files.  Class  path  entries are separated by
         colons (:). Specifying -classpath or -cp overrides any setting of
         the CLASSPATH environment variable.


there should be some output in you IDE how the program is launched...

if you have found the missing classes, you can also add them to your [classpath settings]("http://java.sun.com/docs/books/tutorial/deployment/jar/downman.html") inside your manifest file...

---

### Post by hannehomuth on 2008-07-04
I've printed out the java.library.path in my app and set it as the classpath while trying to run from shell.

```

java --classpath /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib:/usr/lib/jni -jar /home/jhomuth/projekte/LDAP/dist/LDAP.jar

```

But same s**t.

Any other ideas, or is the classpath and the library path a difference??

---

### Post by xlinuks on 2008-07-04
> Caused by: java.lang.ClassNotFoundException: javax.swing.RowSorter not found in gnu.gcj.runtime.SystemClassLoader
It turns out your system is configured to use the GNU Java (GCJ) from the command line, the way to change it is:
```

sudo update-alternatives --config java

```
NetBeans uses Sun's Java.

---

### Post by skafoelix on 2009-04-04
That just helped me out, thx!

---

