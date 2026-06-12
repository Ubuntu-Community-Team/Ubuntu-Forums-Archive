---
title: "error: ‘lua_State’ was not declared in this scope"
date: 2011-08-27
forum: Programming Talk
---

### Post by ahso4271 on 2011-08-27
Hi
lstate.h where did it go in the lua 5.1.4 from ubuntu 10.04?
Thanks

---

### Post by Zugzwang on 2011-08-28
Looks like you've got some legacy code.

Apparently, "lstate.h" is not needed. When searching for an example that uses "lua_State", there's the following page: [http://gamedevgeek.com/tutorials/calling-c-functions-from-lua/](http://gamedevgeek.com/tutorials/calling-c-functions-from-lua/) - Here, only three lua headers are included. Try to use those: "lua.h", "lualib.h" and "lauxlib.h" - If you are programming in C++, make sure to include them as being 'extern "C"'.

---

