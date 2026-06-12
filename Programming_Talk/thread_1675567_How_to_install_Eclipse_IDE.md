---
title: "How to install Eclipse IDE?"
date: 2011-01-25
forum: Programming Talk
---

### Post by jsel21 on 2011-01-25
Since I am already familiar with Eclipse from working with it at school, I want to try and install it on Ubuntu. I tried installing it from the software center but for some reason the workspace will not work, instead it will open up c++ files in the gedit text editor. Is downloading from the repository the best way?

---

### Post by GregBrannon on 2011-01-25
When does gedit open cpp files?  Can you create a project in Eclipse, write a simple program, and run it?  You likely have Ubuntu configured to open c++ files with gedit.  You can change that.  If you think it's a problem with the way your workspace is configured, try creating a new one.

As for installing Eclipse from the Software Center, doing it that way will enable Ubuntu to manage your updates, though that may leave you behind the latest Eclipse release.  Installing Eclipse "manually" is easy, usually works well, and Eclipse can manage its own updates.

---

### Post by Roberto_Lapuente on 2011-01-26
I know you say you use Eclipse because you already know it but you should totally try out netBeans. I have used both of them and i think net beans is much better, plus in netBeans you can create GUI without writing code.

---

### Post by fct on 2011-01-26
I download eclipse from the website, then extract it to /opt/eclipse and run it from the /bin subdirectory.

That way I use the latest eclipse when it's available.

---

### Post by GregBrannon on 2011-01-26
> **Roberto_Lapuente said:**
> I know you say you use Eclipse because you already know it but you should totally try out netBeans. I have used both of them and i think net beans is much better, plus in netBeans you can create GUI without writing code.

One's IDE preference is just that, a personal preference.  I've tried both Eclipse and NetBeans, and I have my preference, but I can't really explain why.  I just like one more than the other.

As for the specific capability to build GUIs without coding them "by hand:"

 - I recommend learning to code them by hand.  Learn Swing and use it enough to understand it well.

 - Eclipse has support for drag and drop GUI development. Eclipse has its own Visual Editor Project (see eclipse.org).  And Google bought WindowBuilder Pro and released it into the public domain for open source development (I may not have the legal terminology correct).  You can learn more about that by Googling.

---

