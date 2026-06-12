---
title: "GCJ and gnome"
date: 2008-02-29
forum: Programming Talk
---

### Post by tadasv on 2008-02-29
Hi,

I am trying to compile a java gnome example with gcj and it does not compile. This is how i compile it:

gcj --classpath=/usr/share/java/gtk2.10.jar:[A/usr/share/java/gnome2.12.jar:/usr/share/java/glade2.12.jar -lgtkjar2.10 -lgnomejar2.12 -lgladejar2.12 -o ExampleGNOME --main=ExampleGNOME ExampleGNOME.java

And I get errors like this: The import org.gnu cannot be resolved

The example java program is taken from here 
[http://www.linuxjournal.com/article/8111](http://www.linuxjournal.com/article/8111)

So does anyone know how to solve this problem? Thanks.

---

