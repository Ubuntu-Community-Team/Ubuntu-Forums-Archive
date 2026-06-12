---
title: "Problems in simple array program( beginner)."
date: 2009-07-09
forum: Programming Talk
---

### Post by ROBERT ALCATARA on 2009-07-09
I am a beginner in Java programming I tried to compile this programme and found the following problems, Please help me.

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package daysofweek;

/**
 *
 * @author c1272e
 */
public class DaysOfWeek {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        String daysofweek[] = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};

        for(int i = 0; i < daysofweek.length; i++){
            System.out.println( daysofweek[i] );
        }

    }

}


The messages in the otuput window are as follows,


java.lang.ClassFormatError: Duplicate field name&signature in class file daysofweek/DaysOfWeek
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: daysofweek.DaysOfWeek.  Program will exit.
Exception in thread "main" 
Exception in thread "main" Java Result: 1
BUILD SUCCESSFUL (total time: 3 seconds)

Can some body read through my code and point out what I left out. Thank you.

[EMAIL="ROBINSON_8331@HOTMAIL.COM"]ROBINSON_8331@HOTMAIL.COM[/EMAIL]

---

### Post by iver2435 on 2009-07-09
I believe the problem is that this line:

```
String daysofweek[] = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};
```

should actually read:

```
String[] daysofweek = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};
```

BTW, I don't mind helping a brother out, but this forum is mainly to discuss questions related to Ubuntu and Linux. I'm sure you could find much more targeted help on a Java forum.

---

### Post by lavinog on 2009-07-09
> **iver2435 said:**
> 
BTW, I don't mind helping a brother out, but this forum is mainly to discuss questions related to Ubuntu and Linux. I'm sure you could find much more targeted help on a Java forum.

There is a section in the forums for programing talk

---

### Post by sdlynx on 2009-07-09
> **iver2435 said:**
> I believe the problem is that this line:

```
String daysofweek[] = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};
```

should actually read:

```
String[] daysofweek = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};
```

BTW, I don't mind helping a brother out, but this forum is mainly to discuss questions related to Ubuntu and Linux. I'm sure you could find much more targeted help on a Java forum.

I think it should actually be ```
String[] daysofweek = new String[7] = { “Mon”, “Tue”, “Wed”, “Thu”, “Fri”, “Sat”, “Sun”};
```

---

### Post by myrtle1908 on 2009-07-10
I'm no sure what version of Java you are using to compile but that code will compile with v5.  The code is not great however.  For example, your package name is 'daysofweek', your classname is 'DaysOfWeek' and you have a variable named 'daysofweek'.  Whilst technically legal (in Java 5 and perhaps other versions) it is poor practice.

The stack trace you posted earlier seems to indicate that there is a clash:-

```
java.lang.ClassFormatError: Duplicate field name&signature in class file daysofweek/DaysOfWeek
```

Finally, there is **nothing** wrong with the format of your array declaration.

---

### Post by sdlynx on 2009-07-10
oh sorry, that's always how I've learned it (and how it is on java.sun.com)

---

