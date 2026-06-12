---
title: "Embedding LUA to C++ - Missing headers while compiling?"
date: 2010-08-16
forum: Programming Talk
---

### Post by ZequeZ on 2010-08-16
Well, I was wondering how to embed a scripting language into C++ so I did a search and I find out [this tutorial]("http://www.debian-administration.org/articles/264"), I installed the required libraries and anything that said LUA and DEV in Synaptics... But, I can't manage to compile it...

Here is the code from the tutorial:

```

#include <stdio.h>

#include "lua.h"
#include "lualib.h"
#include "lauxlib.h"  /* the Lua interpreter */

lua_State* L; 

int main ( int argc, char *argv[] ) {
   /* initialize Lua */
   L = lua_open();
   /* load various Lua libraries */
   lua_baselibopen(L); 
   luaopen_table(L);
   luaopen_io(L);
   luaopen_string(L);
   luaopen_math(L);

   /* cleanup Lua */
   lua_close(L);
   return 0;
}

```

First of all: Why it uses #include "***" instead of #include <***>? It want me to copy the headers from the system libraries to my program path? :S. Anyway if I change it to <***> it doesn't find anything neither:

```

zequez@zequez-desktop:$ gcc main.cpp
main.cpp:3:17: error: lua.h: No such file or directory
main.cpp:4:20: error: lualib.h: No such file or directory
main.cpp:5:21: error: lauxlib.h: No such file or directory
main.cpp:8: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:12: error: &#8216;L&#8217; was not declared in this scope
main.cpp:12: error: &#8216;lua_open&#8217; was not declared in this scope
main.cpp:15: error: &#8216;lua_baselibopen&#8217; was not declared in this scope
main.cpp:16: error: &#8216;luaopen_table&#8217; was not declared in this scope
main.cpp:17: error: &#8216;luaopen_io&#8217; was not declared in this scope
main.cpp:18: error: &#8216;luaopen_string&#8217; was not declared in this scope
main.cpp:19: error: &#8216;luaopen_math&#8217; was not declared in this scope
main.cpp:22: error: &#8216;lua_close&#8217; was not declared in this scope
zequez@zequez-desktop:$ 

```Which are the links for LUA? And what means the return of lua-config?

---

### Post by dwhitney67 on 2010-08-16
You tell me... do you have the LUA header files on your system???????????????

If you don't, get them.  If you do, then where are they?  Find out.  Let us know... then we can help you with your **g++** statement.

C -->  use gcc

C++ --> use g++


Note:  C and C++ are NOT the same.  C is a very basic language.

---

### Post by ZequeZ on 2010-08-16
> **dwhitney67 said:**
> You tell me... do you have the LUA header files on your system???????????????

If you don't, get them.  If you do, then where are they?  Find out.  Let us know... then we can help you with your **g++** statement.

C -->  use gcc

C++ --> use g++


Note:  C and C++ are NOT the same.  C is a very basic language.

Wait... gcc doesn't compile C++? Damn, that explain a lot of things *facepalm*

---

### Post by kknd on 2010-08-16
Hi,

First, it's Lua, not LUA (it's not an acronym, it's the portuguese for moon).

Here goes a simple example of how to use Lua with C++:

[PHP]
extern "C" {
    #include <lua.h>
    #include <lauxlib.h>
    #include <lualib.h>
}

int main(int argc, char** argv)
{
    lua_State* L = luaL_newstate();
    
    luaL_dostring(L, "a = 10 + 5");
    lua_getglobal(L, "a");
    int i = lua_tointeger(L, -1);
    printf("%d\n", i);
    
    lua_close(L);
    
    return 0;
}
[/PHP]

You can compile it with 'g++ test.cpp -o output -llua'.
If you still get those errors, then you don't have the headers.

---

### Post by soltanis on 2010-08-17
> **ZequeZ said:**
> Wait... gcc doesn't compile C++? Damn, that explain a lot of things *facepalm*

It actually just invokes the C++ compiler if you try to feed it C++ code.

---

### Post by ZequeZ on 2010-08-23
Thanks ^^.
But still having trouble to compile successful  =(.
I installed everything that has lua and dev in the name and then I used lua-config --libs to see which libraries I had to use to compile and then I used lua-config --include to see the path where Lua is located, buuut it still don't compile =(.

Here is what I have:

```
extern "C" {
    #include <lua50/lua.h>
    #include <lua50/lauxlib.h>
    #include <lua50/lualib.h>
}

int main(int argc, char** argv)
{
    lua_State* L = luaL_newstate();
    
    luaL_dostring(L, "a = 10 + 5");
    lua_getglobal(L, "a");
    int i = lua_tointeger(L, -1);
    printf("%d\n", i);
    
    lua_close(L);
    
    return 0;
}  
```


```

zequez@zequez:~/Lua$ lua-config --libs
-L/usr/include -llualib50 -llua50
zequez@zequez:~/Lua$ lua-config --include
-I/usr/include/lua50
zequez@zequez:~/Lua$ g++ main.cpp -llua50 -llualib50
main.cpp: In function ‘int main(int, char**)’:
main.cpp:9: error: ‘luaL_newstate’ was not declared in this scope
main.cpp:11: error: ‘luaL_dostring’ was not declared in this scope
main.cpp:13: error: ‘lua_tointeger’ was not declared in this scope

```

Any clue?

Sorry for my English =P

---

### Post by kknd on 2010-08-23
Lua 5.0 doesn't have the functions 'luaL_newstate' and etc. This functions were added in version 5.1 (the current version, released in 2006).

The official site is: [http://www.lua.org](http://www.lua.org)

---

