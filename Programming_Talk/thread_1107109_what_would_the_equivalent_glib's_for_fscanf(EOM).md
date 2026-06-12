---
title: "what would the equivalent glib's for fscanf?(EOM)"
date: 2009-03-26
forum: Programming Talk
---

### Post by mhexyl on 2009-03-26
looking for your help:)

---

### Post by dwhitney67 on 2009-03-26
How about:

-- fread()
-- scanf() if reading from stdin


What are you fishing for with your query?

---

### Post by mhexyl on 2009-03-26
> **dwhitney67 said:**
> How about:

-- fread()
-- scanf() if reading from stdin


What are you fishing for with your query?

fread needs a file descriptor, fscanf also. But GOutputStream instead of file descriptor in glib, i failed to find a API using GOutputStream is similar to fscanf.

---

### Post by dwhitney67 on 2009-03-26
> **mhexyl said:**
> fread needs a file descriptor, fscanf also. But GOutputStream instead of file descriptor in glib, i failed to find a API using GOutputStream is similar to fscanf.

Sorry about that; I misread the 'glib' in the title to be glibc (gnu C library).

I have never looked into glib (Gnome Library), but with a little research via Google, I found documentation for the [Lexical Scanner]("http://library.gnome.org/devel/glib/stable/glib-Lexical-Scanner.html#g-scanner-input-file").  Perhaps this can help you.

---

