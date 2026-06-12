---
title: "Gladex (for Ubuntu 64?)"
date: 2008-07-18
forum: Programming Talk
---

### Post by chris062689 on 2008-07-18
I just whipped up a basic Glade file, but now I want to create a skeleton python code.
I tried using Gladex ([https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex)) but they only have a package for 32 architecture, not 64 bit.
Is there an alternative I can use that has 64-bit packages?

---

### Post by mssever on 2008-07-18
> **chris062689 said:**
> I just whipped up a basic Glade file, but now I want to create a skeleton python code.
I tried using Gladex ([https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex)) but they only have a package for 32 architecture, not 64 bit.
Is there an alternative I can use that has 64-bit packages?
If you're using GtkBuilder, writing the code manually is so trivial that there's not a lot of point to Gladex. I tried Gladex at first, but decided it wasn't worth it. See [this page]("http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html") for an idea of how little code there is to write to get started.

EDIT: <off-topic>The bean counters have determined that this post has given me my 2,000th bean. Now, I just need to figure out what to do with all those beans. :)</off-topic>

---

### Post by bruce89 on 2008-07-18
> **chris062689 said:**
> I just whipped up a basic Glade file, but now I want to create a skeleton python code.
I tried using Gladex ([https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex)) but they only have a package for 32 architecture, not 64 bit.
Is there an alternative I can use that has 64-bit packages?

You should not use code generation. It is evil. Use libglade instead.

> **mssever said:**
> If you're using GtkBuilder, writing the code manually is so trivial that there's not a lot of point to Gladex.

GtkBuilder XML files are not the same as "Glade files".

---

### Post by mssever on 2008-07-18
> **bruce89 said:**
> GtkBuilder XML files are not the same as "Glade files".
True, but it's trivial to convert a Glade file to a GtkBuilder XML file:
```
gtk-builder-convert something.glade something.xml
```

---

### Post by bruce89 on 2008-07-18
> **mssever said:**
> True, but it's trivial to convert a Glade file to a GtkBuilder XML file:
```
gtk-builder-convert something.glade something.xml
```

Indeed, but I prefer writing GtkBuilder files manually.

Glade-3 has support for GtkBuilder in Subversion.

---

