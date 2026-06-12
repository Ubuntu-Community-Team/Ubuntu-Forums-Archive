---
title: "Importing libraries for mingw-gcc"
date: 2011-12-16
forum: Packaging and Compiling Programs
---

### Post by Finalfantasykid on 2011-12-16
I am trying to compile some c code(generated from vala code) which uses several SDL and OpenGL libraries.  When I try to compile the c code, I get numerous errors.  Here are a few:

```
/usr/include/SDL/SDL_stdinc.h:605: error: expected ‘)’ before ‘cd’
In file included from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:30,
                 from /home/david/code/tlc/src/graphics/Image.c:7:
/usr/include/SDL/SDL_stdinc.h:74:20: error: iconv.h: No such file or directory
In file included from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:30,
                 from /home/david/code/tlc/src/graphics/Image.c:7:
/usr/include/SDL/SDL_stdinc.h:605: error: expected ‘)’ before ‘cd’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/item/Armour.c:11:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/item/RestoreItem.c:11:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/item/Shard.c:11:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/item/Weapon.c:11:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/menu/Conditional.c:9:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/menu/ConversationTree.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
/home/david/code/tlc/src/menu/ConversationTree.c: In function ‘string_strip’:
/home/david/code/tlc/src/menu/ConversationTree.c:718: warning: passing argument 1 of ‘g_strchug’ discards qualifiers from pointer target type
/usr/include/glib-2.0/glib/gstrfuncs.h:154: note: expected ‘gchar *’ but argument is of type ‘const gchar *’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/menu/Menu.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/menu/MenuGrid.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/menu/MenuMethods.c:9:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/aosObject/Debris.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/aosObject/Door.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/aosObject/House.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/aosObject/NPC.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/aosObject/Shop.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
In file included from /usr/include/glib-2.0/gio/gio.h:47,
                 from /home/david/code/tlc/src/script/Script.c:10:
/usr/include/glib-2.0/gio/gcredentials.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_credentials_get_unix_user’
/usr/include/glib-2.0/gio/gcredentials.h:70: error: expected declaration specifiers or ‘...’ before ‘uid_t’
```

I have never used mingw-gcc before, so I am not sure about how to fix these errors.  Here is the compile command that I am attempting.

```
/usr/bin/i586-mingw32msvc-gcc -o ... ... -pthread -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/SDL -I/usr/include/gee-1.0  -pthread -lSDL -lGL -lgio-2.0 -lgmodule-2.0 -lgee -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0 '-mwindows' '-lSDL_gfx' '-lSDL_image' '-lglut' '-lSDL_ttf'

```

---

### Post by dodle on 2011-12-22
You need to tell the compiler and linker where the headers and libraries are. They are located in the "include" and "lib" sub-directories of "i586-mingw32msvc" (might be something else if you are using 64 bit). I think you can do it by setting the environment variables for [color=blue]CFLAGS[/color] and [color=blue]LDFLAGS[/color]:

> CFLAGS="-I/usr/i586-mingw32msvc/include"
LDFLAGS="-L/usr/i586-mingw32msvc/lib"

Or if you don't want to set the variables permanently you can try this:

> ./configure CFLAGS="-I/usr/i586-mingw32msvc/include" LDFLAGS="-I/usr/i586-mingw32msvc/lib" --prefix=/usr/i586-mingw32msvc --host=i586-mingw32msvc --build=i686-linux

or if that doesn't work try this:

source: [http://hintsforums.macworld.com/archive/index.php/t-45956.html](http://hintsforums.macworld.com/archive/index.php/t-45956.html)
> env CFLAGS="-I/usr/i586-mingw23msvc/include" LDFLAGS="-I/usr/i586-mingw32msvc/lib" ./configure --prefix=/usr/i586-mingw32msvc --host=i586-mingw32msvc --build=i686-linux

---

