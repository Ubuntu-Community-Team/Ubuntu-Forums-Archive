---
title: "java troubles"
date: 2006-10-12
forum: Programming Talk
---

### Post by baitman on 2006-10-12
Hi,

First year comp sci student trying desperately to get java working under ubuntu. 'javac' works fine but when i try and run mt java using 'java hell' (the name of my .java file) i get this


```
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorlApp.class
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: HelloWorlApp.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

I have absolutely no clue what it means and my code is fine, its only supposed to print out hell world

```
/** 
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */
class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}

```

Can anyone help me?

regards

---

### Post by taehher on 2006-10-12
Is the name of the file HelloWorldApp.java, if not you will get an error the name of the file must match the name of the public class described within it.

---

### Post by rekahsoft on 2006-10-12
first off i would recommend you use the jdk made by Sun Microsystems instead of GCJ (Gnu Compiler for Java). and like taehher said i think you have the class name wrong.

---

### Post by amo-ej1 on 2006-10-13
in order to chance the jdk used, you might want to check how to use update-alternatives

---

### Post by Blacktalon on 2006-10-13
Again like they said it looks like the class name wrong.

But did you actually put in 'java hell' if that is the case then yes it will pull up that error it wouldn't be the class name for the class name need to be what your public class name is.

---

### Post by hod139 on 2006-10-15
See this [thread]("http://ubuntuforums.org/showthread.php?t=201378") for setting up Sun's java (you can ignore the eclipse stuff if you don't want eclipse).

Also, as someone else mentioned, with Java the filename has to equal the class name.  So, to compile you would type:
```
javac HelloWorldApp.java 
```and to run
```
java HelloWorldApp  
```

---

