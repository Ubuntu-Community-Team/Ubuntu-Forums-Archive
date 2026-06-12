---
title: "How do you publish a MonoDevelop Program?"
date: 2011-06-15
forum: Packaging and Compiling Programs
---

### Post by Nifrpe on 2011-06-15
I mean as a .deb file or a package or something.  I developed C# programs on Windows for a while, but how do you do it on Ubuntu?

---

### Post by ztefn on 2011-07-10
When you have your solution opened up in MonoDevelop you can choose Project -> Create Package and then select the "Tarball" option. This will generate a distro agnostic "Makefile" based package, which can be installed with the commands "./configure", "make" and "make install".

If you want a reusable packaging setup, you can add a "Packaging project" to your solution, which works the same way as above. This way, when you want to build the package, the only thing you have to do is right click your packaging project and choose "Build".

Going a step further, "[checkinstall]("http://www.google.com/search?hl=en&q=checkinstall+create+deb+package")" is an easy way to convert the tarball into a deb package.

---

