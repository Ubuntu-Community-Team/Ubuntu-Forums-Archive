---
title: "Create java application with glade ui"
date: 2009-01-14
forum: Programming Talk
---

### Post by hermes0710 on 2009-01-14
Hi all,
   I would like to get informed about the jar files i should use in a project I am developing using eclipse as ide in Java.

   I found some tutorials about how to bind the application with a glade interface but i got confused. I am supposed to use a class LibGlade which keeps being presented as deprecated by the compiler...

Is there a guideline about the libs/jars i should use?

Regards

---

### Post by Titan8990 on 2009-01-14
I recommend that you report this post and asked that it is moved to the "programming talk" forum where you are more likely to get assistance.

---

### Post by hermes0710 on 2009-01-14
> **Titan8990 said:**
> I recommend that you report this post and asked that it is moved to the "programming talk" forum where you are more likely to get assistance.

I totally agree. My bad... I checked only the Main categories. How am I supposed to report the thread (never mind, i found it).

---

### Post by Titan8990 on 2009-01-14
It is a little button under your name and avatar.

---

### Post by jespdj on 2009-01-14
Glade is for developing GTK+ user interfaces. Java has its own user interface library (Swing). You can't use Glade to create Swing UI's.

There is a [GTK+ binding to Java](http://java-gnome.sourceforge.net/), which you could use if you really would want to create a GTK+ application in Java.

I would, however, advise you to use Swing instead of GTK+ for a Java application, simply because Swing is Java's default GUI library, and it will make it easier to run your program on other platforms for which GTK+ is not readily available. One IDE that has a good UI builder for Swing is [NetBeans](http://www.netbeans.org/).

---

### Post by hermes0710 on 2009-01-14
> **jespdj said:**
> Glade is for developing GTK+ user interfaces. Java has its own user interface library (Swing). You can't use Glade to create Swing UI's.

There is a [GTK+ binding to Java](http://java-gnome.sourceforge.net/), which you could use if you really would want to create a GTK+ application in Java.

I would, however, advise you to use Swing instead of GTK+ for a Java application, simply because Swing is Java's default GUI library, and it will make it easier to run your program on other platforms for which GTK+ is not readily available. One IDE that has a good UI builder for Swing is [NetBeans](http://www.netbeans.org/).


I want to use gtk because I want the application to inherit gnome's theme, widgets etc. It's all about a gnome application so i am not that interested making it compatible for other platforms.

---

