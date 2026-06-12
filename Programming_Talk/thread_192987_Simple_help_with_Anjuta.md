---
title: "Simple help with Anjuta"
date: 2006-06-09
forum: Programming Talk
---

### Post by digimars on 2006-06-09
I have followed along with setting up SDL in Anjuta from this [site]("http://lazyfooproductions.com/SDL_tutorials/lesson01/linux/anjuta/index.php").

I can build the project, and Execute it from the IDE, and it will run fine.  But when I go to where my project is at /home/me/Projects/SDL_tut/ there is no SDL_tut file in there, but there is a binary file by that name in /home/me/Projects/SDL_tut/src.  But when I try to run that with this:
```

me@Archimedes:~$ cd /home/me/Projects/SDL_tut/src
me@Archimedes:~/Projects/SDL_tut/src$ ls
main.cc  main.o  Makefile  Makefile.am  Makefile.in  sdl_tut
me@Archimedes:~/Projects/SDL_tut/src$ sdl_tut
bash: sdl_tut: command not found
me@Archimedes:~/Projects/SDL_tut/src$ sh sdl_tut
sdl_tut: sdl_tut: cannot execute binary file
me@Archimedes:~/Projects/SDL_tut/src$ bash sdl_tut
sdl_tut: sdl_tut: cannot execute binary file

```

And I tried to do a Build Distribution, all I get is this:
```

Building the distribution package of the Project: SDL_tut ...
make  dist
cd . && autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
rm -rf SDL_tut-0.1
mkdir SDL_tut-0.1
chmod 777 SDL_tut-0.1
here=`cd . && pwd`; \
	top_distdir=`cd SDL_tut-0.1 && pwd`; \
	distdir=`cd SDL_tut-0.1 && pwd`; \
	cd . \
	  && automake-1.4 --include-deps --build-dir=$here --srcdir-name=. --output-dir=$top_distdir --gnu Makefile
configure.in: 78: required file `./ABOUT-NLS' not found
Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS
Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS
automake: Makefile.am: AM_GNU_GETTEXT in `configure.in' but `ALL_LINGUAS' not defined
make: *** [distdir] Error 1
Completed ... unsuccessful
Total time taken: 2 secs

```

How can I run my test program outside of the IDE?  Why can't I build a distribution?

I'm extremely new to Linux programming, but I have dealt with beginner to intermediate Windows programming, so I'm not too noobish.

Any help would be greatyl appreciated.

---

### Post by BugenhagenXIII on 2006-06-09
While in the src directory, type 
```

./sdl_tut

```

---

### Post by digimars on 2006-06-09
[QUOTE=BugenhagenXIII]While in the src directory, type 
```

./sdl_tut

```[/QUOTE]
Thanks, I gave it a shot, but it just went back to the command line.  I recall in Windows that you would have to do something like system("PAUSE") to prevent a console window closing at the end of the program's execution, is that what is happening here?

---

### Post by BornLoser on 2006-08-27
> ...recall in Windows that you would have to do something like system("PAUSE") to prevent a console window closing at the end of the program's execution, is that what is happening here?

I've actually wondered the same thing. Within Linux, I cannot use the system("Pause") command to stop the console window from closing. Everytime this happens I encounter errors. Is there some equivalent within Linux that I can use to do this? Better still, is there some method that works across ** both** operating systems so I don't have to worry about writing it one way, building to see if my program works, then changing the command to something that will work in Windows to send to my professor who uses Windows XP for final review/ grading. 

Any help would be appreciated.

Thanks.

---

