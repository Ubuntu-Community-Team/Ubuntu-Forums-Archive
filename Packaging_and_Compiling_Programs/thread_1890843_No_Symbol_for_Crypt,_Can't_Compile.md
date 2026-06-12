---
title: "No Symbol for Crypt, Can't Compile"
date: 2011-12-04
forum: Packaging and Compiling Programs
---

### Post by amishx64 on 2011-12-04
Hello all,

I am trying to compile a project known as LuCI used on OpenWrt routers.

According to [this]("http://luci.subsignal.org/trac/wiki/Documentation/DevelopmentEnvironmentHowTo") page, I install the respective packages. I checked out with ```
svn co http://svn.luci.subsignal.org/luci/trunk
```

When I get to compiling, I run into issues with the crypt symbol.


```
cc -o uhttpd -L./lua-5.1.4/src -Wl,--export-dynamic -lcrypt -ldl uhttpd.o uhttpd-file.o uhttpd-utils.o uhttpd-cgi.o
uhttpd.o: In function `main':
/home/amishx64/Luci/trunk/contrib/uhttpd/uhttpd-src/uhttpd.c:965: [COLOR="Red"]undefined reference to `crypt'[/COLOR]
uhttpd-utils.o: In function `uh_auth_check':
/home/amishx64/Luci/trunk/contrib/uhttpd/uhttpd-src/uhttpd-utils.c:787: [COLOR="Red"]undefined reference to `crypt'[/COLOR]
collect2: ld returned 1 exit status
make[2]: *** [compile] Error 1
make[2]: Leaving directory `/home/amishx64/Luci/trunk/contrib/uhttpd/uhttpd-src'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/home/amishx64/Luci/trunk/contrib/uhttpd'
*** Compilation of contrib/uhttpd failed!
make: *** [gccbuild] Error 1
```

Doing a nm on libcrypt.so.1 says that there is no symbol.
```
nm /lib/i386-linux-gnu/libcrypt.so.1
nm: /lib/i386-linux-gnu/libcrypt.so.1: no symbols
```

I am running Ubuntu 11.10 with a nearly fresh install (this week). I have the libc6 package and it is the latest version.

I don't know what the issue is with the symbol, what it means, and/or how to solve it.

Any help would be appreciated.

EDIT: Is the issue with my post the same as [http://ubuntuforums.org/showthread.php?t=1885626](http://ubuntuforums.org/showthread.php?t=1885626) ?

---

### Post by SevenMachines on 2011-12-04
Yes, same issue, --as-needed change requires libs after objects/source. You'll need to adjust the corresponding Makefiles

---

### Post by SevenMachines on 2011-12-04
The changes below should do it
```
$ cat contrib/uhttpd/uhttpd-src/Makefile |grep -A 1 -n compile:
72:compile: $(OBJ) $(TLSLIB) $(LUALIB)
73-    $(CC) -o uhttpd $(LDFLAGS) $(OBJ) $(LIB)

$ cat modules/admin-full/Makefile | grep -A 1 -n compile:
13:compile: build-clean $(BWC_OBJ)
14-    $(LINK) -o src/$(BWC_BIN) $(BWC_OBJ) $(BWC_LDFLAGS)
```

---

### Post by amishx64 on 2011-12-04
> **SevenMachines said:**
> The changes below should do it
```
$ cat contrib/uhttpd/uhttpd-src/Makefile |grep -A 1 -n compile:
72:compile: $(OBJ) $(TLSLIB) $(LUALIB)
73-    $(CC) -o uhttpd $(LDFLAGS) $(OBJ) $(LIB)

