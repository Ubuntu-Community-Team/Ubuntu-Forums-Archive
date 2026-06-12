---
title: "Required: C++ Reference (Up to Date)"
date: 2006-11-22
forum: Programming Talk
---

### Post by charlie. on 2006-11-22
Has anyone noticed that the libstdc++ references that GNU.org hosts have not been updated since v.3? (And they don't go down to the class level either.)

I'm looking for a good, up-to-date, reference on all those header files, classes, methods, inheritance hierarchies, enums, constants, namespaces and other guff in the standard C++ library.

I envision something like Microsoft's MSDN or the output that Doxygen generates for many millions of projects. Essentially, I want to know what classes are in which headers, what methods they have and what parameters those methods take.

Any ideas?

---

### Post by hod139 on 2006-11-22
This site is up to date: [http://www.cppreference.com/](http://www.cppreference.com/)

---

### Post by amo-ej1 on 2006-11-24
I use the [http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html) version all the time, ... you want the doxygen documentation matching you installed libstdc++ you might want to take a look at these:

```

e@lap:~$ apt-cache search libstdc++ | grep doc
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.0-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)

```

These result in /usr/share/doc/libstdc++6-4.0-doc/libstdc++/html_user/index.html where you will find an 'alike' page.

---

