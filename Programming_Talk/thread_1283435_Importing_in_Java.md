---
title: "Importing in Java"
date: 2009-10-05
forum: Programming Talk
---

### Post by jejune2 on 2009-10-05
I'm trying to run a simple program that imports

import acm.program.*
import acm.graphics.*

and then displays "hello world."

Apparently I need to get the acm.jar package, which I've downloaded but I don't know how to "install."

How do I add these additional packages? Also are there many of these that need to be added every time I import or is there a large one with all of them? An explanation would be great, thanks.

---

### Post by Reiger on 2009-10-05
You do not have to &#8216;install&#8217; it, you must make sure that the classpath is set properly so it is found automatically. There are lots of tutorials about this (the Java classpath variable) on the web: try Google. ;)

---

### Post by jejune2 on 2009-10-05
I've tried 

java -classpath $/home/[username]/Desktop/acm.jar

but it doesn't seem to be doing anything. (I've tried both ways but should I extract or leave it compressed?)

I still get the Exception in thread "main" java.lang.NoClassDefFoundError: Start
Caused by: java.lang.ClassNotFoundException error.

---

### Post by Reiger on 2009-10-05
Well first of all the Classpath you set doesn't do what you assumed it would do (this has to do with the fact that the jar is now searched for in the jar because of how the jar URL scheme works). I really suggest you _do_ take the time to google & read a proper tutorial on this; because it has implications beyond loading classes when you get to the proper way of loading icons and similar resources.

---

