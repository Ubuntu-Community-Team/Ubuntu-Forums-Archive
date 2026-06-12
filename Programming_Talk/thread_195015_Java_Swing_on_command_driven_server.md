---
title: "Java Swing on command driven server"
date: 2006-06-12
forum: Programming Talk
---

### Post by jitesh on 2006-06-12
Can I run an application which is built with a java swing interface on the command driven ubuntu server.

---

### Post by daneel_olivaw on 2006-06-12
you mean by command line?.. all u have to do is having java installed.. but i guess it's not precicely what you wanted to know

---

### Post by gekkio on 2006-06-12
I believe it's not possible to do easily.
I tried SwingSet2 (a Swing example in Sun's Java JDK) on a Dapper server which doesn't have X.
```
Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at sun.java2d.HeadlessGraphicsEnvironment.getDefaultScreenDevice(HeadlessGraphicsEnvironment.java:65)
        at SwingSet2.main(SwingSet2.java:248)

```

If you have access to the source code, it's probably possible to modify the program to work on X and terminal environments (but it would probably be quite complex).

You could try X11 forwarding if you have another computer that's always online when you need to run the app.

---

### Post by jvictor on 2006-06-12
If u have ur graphics subsytem & libs installed on the server , u can run apps that use graphics (java.awt) to draw lines etc like jasper reports to generate PDFs and charts.
X **neednt** be running. just the X libs need to be there in place.

you get a java.awt.HeadlessException if the X libs are not present and try to run an app that uses windowing capabilites.

However when u execute a Swing based app on a server running in text mode , theres no display to handle the GUI hence it wont. 

To add on , Swing is 'local' to the machine .. so why would u want to run it onthe server ?

---

