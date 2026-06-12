---
title: "Installing SQLite Wrapper in Lua"
date: 2013-07-05
forum: Programming Talk
---

### Post by stevenc2 on 2013-07-05
I've googled a lot, had a friend who knows more about Ubuntu help me (isn't saying much), but I can't for the life of me get any SQLite wrapper to work with Lua.

I get an error:
```
Lua 5.2.1  Copyright (C) 1994-2012 Lua.org, PUC-Rio
> require "sqlite3"
stdin:1: module 'sqlite3' not found:
        no field package.preload['sqlite3']
        no file '/usr/local/share/lua/5.2/sqlite3.lua'
        no file '/usr/local/share/lua/5.2/sqlite3/init.lua'
        no file '/usr/local/lib/lua/5.2/sqlite3.lua'
        no file '/usr/local/lib/lua/5.2/sqlite3/init.lua'
        no file './sqlite3.lua'
        no file '/usr/share/lua/5.2/sqlite3.lua'
        no file '/usr/share/lua/5.2/sqlite3/init.lua'
        no file './sqlite3.lua'
        no file '/usr/local/lib/lua/5.2/sqlite3.so'
        no file '/usr/lib/i386-linux-gnu/lua/5.2/sqlite3.so'
        no file '/usr/lib/lua/5.2/sqlite3.so'
        no file '/usr/local/lib/lua/5.2/loadall.so'
        no file './sqlite3.so'
stack traceback:
        [C]: in function 'require'
        stdin:1: in main chunk
        [C]: in ?

```

Unless I type 
```
module "sqlite3"
```
first, then I can 'require "sqlite3' just fine.

But then I can't for the life of me figure out how to use it....
```
> print (sqlite3().version)
stdin:1: attempt to call global 'sqlite3' (a table value)
stack traceback:
        stdin:1: in main chunk
        [C]: in ?

```

Any help would be greatly appreciated!  I'm kind of lost here.  Spoiled coming from Lua for Windows when SQLite is preinstalled....

---

### Post by Kujua on 2013-07-05
I am not a Lua expert, but I had used sqlite3 with lua some time back. Hope this helps:

```

module "sqlite3"
require "sqlite3"

```
When you do this, *module* **creates** a new module named 'sqlite3'. So *require* succeeds after that. But it just loads the module created by you in the first step, not the real sqlite3 module you are interested in.
If you don't execute *module*, *require* tries to search for a module named sqlite3 on your system, fails to find it, and throws an error.

Did you install lua-sql-sqlite3 package?
```
sudo apt-get install lua-sql-sqlite3
```

Module name is *luasql.sqlite3*

Example:
```

$ lua
Lua 5.2.1  Copyright (C) 1994-2012 Lua.org, PUC-Rio
> drv = require "luasql.sqlite3"
> print(drv._VERSION)
LuaSQL 2.3.0

```

For details on luasql: [http://www.keplerproject.org/luasql/manual.html](http://www.keplerproject.org/luasql/manual.html)

---

