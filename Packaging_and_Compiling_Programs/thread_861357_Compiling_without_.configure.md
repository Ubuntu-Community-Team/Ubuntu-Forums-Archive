---
title: "Compiling without ./configure"
date: 2008-07-16
forum: Packaging and Compiling Programs
---

### Post by andrewkk on 2008-07-16
The [lzlib]("http://luaforge.net/projects/lzlib/") source has a Makefile, but no configuration script and no installation instructions.

This is all the configuration there is in the Makefile:
```
# change these to reflect your Lua installation
LUA= $(HOME)/local/lua
LUAINC= $(LUA)/include
LUALIB= $(LUA)/lib
LUABIN= $(LUA)/bin
```

It doesn't look at all like how things are usually organized in Ubuntu. I have no $(HOME)/local folder, and the [packaged Lua installation]("http://packages.ubuntu.com/hardy/liblua5.1-0-dev") is certainly not going to be anywhere in $(HOME) anyway.

This is what happens when I run make:
```
$ make
cc -I/home/ak/local/lua/include -I../zlib-1.2.3  -g -Werror -Wall -pedantic  -O0    -c -o lzlib.o lzlib.c
lzlib.c:28:17: error: lua.h: No such file or directory
lzlib.c:29:21: error: lauxlib.h: No such file or directory
lzlib.c:90: error: expected ‘)’ before ‘*’ token <--- Lots of these
lzlib.c:844: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
make: *** [lzlib.o] Error 1

```

Any pointers on what to set those Makefile variables to?

---

### Post by Bachstelze on 2008-07-16
```
LUA=/usr
```

Shouldo to the trick. Make sure you have the -dev package for your version of liblua as well.

---

### Post by andrewkk on 2008-07-16
Thanks, that sounds like it should work. But it doesn't appear to be quite right though:
```
$ make
cc -I/usr/include -I../zlib-1.2.3  -g -Werror -Wall -pedantic  -O0    -c -o lzlib.o lzlib.c
lzlib.c:28:17: error: lua.h: No such file or directory
lzlib.c:29:21: error: lauxlib.h: No such file or directory
lzlib.c:90: error: expected ‘)’ before ‘*’ token
lzlib.c:844: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
make: *** [lzlib.o] Error 1

```

lua.h and lauxlib.h are in /usr/include/lua5.1/. When I set
```
LUA= /usr
LUAINC= $(LUA)/include/lua5.1
```
it gets a little farther:
> $ make
cc -I/usr/include/lua5.1 -I../zlib-1.2.3  -g -Werror -Wall -pedantic  -O0    -c -o lzlib.o lzlib.c
cc -o zlib.so -shared lzlib.o -L../zlib-1.2.3 -lz -L/usr/lib -L/usr/bin -llua51
/usr/bin/ld: cannot find -llua51
collect2: ld returned 1 exit status
make: *** [zlib.so] Error 1


That one really stumps me. I don't think [-llua51]("http://packages.ubuntu.com/search?searchon=contents&keywords=llua51&mode=filename&suite=hardy&arch=i386") is a real file.

---

### Post by andrewkk on 2008-07-16
> **andrewkk said:**
> That one really stumps me. I don't think [-llua51]("http://packages.ubuntu.com/search?searchon=contents&keywords=llua51&mode=filename&suite=hardy&arch=i386") is a real file.

Aha! It isn't. There's a typo farther down in the Makefile. This line
```
LIBS= -L$(ZLIB) -lz -L$(LUALIB) -L$(LUABIN) -llua51
```
needs to be this:
```
LIBS= -L$(ZLIB) -lz -L$(LUALIB) -L$(LUABIN) -Llua51
```

Thanks for the help. I'll go bug the lzlib people.

I'm learning a lot today :)

---

### Post by WW on 2008-07-18
That doesn't make sense.  The argument should probably be **-llua5.1**.

If you look [here](http://packages.ubuntu.com/hardy/i386/liblua5.1-0/filelist), you'll see that the Ubuntu package [liblua5.1-0](http://packages.ubuntu.com/hardy/liblua5.1-0) provides the shared library files /usr/lib/liblua5.1.so.0 and /usr/lib/liblua5.1.so.0.0.0.  The compiler option **-llua5.1** tells the compiler (linker, actually) that you are using this library; it will convert **lua5.1** to the appropriate name (i.e. add the "lib" prefix, and identify the appropriate .so file in /usr/lib to use).

The **-L** option tells the linker *where* to look for the library files. The option **-Llua51** means "look in a directory called lua51".  Since there is no such directory, this option has no effect.

---

### Post by WW on 2008-07-18
By the way, according to [this list of files](http://packages.ubuntu.com/hardy/i386/liblua5.1-0-dev/filelist), the package [liblua5.1-0-dev](http://packages.ubuntu.com/hardy/liblua5.1-0-dev) provides the file  /usr/lib/pkgconfig/lua5.1.pc.  This is a configuration file for the **pkg-config** command.  This means there is a simple way to get the correct arguments for compiling and linking a program that uses the library, using the pkg-config command.  For example, for compiling:
```

pkg-config --cflags lua5.1

```
will print the compiler options, and
```

pkg-config --libs lua5.1

```
will print the linker options.  It would be nice if the lzlib Makefile used pkg-config (but I guess they can't count on all operating systems providing the pkg-config command).

---

