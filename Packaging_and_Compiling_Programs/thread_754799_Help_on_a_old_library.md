---
title: "Help on a old library"
date: 2008-04-14
forum: Packaging and Compiling Programs
---

### Post by hmgp on 2008-04-14
Hello there. I'm helping the Salasaga project, I already made a Ubuntu How to install from source tutorial, but now the project would like to have a Ubuntu Package. I never, ever made a package and I know I must read the PackagingGuide but a problem we see right now his about a library. More precisely the Ming library (libming). The one in the hardy is the same as the one from Gutsy and from Feisty and from Edgy so as you might already understood, it's too old. So the new Salasaga build uses at least version 0.4.0 Beta 5. 

So, how do I create a package to Ubuntu that needs a library that the repositories don't provide, or provide but it's too old?

Thank you.

---

### Post by Zugzwang on 2008-04-14
As long as you're making a binary release, you could statically link the library to your executable, then installing the library is not a requirement. You'd have to include the library in the respective source package, though.

---

### Post by hmgp on 2008-04-14
Thank you very much. I will do as suggested.

---

