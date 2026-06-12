---
title: "Link Text File c++"
date: 2011-11-19
forum: Programming Talk
---

### Post by roadkillguy on 2011-11-19
Is it possible to link a given file into a c++ binary?  I don't want to ship my application with the file, but I'd like to keep it with the binary.  Is that possible?  I was thinking I'd somehow need to turn the file into an object file, but I'm not sure if I'd still be able to use fopen on it.

Thanks

EDIT: It's actually not that big of a file, I just don't want to have to make a char array of binary data manually every time I change it.  (It's an ascii art image kind of thing, and it'd be nice to "compile" it every time I change it.)

---

### Post by nvteighen on 2011-11-19
> **roadkillguy said:**
> Is it possible to link a given file into a c++ binary?  I don't want to ship my application with the file, but I'd like to keep it with the binary.  Is that possible?  I was thinking I'd somehow need to turn the file into an object file, but I'm not sure if I'd still be able to use fopen on it.

Thanks

EDIT: It's actually not that big of a file, I just don't want to have to make a char array of binary data manually every time I change it.  (It's an ascii art image kind of thing, and it'd be nice to "compile" it every time I change it.)

You could write a module that solely consists in this array, compile it separately and have a header that declares that array as "extern". Using a Makefile would prevent you to recompile this when not needed.

Anyway, is there a reason to do this? It is much simpler to have this stored in a regular ASCII file that's accessed by the program... and just edit the ASCII file when needed... why not?

---

### Post by roadkillguy on 2011-11-19
Yeah I guess you're right. I'll just leave it as-is.  Thanks anyway.

---

