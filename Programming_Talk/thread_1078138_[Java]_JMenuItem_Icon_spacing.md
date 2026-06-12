---
title: "[Java] JMenuItem Icon spacing"
date: 2009-02-23
forum: Programming Talk
---

### Post by DocForbin on 2009-02-23
When I use an icon with JMenuIten there is annoying excessive space to the left. Anyone know how to get rid of it?

e.g.

[IMG]http://img218.imageshack.us/img218/7355/icon.png[/IMG]

---

### Post by myrtle1908 on 2009-02-23
I had this problem once.  Pretty sure you use insets.  Have a look here [http://forums.sun.com/thread.jspa?threadID=5327895&tstart=-4](http://forums.sun.com/thread.jspa?threadID=5327895&tstart=-4) ... should point you in the right direction.

---

### Post by DocForbin on 2009-02-23
> **myrtle1908 said:**
> I had this problem once.  Pretty sure you use insets.  Have a look here [http://forums.sun.com/thread.jspa?threadID=5327895&tstart=-4](http://forums.sun.com/thread.jspa?threadID=5327895&tstart=-4) ... should point you in the right direction.

Thanks. Ugly. Was hoping I missed something simple ;)

Doc <-- cursing Swing

---

### Post by DocForbin on 2009-02-23
Arg This is the 2nd or 3rd instance in one weekend of working on a Java app I've found default settings for swing/awt compoents ridiculous, and worse, not easily changeable. I love the cross-platform benefit of Java, but gui development on Linux is a a major pain in the ****.

---

### Post by cl333r on 2009-02-23
Unless you're not doing hello world like apps, gui development is always a pain, but things are getting better, too slowly though.

---

### Post by DocForbin on 2009-02-23
Just noticed there is no spacing problem with the default MetalLookAndFeel. I'm using NimbusLookAndFeel, and the UIManager.put("MenuItem.margin"...) hack doesn't seem to have any effect.

---

