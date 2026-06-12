---
title: "Java - Toolkits"
date: 2011-01-22
forum: Programming Talk
---

### Post by CaptainMark on 2011-01-22
This may be a stupid question but im totally new to java excuse the ignorance, do you still need to import specific gui toolkits, like in python i would import gtk.
I know java works differently, with the whole runtime environment thing, they say its completey cross platform even after compling, does this mean you can pull a toolkit that will work with the JRE weather on windows, mac or linux????
Again im totally new to java so try to keep it simple and just be nice if this is a stupid question.

---

### Post by lykeion on 2011-01-23
In Java you primarily use [Swing]("http://en.wikipedia.org/wiki/Swing_(Java)") for GUI development. It's included in the JDK and is platform independent both in terms of expression (Java) and implementation (Look-and-Feel).
The official [Swing Tutorial]("http://download.oracle.com/javase/tutorial/ui/features/components.html") is good start to find out its features.

---

### Post by fct on 2011-01-23
If you want to use another GUI toolkit apart from Swing (for example SWT), you need to bundle the required jars with your applications.

Those toolkits usually include deployment instructions in their documentation.

---

### Post by CaptainMark on 2011-01-23
I think ill stick to the basics, i want to use one that will be easy to learn and to find help for, and as a bonus work cross platform. the problem i wanted to avoid was that im learning C as well and i can find guides for C with other toolkits and i can find guides for GTK but being a real beginner to this language it would help to find a guide written by someone using C and GTK together, looks like i wont have that problem with java

---

