---
title: "gcc finds library but ld-linux.so does not?"
date: 2010-06-16
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-06-16
I'm coding an awesome game in C. But the graphics are not so awesome, so I decided to rewrite the graphics code.

I reorganized the entire directory tree to make things look clean, moved some stuff to separate libraries
and moved most of the game-specific source files (33) to src/game/temp, so they don't get compiled. 

Then I rewrote all remaining files in src/game and src/game/graphics. The new directory tree looks like this:
```

.
&#9500;&#9472;&#9472; [COLOR="Orange"]SConstruct[/COLOR]
&#9500;&#9472;&#9472; [COLOR="DarkGreen"]libshared.so[/COLOR]
&#9500;&#9472;&#9472; [COLOR="DarkGreen"]libminiparser.so[/COLOR]
&#9500;&#9472;&#9472; [COLOR="DarkGreen"]Stacked Fortress[/COLOR]
&#9492;&#9472;&#9472; src
    &#9500;&#9472;&#9472; game
    &#9474;   &#9500;&#9472;&#9472; [COLOR="Orange"]SConscript[/COLOR]
    &#9474;   &#9500;&#9472;&#9472; (source files)
    &#9474;   &#9474;  ........... 
    &#9474;   &#9492;&#9472;&#9472; ......
    &#9500;&#9472;&#9472; miniparser
    &#9474;   &#9500;&#9472;&#9472; [COLOR="Orange"]SConscript[/COLOR]
    &#9474;   &#9500;&#9472;&#9472; (source files)
    &#9474;   &#9474;  ........... 
    &#9474;   &#9492;&#9472;&#9472; ......
    &#9492;&#9472;&#9472; shared
        &#9500;&#9472;&#9472; [COLOR="Orange"]SConscript[/COLOR]
        &#9500;&#9472;&#9472; (source files)
        &#9474;  ........... 
        &#9492;&#9472;&#9472; ......

```

There are no errors when compiling it:
```

rho@a91-156-166-231:~/Source/stacked/Stacked Fortress 0.8$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
gcc -o .obj/game/gameloop.o -c -std=gnu99 -Wall -g -D_GNU_SOURCE=1 -D_REENTRANT -I.obj/game -I.obj/game/graphics -I.obj/shared -I.obj/miniparser -I/usr/include/SDL -I/usr/include/FTGL -I/usr/include/freetype2 .obj/game/gameloop.c
gcc -o .obj/game/graphics/text.o -c -std=gnu99 -Wall -g -D_GNU_SOURCE=1 -D_REENTRANT -I.obj/game -I.obj/game/graphics -I.obj/shared -I.obj/miniparser -I/usr/include/SDL -I/usr/include/FTGL -I/usr/include/freetype2 .obj/game/graphics/text.c
.obj/game/graphics/text.c: In function 'draw_text':
.obj/game/graphics/text.c:38: warning: implicit declaration of function 'glWindowPos2i'
gcc -o .obj/game/main.o -c -std=gnu99 -Wall -g -D_GNU_SOURCE=1 -D_REENTRANT -I.obj/game -I.obj/game/graphics -I.obj/shared -I.obj/miniparser -I/usr/include/SDL -I/usr/include/FTGL -I/usr/include/freetype2 .obj/game/main.c
gcc -o .obj/game/mod.o -c -std=gnu99 -Wall -g -D_GNU_SOURCE=1 -D_REENTRANT -I.obj/game -I.obj/game/graphics -I.obj/shared -I.obj/miniparser -I/usr/include/SDL -I/usr/include/FTGL -I/usr/include/freetype2 .obj/game/mod.c
gcc -o .obj/miniparser/miniparser.os -c -std=gnu99 -Wall -g -fPIC -I.obj/shared .obj/miniparser/miniparser.c
gcc -o .obj/shared/getmem.os -c -std=gnu99 -Wall -g -fPIC .obj/shared/getmem.c
gcc -o .obj/shared/linkedlist.os -c -std=gnu99 -Wall -g -fPIC .obj/shared/linkedlist.c
gcc -o .obj/shared/str_utils.os -c -std=gnu99 -Wall -g -fPIC .obj/shared/str_utils.c
gcc -o libshared.so -shared .obj/shared/getmem.os .obj/shared/linkedlist.os .obj/shared/str_utils.os
gcc -o libminiparser.so -shared .obj/miniparser/miniparser.os -L. -lshared
gcc -o "Stacked Fortress" .obj/game/gameloop.o .obj/game/main.o .obj/game/mod.o .obj/game/graphics/text.o -L.obj/game -L. -lGLU -lGL -lSDL_image -lminiparser -lshared -lSDL -lftgl
scons: done building targets.

```

But when I try to run it:
```

arho@a91-156-166-231:~/Source/stacked/Stacked Fortress 0.8$ ./Stacked\ Fortress 
./Stacked Fortress: error while loading shared libraries: libminiparser.so: cannot open shared object file: No such file or directory
arho@a91-156-166-231:~/Source/stacked/Stacked Fortress 0.8$ 

```

My temporary solution:
```

export LD_LIBRARY_PATH=.

```
Then the program works as it should.

The problem must be in SConscripts. Here's src/game/SConscript:
```

Import( Split("ccflags") )
src_dirs = Split( ". graphics" )
include_dirs = Split( ". ../shared ../miniparser" )

env = Environment()
env.Append( CCFLAGS = ccflags )
env.Append( CPPPATH = src_dirs + include_dirs )
env.Append( LIBPATH = ["../.."] )
env.Append( LIBS = Split("GLU GL SDL_image miniparser shared") );
env.ParseConfig( "pkg-config --cflags --libs sdl ftgl" )

src = []
for dir in src_dirs:
	src += Glob( dir + "/*.c" )

obj = env.Object( source = src );
env.Program( target = "../../Stacked Fortress", source = obj );

```

And src/miniparser/SConscript:
```

Import( Split("ccflags") )

env = Environment()
env.Append( LIBPATH = ["../.."] )
env.Append( LIBS = Split("shared") )
env.Append( CPPPATH = ["../shared"] )
env.Append( CCFLAGS = ccflags )

src = Glob( "*.c" )
obj = env.SharedObject( source = src )
env.SharedLibrary( target = "../../miniparser", source = obj )

```

Why ld-linux.so doesn't find my libraries?

And BTW, why does it warn about glWindowPos2i? I have it in my system:
```

arho@a91-156-166-231:~/Source/stacked/Stacked Fortress 0.8$ glewinfo|grep 'glWindowPos2i: '
  glWindowPos2i:                                               OK
arho@a91-156-166-231:~/Source/stacked/Stacked Fortress 0.8$

```

---

### Post by Some Penguin on 2010-06-16
Because the libraries aren't installed in a directory specified by /etc/ld.so.conf.

---

### Post by crazyfuturamanoob on 2010-06-16
I changed the shared libraries to static ones. Problem solved :)

---

### Post by dwhitney67 on 2010-06-16
> **crazyfuturamanoob said:**
> I changed the shared libraries to static ones. Problem solved :)

Ah, you found a work-around without fully understanding why you had a problem in the first place.  Good for you.

---

