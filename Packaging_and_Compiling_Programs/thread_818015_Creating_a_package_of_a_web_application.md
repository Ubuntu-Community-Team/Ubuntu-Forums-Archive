---
title: "Creating a package of a web application"
date: 2008-06-04
forum: Packaging and Compiling Programs
---

### Post by v8YKxgHe on 2008-06-04
Hey,

I'm wondering if anyone can point me in the right direction for creating a .deb package of a web-application. Also, is it really worth doing for a web-app?

Regards,

---

### Post by v8YKxgHe on 2008-06-10
Anyone? =)

---

### Post by dmitrijledkov on 2008-06-10
> **AlexC_ said:**
> Anyone? =)

Well I'm not an expert. But if it's Ruby on Rails you should let ruby install it. If it is php forum then there are special ways of installing php "web-apps". So usually if it doesn't need to be compiled then there is no need for .deb.

Cause .deb has 2 functions. Create a source .deb which conforms to your distribution and will for sure get build. Or binary .deb which for sure has been compiled for your system and you can easily install it on your system using apt or other package management tool.

---

