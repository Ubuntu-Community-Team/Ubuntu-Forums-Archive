---
title: "Lua 5.1 and LuaSocket on Ubuntu 9.04 64bit"
date: 2009-07-07
forum: Programming Talk
---

### Post by HOLOGRAPHICpizza on 2009-07-07
I installed Lua 5.1 and LuaSocket on Ubuntu 9.04 64bit using:
```
sudo aptitude install lua5.1 luasocket
```

But when I attempt to include 'socket.http' in Lua, I get the following error:
```
michael@flash:~$ lua
Lua 5.1.4  Copyright (C) 1994-2008 Lua.org, PUC-Rio
> require 'socket.http'
stdin:1: module 'socket.http' not found:
	no field package.preload['socket.http']
	no file './socket/http.lua'
	no file '/usr/local/share/lua/5.1/socket/http.lua'
	no file '/usr/local/share/lua/5.1/socket/http/init.lua'
	no file '/usr/local/lib/lua/5.1/socket/http.lua'
	no file '/usr/local/lib/lua/5.1/socket/http/init.lua'
	no file '/usr/share/lua/5.1/socket/http.lua'
	no file '/usr/share/lua/5.1/socket/http/init.lua'
	no file './socket/http.so'
	no file '/usr/local/lib/lua/5.1/socket/http.so'
	no file '/usr/lib/lua/5.1/socket/http.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
	no file './socket.so'
	no file '/usr/local/lib/lua/5.1/socket.so'
	no file '/usr/lib/lua/5.1/socket.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
stack traceback:
	[C]: in function 'require'
	stdin:1: in main chunk
	[C]: ?
> 

```

Where does Ubuntu keep the Lua installation at? Any ideas on how to get this to work?

---

### Post by fr4nko on 2009-07-08
I'm not sure but I will not install luasocket but liblua5.1-socket2 instead. May be the problem is that lua socket trigger the installation of the library for lua 5.0.

To have the list of files in  liblua5.1-socket2 you can look [here]("http://packages.debian.org/sid/i386/liblua5.1-socket2/filelist").

Francesco
******

---

### Post by HOLOGRAPHICpizza on 2009-07-08
Awesome, that worked! Thanks! :D

---

