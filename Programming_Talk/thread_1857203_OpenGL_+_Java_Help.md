---
title: "OpenGL + Java Help"
date: 2011-10-09
forum: Programming Talk
---

### Post by roadkillguy on 2011-10-09
Hi,

I've been trying to write a java app with OpenGL.  I've used OpenGL a bunch with c++, so that's not the problem.  The problem is, I don't understand the #include equivalent in Java.  C++ makes so much more sense at this point :D

Basically, where does jogl.jar go and how do I include it in my program?

Tutorials online just say "Put it in your $CLASSPATH," and I don't know where that is because 'echo $CLASSPATH' returns nothing.

Thanks for the help.

---

### Post by PaulM1985 on 2011-10-10
Do you program using an IDE?  I use Netbeans.  Netbeans allows you to add libraries that your application is to use, which means that you don't have to mess around with class paths, it will do it all for you.

Also, I would recommend using lwjgl rather than jogl.  I had problems with jogl on some computers.  There is a link to their site here: [http://lwjgl.org/](http://lwjgl.org/)

Setting up is pretty simple.  There is a tutorial on their site.

Paul

---

### Post by DarkAmbient on 2011-10-10
+1 on lwjgl

as paul said aswell, you need to link the libraries in your IDE. If you compile from the terminal I think it's something like 

```
javac -classpath="/some/dir/to/library.jar" yourproject.class
```

Not too sure on the terminal-way thought...

---

### Post by roadkillguy on 2011-10-10
I'll look at lwjgl then.

Also, does using these libraries mean the people who view the applet need them as well?  I don't know how that works in java.

---

### Post by PaulM1985 on 2011-10-10
Yes.  I am not sure how it works with applets.  With a normal desktop application you need to provide your opengl .jar files as well as the native libraries that are used.  So taking ubuntu as an example, you would provide your .jar, the jars for lwjgl as well as the native .so files.

In an applet, I am not sure how you would do it.  Also, the download would be about 10MB-ish, which could potentially take a while for the user to get.

Paul

---

### Post by roadkillguy on 2011-10-10
I've seen 3D in applets before, there's no doubt about it.  (RuneScape or Minecraft)  They've gotta be doing something.

Edit: [http://www.lwjgl.org/applet/]("http://www.lwjgl.org/applet/") looks like it downloads lwjgl before you run it.  It crashes for me, but it looks promising.

---

