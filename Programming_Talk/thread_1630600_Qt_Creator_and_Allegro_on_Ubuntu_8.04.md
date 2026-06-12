---
title: "Qt Creator and Allegro on Ubuntu 8.04"
date: 2010-11-25
forum: Programming Talk
---

### Post by heatblazer on 2010-11-25
Please help! I am trying to use allegro on qt creator 2.0 on ubuntu 8.04. I`ve installed it but here is what always happens :(
 A detailed explanation will be appriciated. It`s my first step so please be concrete.

---

### Post by spjackson on 2010-11-25
As with most libraries, it isn't enough simply to include the allegro header -  you need to link to the allegro library too.

---

### Post by heatblazer on 2010-11-25
> **spjackson said:**
> As with most libraries, it isn't enough simply to include the allegro header -  you need to link to the allegro library too.

And thats what I need to know how to do...

---

### Post by Tcressy on 2010-11-25
Perhaps what your looking for is something like

gcc myfile.c -lallegro

probably something along those lines...You just need to link the library when you compile it. you might have to do the path to allegro after -l ?

---

### Post by spjackson on 2010-11-25
> **heatblazer said:**
> And thats what I need to know how to do...
 As you are using QtCreator, you need to add a line to your project's .pro file. Something like:
```

LIBS += -L/path/to/lib/directory -lallegro

```but the details depend on where you installed the allegro library.

---

### Post by heatblazer on 2010-11-26
> **spjackson said:**
> As you are using QtCreator, you need to add a line to your project's .pro file. Something like:
```

LIBS += -L/path/to/lib/directory -lallegro

```but the details depend on where you installed the allegro library.

That helped a lot. Now apps are starting. But after the black screen my desktop resolution is set to 640x480...any info?

---

### Post by heatblazer on 2010-11-26
Thank you for assisting. I am moving on now... even loaded a itmap :)

---

### Post by spaceintruder on 2012-01-18
> **spjackson said:**
> As you are using QtCreator, you need to add a line to your project's .pro file. Something like:
```

LIBS += -L/path/to/lib/directory -lallegro

```but the details depend on where you installed the allegro library.

Hello, i have tried Qt Creator with allegro on Ubuntu, and it works, according to your instruction ( manually editing .pro file ) but same approach doesn't work on Windows XP.
I know it's Ubuntu forum, but as those two products are platform independent (Qt and allegro itself) maybe someone here have a hint how to do it on Windows ( Qt Creator and allegro,latest releases ).
First of all, QtCreator doesn't recognize the header allegro.h, even when i add it to the project, and when i apply the above approach with LIB += includes to the pro file, it won't compile with message  No rule to make target `

Somebody, please help me,thanks in advance.

---

### Post by Zugzwang on 2012-01-18
> **spaceintruder said:**
> Hello, i have tried Qt Creator with allegro on Ubuntu, and it works, according to your instruction ( manually editing .pro file ) but same approach doesn't work on Windows XP.
I know it's Ubuntu forum, but as those two products are platform independent (Qt and allegro itself) maybe someone here have a hint how to do it on Windows ( Qt Creator and allegro,latest releases ).
First of all, QtCreator doesn't recognize the header allegro.h, even when i add it to the project, and when i apply the above approach with LIB += includes to the pro file, it won't compile with message  No rule to make target `


You might have better started a new thread for this one, because it is common to do so here. Furthermore, having "Ubuntu 8.04" in the name of your post isn't advantageous.

What compiler are you using under windows?
For specifying the location of your header files, add the line
"INCLUDEPATH += \path\to\include\directory" to your project file and fill in the correct directory.

The stuff you specify in the "LIBS" variable in a QMake project file is only used during linking, and your problem is during compiling.

---

### Post by spaceintruder on 2012-01-18
> **Zugzwang said:**
> You might have better started a new thread for this one, because it is common to do so here. Furthermore, having "Ubuntu 8.04" in the name of your post isn't advantageous.

What compiler are you using under windows?
For specifying the location of your header files, add the line
"INCLUDEPATH += \path\to\include\directory" to your project file and fill in the correct directory.

The stuff you specify in the "LIBS" variable in a QMake project file is only used during linking, and your problem is during compiling.

First of all, apologies for my way of posting, it was motivated because of similar solution on Ubuntu, which works.
I have MinGW g++ compiler, i have tried all ways to add libraries and headers, including writting to pro file, and yes i have included path to include dir as well, but nothing works.
When i start to write code, #include <allegro.h> or #include "allegro.h" both ways were immediately recognized in editor with path setup according to directive 

win32:[COLOR=#800080]INCLUDEPATH[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]C:/MinGW/[COLOR=#808000]include[/COLOR] 

(maybe i was under impression of similar ways of solving this under other IDE's so i copied headers from allegro dir into MinGW folder)

but when i type function allegro_init(); after allegro the editor blinks with ALLEGRO_H, and allegro_init() is not recognized nor compiled as function.
Other code, standard C++ headers all work fine and compiles without problem.
I am now thinking, maybe i have to download prebuilt package for allegro to match correct version of MinGW?

My Allegro library is 4.2.3 while MinGW g++ version used by QtSDK is 4.4.0, but that shouldn't be problem.

Here are other directives i have tried to enter manually because i choosed empty QtCreator project and tried to fill pro file myself, from scratch, but nothing helps.

win32:[COLOR=#800080]CONFIG[/COLOR](release,[COLOR=#c0c0c0] [/COLOR]debug|release):[COLOR=#c0c0c0] [/COLOR][COLOR=#800080]LIBS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]-L$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2/[COLOR=#c0c0c0] [/COLOR]-lalleg win32:[COLOR=#800080]CONFIG[/COLOR](debug,[COLOR=#c0c0c0] [/COLOR]debug|release):[COLOR=#c0c0c0] [/COLOR][COLOR=#800080]LIBS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]-L$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2/[COLOR=#c0c0c0] [/COLOR]-lalld   win32:[COLOR=#800080]INCLUDEPATH[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]C:/MinGW/lib/gcc/mingw32/4.6.2 win32:[COLOR=#800080]INCLUDEPATH[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]C:/MinGW/[COLOR=#808000]include[/COLOR] win32:[COLOR=#800080]HEADERS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]allegro.h[COLOR=#c0c0c0] [/COLOR]winalleg.h win32:[COLOR=#800080]SOURCES[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]primer3.cpp win32:[COLOR=#800080]CONFIG[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]qt  [COLOR=#800080]DEPENDPATH[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2  win32:[COLOR=#800080]CONFIG[/COLOR](release,[COLOR=#c0c0c0] [/COLOR]debug|release):[COLOR=#c0c0c0] [/COLOR][COLOR=#800080]PRE_TARGETDEPS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2/alleg.lib else:win32:[COLOR=#800080]CONFIG[/COLOR](debug,[COLOR=#c0c0c0] [/COLOR]debug|release):[COLOR=#c0c0c0] [/COLOR][COLOR=#800080]PRE_TARGETDEPS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2/alld.lib else:unix:!macx:!symbian:[COLOR=#c0c0c0] [/COLOR][COLOR=#800080]PRE_TARGETDEPS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]$$PWD/../../../../MinGW/lib/gcc/mingw32/4.6.2/liballeg.a  
Also, i have noticed that when i type #include <allegro.h> in the editor the popup appears with possible files that are 'allegro.h" but also /allegro which is subfolder i have copied together wiht include files....nothing helps.

I am too confused now, hopefully not for long.

---

