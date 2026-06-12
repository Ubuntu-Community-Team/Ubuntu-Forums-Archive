---
title: "can you load and use shared libraries in Lua?"
date: 2009-09-30
forum: Programming Talk
---

### Post by manualqr on 2009-09-30
I'm using Lua as an embedded scripting language. I can't find any material on this online, but;

Is there a portable way of loading shared libraries and using their functions, variables, etc. from Lua?

e.g;
Programmer 'X' wants to interface with my software. He's got to use Lua for this, but he wants to use library 'foo' (written in C) that provides some special functionality.

If not, my alternative is to write a wrapper around dlopen etc. and its Windows equivalent. Which would be painful.

---

### Post by falconindy on 2009-09-30
[This](http://lua-users.org/lists/lua-l/2005-11/msg00295.html) might be of interest to you. Someone else might know more about Lua in the "outside world", but my experience with it is limited to coding addons for WoW (where you're heavily sandboxed).

---

### Post by manualqr on 2009-09-30
Thanks! That led me to these gems;

[http://lua-users.org/wiki/BindingCodeToLua](http://lua-users.org/wiki/BindingCodeToLua)
[http://lua-users.org/wiki/BuildingModules](http://lua-users.org/wiki/BuildingModules)

I've seen the first link before, but for some reason, the idea that people would have to wrap their C functions to get them to play nicely with Lua never occurred to me =p.

So the solution is to;
1. wrap the C functions you need over Lua API
2. re-compile your shared library
3. use loadlib() in Lua to access your functions ([http://apache.dataloss.nl/~peter/www.lua.org/pil/8.2.html](http://apache.dataloss.nl/~peter/www.lua.org/pil/8.2.html))

---

