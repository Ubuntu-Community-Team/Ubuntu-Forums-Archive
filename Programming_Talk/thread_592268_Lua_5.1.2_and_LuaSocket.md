---
title: "Lua 5.1.2 and LuaSocket"
date: 2007-10-26
forum: Programming Talk
---

### Post by Samjiman on 2007-10-26
Hi. I have been trying to prototype an idea of mine in Lua, which involves web requests, so I googled for a network socket library and found LuaSocket.

I had previously installed Lua 5.0 from the Ubuntu respositories. Problem is that that installation does not seem to follow the standard Lua distribution directory structure. That is,  I did not find these directtory structures:
[LIST]
[*]/usr/local/lib/lua/5.0
[*]/usr/local/share/lua/5.0
[/LIST]

I uninstalled Lua 5.0, as installed from the respositories, and downloaded Lua 5.1.2 from [http://luabinaries.luaforge.net](http://luabinaries.luaforge.net).

I installed the exectuables to /usr/bin/. So my Lua executable is /usr/bin/lua.

I downloaded the LuaSocket ([http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/home.html](http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/home.html)) source code and have had troubles building it with the included makefile.

When I try building with make, I get this feedback:

```

cd src; make all
make[1]: Entering directory `/home/sam/Desktop/luasocket-2.0.2/src'
gcc  -DLUASOCKET_DEBUG  -pedantic -Wall -O2 -fpic   -c -o luasocket.o luasocket.c
luasocket.c:20:17: error: lua.h: No such file or directory
luasocket.c:21:21: error: lauxlib.h: No such file or directory
luasocket.c:24:24: error: compat-5.1.h: No such file or directory
In file included from luasocket.c:30:
luasocket.h:30: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:31:
auxiliar.h:37: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:38: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:39: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:40: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:41: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:42: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:43: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:44: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:45: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
auxiliar.h:46: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:32:
except.h:33: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:33:
timeout.h:19: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
timeout.h:26: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:34:
buffer.h:39: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buffer.h:41: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buffer.h:42: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buffer.h:43: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
buffer.h:44: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:35:
inet.h:27: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
inet.h:35: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
inet.h:36: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:36:
tcp.h:34: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:37:
udp.h:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from luasocket.c:38:
select.h:15: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:43: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:44: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:45: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:50: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;mod&#8217;
luasocket.c:60: warning: ISO C does not allow extra &#8216;;&#8217; outside of a function
luasocket.c:62: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;func&#8217;
luasocket.c:66: warning: ISO C does not allow extra &#8216;;&#8217; outside of a function
luasocket.c:71: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:80: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:89: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
luasocket.c:113: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
make[1]: *** [luasocket.o] Error 1
make[1]: Leaving directory `/home/sam/Desktop/luasocket-2.0.2/src'
make: *** [all] Error 2

```

I'm inexperienced with makefiles, so I'm not really sure whats happening here. Other than that their appears to be erros in the source files and that certain files cannot be found.

Anyway, can anyone help me find an easy way of getting the LuaSocket library up and running with Lua?

Thanks very much.


[B]EDIT:  I downloaded the source code for Lua 5.1 and copied the source files to the directory looked for in the makefile and managed to run the makefile successfully. It created object code (*.o) files. But I'm not sure what I'm supposed to do with these and I think I'm supposed to be generating shared libraries (*.so).
Any help would be great.

Thanks again. :)[/B]

---

### Post by moma on 2007-10-26
Ubuntu 7.10 comes with Lua 5.1.2 out of the box.

$ [COLOR="SeaGreen"]apt-cache search lua | grep 5.1[/COLOR]
$ [COLOR="SeaGreen"]apt-cache show lua5.1 lua5.1-doc[/COLOR]
----------

EDIT: you are running Ubuntu 7.04. 

Anyway, if you want to install yourself, download these binary packages. 
lua5_1_2_Linux26g4_bin.tar.gz  	     ( Linux x86 Executables )
lua5_1_2_Linux26g4_lib.tar.gz 	 (  Linux x86 Library and Includes )

And put the files to 3 different places. Where?   
Read this page: [http://luabinaries.luaforge.net/installation.html](http://luabinaries.luaforge.net/installation.html)
Put binaries to /usr/bin or /usr/local/bin, 
libraries to /usr/lib or /usr/local/lib,
and include files to /usr/include or /usr/local/include

Run 
$ [COLOR="SeaGreen"]sudo ldconfig [/COLOR]
afterwards.

---

### Post by Samjiman on 2007-10-27
Thanks, I did manage to get LuaSocket to compile the necessary shared libraries. The solution was to just get the Lua 5.1.2 source code and include the files in the directory where the makefile looked for them.

---

