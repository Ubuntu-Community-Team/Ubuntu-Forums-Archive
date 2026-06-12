---
title: "A small gtk question"
date: 2009-03-15
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-03-15
where is the header gtk.h?

(#include <gtk/gtk.h>)

---

### Post by dwhitney67 on 2009-03-15
On Fedora 9, it is here:  /usr/include/gtk-2.0/gtk/gtk.h

---

### Post by jimi_hendrix on 2009-03-15
> **dwhitney67 said:**
> On Fedora 9, it is here:  /usr/include/gtk-2.0/gtk/gtk.h

that worked but since that header is just a bunch of includes with other headers...

i really just want to see the prototype of G_OBJECT() and G_CALLBACK()

---

### Post by jimi_hendrix on 2009-03-15
also what package do i need to dev gtk+ programs?  i have been trying to do #import <gtk/gtk.h>, but it says there is no such file...i also tried with "'s instead of <>'s

---

### Post by dwhitney67 on 2009-03-15
> **jimi_hendrix said:**
> also what package do i need to dev gtk+ programs?  i have been trying to do #import <gtk/gtk.h>, but it says there is no such file...i also tried with "'s instead of <>'s
As indicated earlier, on my system the gtk/gtk.h file is in /usr/include/gtk-2.0.

Thus to compile a program, I would need to specify that path using the -I option.

For example
```

#include <gtk/gtk.h>
...

```
```

gcc -I/usr/include/gtk-2.0 ...

```
If you are using C++, then substitute gcc with g++.

---

### Post by jimi_hendrix on 2009-03-15
ok thanks

---

### Post by dwhitney67 on 2009-03-15
> **jimi_hendrix said:**
> ..
i really just want to see the prototype of G_OBJECT() and G_CALLBACK()

Are these gtk++ extensions?  They do not exist on my system.

---

### Post by Habbit on 2009-03-15
Some IDEs like NetBeans expand macros for you when you hover the mouse pointer over the invocations. They also allow to "go to declaration" and "go to source" of functions, etc.

---

### Post by nvteighen on 2009-03-15
G_OBJECT() and G_CALLBACK() are actually part of GLib's gobject system, not GTK+.

To create GTK+ apps, you better use:
```

gcc -o myapp source.c -Wall `pkg-config --cflags --libs gtk+-2.0`

```

In the case of C++ programs using the gtkmm binding, I don't know how this is done. If you just use the regular GTK+ in C++ (which seems possible, though ridiculous), I guess just changing gcc to g++ in the former command would be enough.

Use **backticks (` `)** not quotes (' ')!

---

### Post by Habbit on 2009-03-15
> **nvteighen said:**
> Use **backticks (` `)** not quotes (' ')!

Lots of backtick griefs could be avoided just by using the more visually obvious $( subshell-command ) notation.

---

### Post by nvteighen on 2009-03-15
> **Habbit said:**
> Lots of backtick griefs could be avoided just by using the more visually obvious $( subshell-command ) notation.

Thanks. Didn't know that one!

---

### Post by jimi_hendrix on 2009-03-15
> **nvteighen said:**
> G_OBJECT() and G_CALLBACK() are actually part of GLib's gobject system, not GTK+.

To create GTK+ apps, you better use:
```

gcc -o myapp source.c -Wall `pkg-config --cflags --libs gtk+-2.0`

```In the case of C++ programs using the gtkmm binding, I don't know how this is done. If you just use the regular GTK+ in C++ (which seems possible, though ridiculous), I guess just changing gcc to g++ in the former command would be enough.

Use **backticks (` `)** not quotes (' ')!

ok, they were in the first tutorial on google...if anyone has any tutorial recommendations they are welcome (for plain C)

---

