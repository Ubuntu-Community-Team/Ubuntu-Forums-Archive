---
title: "Development Sandboxing"
date: 2011-10-22
forum: Programming Talk
---

### Post by rojanu on 2011-10-22
What is the best to separate my development environment from my user environment. I don't want install JDK, Eclipse, Tomcat and MySQL on my system and keep them there all the time.

---

### Post by NovaAesa on 2011-10-22
What's wrong with keeping them there all the time?

Maybe set up a virtual machine with another install in it?

---

### Post by rojanu on 2011-10-23
well, nothing wrong to keep them all but have them running is not ideal and having an environment set for a project is very good as I can sure that only things needed for that are there, no more - no less.

---

### Post by MadCow108 on 2011-10-23
for packaging one uses pbuilder chroots to keep clean environments:
[https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

you can also use it for general programming work. Its very easy to set up multiple chroots for many different architectures and distributions on a single machine.
Its nice for keeping clean environments, but its obviously not real sandboxing as its very easy to break out of a chroot on linux.

---

### Post by NovaAesa on 2011-10-23
> **rojanu said:**
> well, nothing wrong to keep them all but have them running is not ideal and having an environment set for a project is very good as I can sure that only things needed for that are there, no more - no less.

In that case, programming in a virtual machine would be ideal, that way when you are done programming and close in down, it's all gone away.

---

