---
title: "dependencies not satisfiable:"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by griever2000 on 2008-06-29
i have no internet connection.................and I manually download packages from ubuntu......




:KShey, can you help me??
i had a problem about installing packages in my computer...
Two packages are not installed because they need each other in order to do the installation

it looks like this::

**dependencies not satisfiable:sun java6-bin**--->>>the name of the package is sun java6-jre

the other package prompted like this:

**dependencies not satisfiable:sun java6-jre**--->>>the name of the package is sun java6-bin


they treted ech other as a dependency......

how can i solve this????
just reply, or email me at [email]altercatedalexandrine@gmail.com[/email]

thank you&#9786;&#9787;&#9786;&#9787;

---

### Post by shae on 2008-06-29
Place both files into a folder.  Open terminal

```
cd /path/to/folder
sudo dpkg -i *.deb
```

---

