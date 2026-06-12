---
title: "C++ embedded Lua: requiring shared object files"
date: 2009-10-02
forum: Programming Talk
---

### Post by kumoshk on 2009-10-02
I successfully followed the instructions at the following link:
[http://cc.byexamples.com/20080607/how-to-embed-lua-51-in-c/](http://cc.byexamples.com/20080607/how-to-embed-lua-51-in-c/)

However, I couldn't get the Lua portion to load if I tried requiring a shared object file, or a .so file (even if it was in the same directory).

Does anyone know a way to fix this so the path still looks for shared object files? It doesn't have any problems requiring .lua files (even if they're not in the same directory, as long as they're in a path that Lua looks for).

Note: This shouldn't matter, but if it does, I'm using LuaJIT (requiring .so files when it's not embedded works just fine).

---

### Post by matburton on 2009-10-04
I've embedded Lua before but never tried requiring in a shared lib

Since Lua is written in ANSI C I believe it doesn't know anything about dynamic loading by default

I would check that you have compiled the Lua library with dynamic loading support

(if you can compile your stuff successfully without -ldl then that's probably a good indication that something's missing)

Hope that helps

---

### Post by gmclachl on 2009-10-04
Make sure you have installed all the dev packages.

---

