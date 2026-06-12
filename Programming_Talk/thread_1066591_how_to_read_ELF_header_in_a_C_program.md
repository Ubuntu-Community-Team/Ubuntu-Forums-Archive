---
title: "how to read ELF header in a C program?"
date: 2009-02-11
forum: Programming Talk
---

### Post by xardox69@gmail.com on 2009-02-11
how can i read ELF header from an object file in a  c program?

---

### Post by xardox69@gmail.com on 2009-02-11
and which libraries to use?

---

### Post by SeanHodges on 2009-02-12
Well 2 ways I can think of, either you could shell out to a program like elfls (available in the [elfkickers]("apt://elfkickers") package), and parse the output...

Or, you could use the libelf library ([libelf-dev]("apt://libelf-dev") package), which I believe is the library you need. Theres a guide here: [http://people.freebsd.org/~jkoshy/download/libelf/article.html](http://people.freebsd.org/~jkoshy/download/libelf/article.html)

---

### Post by ch0d3 on 2009-02-12
elfsh is pretty neat: [http://elfsh.asgardlabs.org/](http://elfsh.asgardlabs.org/)

---

