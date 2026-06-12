---
title: "Your views on compiling Java to native machine code"
date: 2007-10-31
forum: Programming Talk
---

### Post by bluedalmatian on 2007-10-31
I was wondering what everyone's thought are on this?  I like Java from a programmers point of view - nice syntax, rich free standard lib, but from an end users point of view I feel its a bit of an ugly pain - the JVM often is troublesome to configure, it tends to be rather slow and clunky, and running in a VM somehow just doesnt feel right to me - it feels as if your programs cut off from the 'real' programs on the system.

I'm attracted to the idea of using gcj to compile Java to native binary. but I've only done it for toy programs not a big system so I dont know how well it scales?

Personally I think Sun ought to promote a dual approach to Java -"Java Native" (i.e write in Java & compile to native binary) and "Java Portable" (run in VM).  I think if it did this it would get far more people adaopting the language, writing libraries, and cementing Java as 'the' language to know.  I think a lot of people are turned off by Java's virtual machine approach, yet at the same time its undoubetly a major advantage. Its about time Sun "legitimatised" the gcj approach as an equally valid and supported way of using the Java platform.

What do you think?

While we're on the subject, I thought in Java 6, Swing used native OS widgets if the OS provided a suitable one, and only resorted to drawing its own if it didnt. So how come Swing GUI's in Java 6 still have that clunky Java look to them? That was huge mistake, they should have stuck with AWT.

---

### Post by Tomosaur on 2007-10-31
Java is JIT compiled - while it makes sense to compile to native binary before distribution, it actually just means that you have to keep releasing multiple binaries. The JVM does JIT compilation - I guess it would be beneficial to store the JIT-compiled binary for later use rather than compiling it every time the software is run - but in reality the JVM approach does have benefits, perhaps the biggest of those being the HotSpot Optimisation which occurs. This wouldn't really be possible in native binary programs - and can be seen as an advantage that the JVM brings to the table, among others.

Speed is not the only important factor, and while the JVM does give a speed penalty, this is always improving, and we still get to keep the benefits that the JVM gives us.

---

