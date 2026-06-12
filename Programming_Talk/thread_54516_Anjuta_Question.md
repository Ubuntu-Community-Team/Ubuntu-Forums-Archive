---
title: "Anjuta Question"
date: 2005-08-04
forum: Programming Talk
---

### Post by grofaz on 2005-08-04
I'm trying to build the SDL_Init example but I'm having difficulty with the library paths. Anjuta can't find the SDL library that defines the SDL_Init function. Can some knowledgeable Anjuta-nik please help me out ?? How do I set the correct library paths ? Appreciate any help! Thanks!

---

### Post by DJ_Max on 2005-08-05
Do you have the correct dev packages?
Example: libsdl1.2-dev

---

### Post by grofaz on 2005-08-05
Yeah I loaded up all the SDL packages, but I don't seem to be able to set the library path correctly. Is it libSDL1.2-dev I need to link to? Thanks!

---

### Post by grofaz on 2005-08-05
Well, as far as I can see libsdl1.2-dev resides in /usr/share/docs but anjuta can't find it when I try a build. I've tried to set the library path accordingly but without success.

Building source directory of the Project: test2 ...
make 
/bin/sh ../libtool --mode=link g++ -Wall 	 -g   -o test2 -L/usr/share/doc/libsdl1.2-dev main.o -lgtkmm-2.0 -lgdkmm-2.0 -latkmm-1.0 -lgtk-x11-2.0 -lpangomm-1.0 -lglibmm-2.0 -lsigc-1.2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   	 -l/usr/share/docs/libsdl1.2-dev 
g++ -Wall -g -o test2 main.o  -L/usr/share/doc/libsdl1.2-dev /usr/lib/libgtkmm-2.0.so /usr/lib/libgdkmm-2.0.so /usr/lib/libatkmm-1.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libpangomm-1.0.so /usr/lib/libglibmm-2.0.so /usr/lib/libsigc-1.2.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangoxft-1.0.so /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -l/usr/share/docs/libsdl1.2-dev
[COLOR=Red]/usr/bin/ld: cannot find -l/usr/share/docs/libsdl1.2-dev[/COLOR]
collect2: ld returned 1 exit status
make: *** [test2] Error 1
Completed ... unsuccessful
Total time taken: 2 secs

Where the heck is the file??

---

### Post by DJ_Max on 2005-08-05
This isn't an Anjuta problem. It's a problem with the example on your comuter. I'm gonna play around and see if I can get the SDL file to include.

---

### Post by LordHunter317 on 2005-08-05
No, the shared library isn't there.  It ought to be in /usr/lib, and all you should have to pass is -lSDL, I believe.

I don't know what led you to believe the library code is in a *documentation* directory.

---

### Post by DJ_Max on 2005-08-05
The file is /usr/include/SDL/SDL.h

What example are you using?

---

### Post by grofaz on 2005-08-05
The example from the dev-help docs. I #included <SDL.h> but it didn't recognize the SDL_Init function so I figured I'd better also set the library path to the SDL library file. I did set the include path correctly apparently since that part seems to work. I've been trying to set the libray path to every SDL library file I can find in /usr/lib and failing there anywhere else I can find that might have the correct file but when I try to build, it isn't found.

---

### Post by grofaz on 2005-08-05
OK...removing all references to sdl library paths this is what I'm getting:

Building source directory of the Project: test2 ...
make 
/bin/sh ../libtool --mode=link g++ -Wall 	 -g   -o test2  main.o -lgtkmm-2.0 -lgdkmm-2.0 -latkmm-1.0 -lgtk-x11-2.0 -lpangomm-1.0 -lglibmm-2.0 -lsigc-1.2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
g++ -Wall -g -o test2 main.o  /usr/lib/libgtkmm-2.0.so /usr/lib/libgdkmm-2.0.so /usr/lib/libatkmm-1.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libpangomm-1.0.so /usr/lib/libglibmm-2.0.so /usr/lib/libsigc-1.2.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangoxft-1.0.so /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so
main.o(.text+0x24): In function `main':
/home/kudu/Projects/test2/src/main.cc:11: undefined reference to `SDL_Init'
main.o(.text+0x2e):/home/kudu/Projects/test2/src/main.cc:14: undefined reference to `SDL_GetError'
main.o(.text+0x67):/home/kudu/Projects/test2/src/main.cc:23: undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
make: *** [test2] Error 1
Completed ... unsuccessful
Total time taken: 2 secs

And this is the program:

#include <SDL.h>
#include <iostream>

int main()
{
	printf("Initializing SDL.\n");
	
	//initialize defaults, video and audio
	if((SDL_Init(SDL_INIT_VIDEO|SDL_INIT_AUDIO)==-1))
	
	{
		printf("Could not initialize SDL: %s.\n", SDL_GetError());
		exit(-1);
	}

	printf("SDL initialized.\n");
	
	printf("Quiting SDL.\n");

	//shutdown all systems
	SDL_Quit();

	printf("Quiting....\n");

	exit(0);
}

HELP!! Thanks...  :)

---

### Post by grofaz on 2005-08-06
[QUOTE=LordHunter317]No, the shared library isn't there.  It ought to be in /usr/lib, and all you should have to pass is -lSDL, I believe.

I don't know what led you to believe the library code is in a *documentation* directory.[/QUOTE]

That's it! The correct library reference is:  -lSDL

Thank you!!

---

