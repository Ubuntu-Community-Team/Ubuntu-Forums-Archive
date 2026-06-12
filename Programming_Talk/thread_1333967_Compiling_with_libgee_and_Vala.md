---
title: "Compiling with libgee and Vala"
date: 2009-11-22
forum: Programming Talk
---

### Post by kumoshk on 2009-11-22
I have libgee working and all, but it doesn't link in directly, it seems. If I go to another computer, I have to install libgee to run my binary (that kind of defeats a major purpose of using a compiled language, I think).

Libgee is supposed to be LGPL. I'm guessing this is why it doesn't compile in by default. However, isn't there a way to get the program's path for libgee.so.2 to search its own directory? I mean, I tried putting libgee.so.2 and my program in the same directory, but it doesn't work.

Keep in mind I wouldn't mind making my entire program LGPL (or even GPL) /if/ I could compile this library in. Is there a way?

Anyway, if this is a hopeless venture, does anyone know another way to use associative arrays (maps/dictionaries) in Vala? I need both keys and values to be able to hold *objects* (not just strings). If not, does anyone know how I can convert a variable name into a string? That would give me a way to make associative arrays with string keys, anyhow.

---

### Post by kumoshk on 2009-11-22
One idea I had was to use lua.vapi in such a manner that I could use Lua tables in Vala. However, that might not work, anyway, and lua.vapi doesn't seem to be functioning on my computer (64-bit).

---

