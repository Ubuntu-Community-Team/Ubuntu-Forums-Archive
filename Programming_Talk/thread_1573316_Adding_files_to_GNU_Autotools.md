---
title: "Adding files to GNU Autotools?"
date: 2010-09-12
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-12
How do I add new files to an Autotool system?

Is there any _**simple**_ guide for doing this?

---

### Post by kamicc on 2010-09-12
is this good enought  [http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/](http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/)    ? :)

---

### Post by fallenshadow on 2010-09-12
I will try it but that tutorial is from 2006 so I hope its not outdated or anything. :D

---

### Post by kamicc on 2010-09-12
Mmmm...
Whole book -> [http://www.freesoftwaremagazine.com/books/autotools_a_guide_to_autoconf_automake_libtool](http://www.freesoftwaremagazine.com/books/autotools_a_guide_to_autoconf_automake_libtool)   :)

And also one more tutorial with plenty of links ->  [http://www.openismus.com/documents/linux/automake/automake](http://www.openismus.com/documents/linux/automake/automake)

---

### Post by pbrane on 2010-09-12
you should add your new source files to **src/Makefile.am**. then run **autogen.sh** again.

---

### Post by fallenshadow on 2010-09-12
```

*** No rule to make target `appname.o', needed by `appname'.  Stop.

```

What the hell does this mean?  :confused:

---

### Post by pbrane on 2010-09-12
you may need to replace **appname** with the name of your program. Probably in configure.in.

---

### Post by fallenshadow on 2010-09-13
I got it fixed now! :)

It now compiles!

Doesn't seem to compile into a working binary though. :D

---

### Post by fallenshadow on 2010-09-14
Seems to work now!

---

