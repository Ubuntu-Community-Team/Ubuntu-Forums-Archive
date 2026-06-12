---
title: "[SOLVED] Adding Library to Ajunta Project"
date: 2008-12-20
forum: Programming Talk
---

### Post by rich1939 on 2008-12-20
I'm building an application using Ajunta and I need to include the PostgreSQL library, pq, as well as it's corresponding header file. I've scoured the docs for Ajunta but I don't see how to add library and include files in the build process.

I suppose that one could muck with the Makefiles, etc., but I'd rather not have to do that if Ajunta offers a simpler way to do so.

So I'm looking for help in adding foreign libs and include files to Ajunta.

---

### Post by rich1939 on 2008-12-22
Not a Bump!

I finally gave up on Ajunta and switched to Code::Blocks, where I was able to easily use its features for adding header files and libraries. The interface to the debugger works fine too, and I can also use GLADE, adding a Pre-Build task to convert the Glade file to a GtkBuilder file (XML). Everything is now automatic.

I guess I just didn't have the mindset to deal with Ajunta, even though the Gnome development team presumably uses it with aplomb.

---

