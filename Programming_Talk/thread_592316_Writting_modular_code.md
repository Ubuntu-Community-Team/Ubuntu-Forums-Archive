---
title: "Writting modular code"
date: 2007-10-26
forum: Programming Talk
---

### Post by i0Null on 2007-10-26
Does anyone know how to write a plugin architecture in C, so that an application can dynamically load modules and plugins at runtime? ( such as data input (from databases, or a file) and different interfaces ( like ncurses or gtk)? ))

---

### Post by Wybiral on 2007-10-26
You just need a way to handle the shared object files.

[http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/dl-libraries.html](http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/dl-libraries.html)

---

