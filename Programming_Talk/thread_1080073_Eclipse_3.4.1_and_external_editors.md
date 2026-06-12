---
title: "Eclipse 3.4.1 and external editors"
date: 2009-02-25
forum: Programming Talk
---

### Post by SwedishWings on 2009-02-25
Hi folks,

I have a simple Eclipse C project with an external makefile that works just fine (Eclipse 3.4.1).

However, If I use an external editor (like Glade 3.4.5 in this case), to edit the included glade file, save the file and choose "Build All" in Eclipse, Eclipse don't run make at all. The only way to make "Buld All" work, is to change a file (any file actually) in the Eclipse editor. 

It seems that Eclipse checks if it has any dirty editor buffers, and don't try to build if they are all clean.

Is this a bug, or something i missed?

Thanks,
Mike

---