$ cat modules/admin-full/Makefile | grep -A 1 -n compile:
13:compile: build-clean $(BWC_OBJ)
14-    $(LINK) -o src/$(BWC_BIN) $(BWC_OBJ) $(BWC_LDFLAGS)
```

Holy crap! You are the man (or machines hehehehe). I actually fixed the first one by looking at the other post and had since gotten stuck on the admin-full.

I have a problem tho (go figure). If I change the make file it gets overwritten every time I do a new make all. It gets overwritten with some patch that I have to find... As a temporary solution, I make the Makefile read only. How would you fix this issue? Make a second patch on top of the dev's patch or just make it read only like I did or something else?

---

### Post by SevenMachines on 2011-12-04
It pulls down uhttpd-src from svn on make. You need to add a patch to the contrib/uhttpd/patches/ directory and update the corresponding series file.
```
$ cat contrib/uhttpd/patches/002_as_needed.patch 
diff -ruN uhttpd-src/Makefile uhttpd-src.new//Makefile
--- uhttpd-src/Makefile    2011-12-04 16:51:03.191879730 +0000
+++ uhttpd-src.new//Makefile    2011-12-04 16:53:12.107876500 +0000
@@ -70,7 +70,7 @@
     $(CC) $(CFLAGS) -c -o $@ $<
 
 compile: $(OBJ) $(TLSLIB) $(LUALIB)
-    $(CC) -o uhttpd $(LDFLAGS) $(LIB) $(OBJ)
+    $(CC) -o uhttpd $(LDFLAGS) $(OBJ) $(LIB)
 
 clean:
     rm -f *.o *.so uhttpd


``````
$ cat contrib/uhttpd/patches/series              
001-pass-env.patch
002_as_needed.patch
```

---

### Post by amishx64 on 2011-12-04
Again, thank you. You are very kind in helping. :D

If I could bother you with one more thing though. I am more stumped here. I don't understand what is going on.

> make runhttpd

results in:

```
build/hostenv.sh /home/mark/Luci/trunk/host /usr/lib/lua /usr/lib/lua "/home/mark/Luci/trunk/host/bin/uci-defaults --exclude luci-freifunk-*"
/home/mark/Luci/trunk/host/bin/../usr/bin/uci: Entry not found
/home/mark/Luci/trunk/host/bin/../etc/uci-defaults/luci-upnp: line 3: /etc/init.d/miniupnpd: No such file or directory
build/hostenv.sh /home/mark/Luci/trunk/host /usr/lib/lua /usr/lib/lua "lua build/lucid.lua"
lua: error loading module 'nixio' from file '/home/mark/Luci/trunk/host//usr/lib/lua/nixio.so':
	/home/mark/Luci/trunk/host//usr/lib/lua/nixio.so: undefined symbol: MD5_Final
stack traceback:
	[C]: ?
	[C]: in function 'require'
	/home/mark/Luci/trunk/host//usr/lib/lua/luci/sys.lua:31: in main chunk
	[C]: in function 'require'
	build/setup.lua:19: in main chunk
	[C]: in function 'dofile'
	build/lucid.lua:1: in main chunk
	[C]: ?
make: *** [runhttpd] Error 1

```

nixio.so is a binary file and there is no makefile in that directory. I have no idea what it is trying to do.

Hopefully this is the last issue before I can actually get to work.

It [seems like this guy has the same problem in 2009]("https://bbs.archlinux.org/viewtopic.php?id=107338") but didn't post anything else.

---

### Post by SevenMachines on 2011-12-04
It's more linking fun, you'll need to make the change below
```
$ cat libs/nixio/Makefile | grep -A 1 -n compile
92:compile: $(NIXIO_OBJ)
93-    $(LINK) $(SHLIB_FLAGS) -o src/$(NIXIO_SO) $(NIXIO_OBJ) $(NIXIO_LDFLAGS_POST) $(NIXIO_LDFLAGS)

```
The clean and recompile the nixio lib before running make runhttpd again

---

### Post by amishx64 on 2011-12-04
Everything seems to be working!

I wish to thank you very very much for all of your help. It would've taken we a week straight to figure all that out.

Everything shows up nicely here at [http://127.0.0.1:8080/luci](http://127.0.0.1:8080/luci)

:)

---

