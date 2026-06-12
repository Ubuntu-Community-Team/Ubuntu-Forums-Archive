---
title: "Linux programming question"
date: 2010-02-23
forum: Programming Talk
---

### Post by Joe Ker1086 on 2010-02-23
Ok, so this might be a really dumb question....but lets say i want to be involved with building live cds and recompiling kernels. even building some packages....what would be the programming language i would be looking for??

---

### Post by Linux000 on 2010-02-23
Most kernel level stuff is in C I believe, graphical stuff is in python.

---

### Post by Zugzwang on 2010-02-24
You neither need programming knowledge for building live cds, nor for packaging programs, nor for recompiling kernels (as long as you don't write new drivers or something similar). 

Having this said, a little bit of scripting knowledge, though, might be useful for the packaging task. Also, when packaging stuff written in C/C++, you might encounter compilation errors in the first place which you need to track the reason. For this task, of course, a little bit of knowledge of these languages is also nice. However, using your favourite search engines on the error messages will help you here.

---

