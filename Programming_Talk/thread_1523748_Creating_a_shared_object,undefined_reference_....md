---
title: "Creating a shared object,undefined reference ..."
date: 2010-07-04
forum: Programming Talk
---

### Post by matmatmat on 2010-07-04
Hi, I'm trying to create a simple helper library for SDL, so far I have created a class for the screen:
```

//screen.h
#ifndef SCREEN_H
#define SCREEN_H

#include "SDL/SDL.h"

class Screen {
    private:
        SDL_Surface *screen;
    public:
        int width, height, bpp;
        Screen(int width, int height, int bpp);
        void blit(int x, int y, SDL_Surface *source);
        int flip();
};

#endif

//screen.cpp
#include "screen.h"

Screen::Screen(int _width, int _height, int _bpp){
    width = _width;
    height = _height;
    bpp = _bpp;
    screen = SDL_SetVideoMode( width, height, bpp, SDL_SWSURFACE );
}

void Screen::blit(int x, int y, SDL_Surface *source){
}

int Screen::flip(){
     return SDL_Flip(screen);
}

```

I've created a simple Makefile:
```

CXX=g++
FILES=screen.cpp
ONAME=sdl_framework.o
SONAME=libsdlframework
TESTNAME=test
main: $(SONAME) ${TESTNAME}.o
	$(CXX) -o $(TESTNAME)  $(TESTNAME).o -L. -lSDL -lSDL_image

$(SONAME): $(FILES)
	$(CXX) -fPIC -c $(FILES) -o $(ONAME)
	$(CXX) -shared  -Wl,-soname,$(SONAME).so -o $(SONAME).so $(ONAME)

clean:
	$rm *.o *.so

```
It all compiles fine until the test program:
```

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "screen.h"
#include <string>

const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;

SDL_Surface *image = NULL;

SDL_Event event;

Screen init()
{
   SDL_Init( SDL_INIT_EVERYTHING );
    Screen screen(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP);
    SDL_WM_SetCaption( "Test", NULL );

    return screen;
}

void clean_up()
{
    SDL_Quit();
}

int main( int argc, char* args[] )
{
    bool quit = false;

    Screen screen = init();

    if( screen.flip() == -1 )
    {
        return 1;
    }

    while( quit == false )
    {
        while( SDL_PollEvent( &event ) )
        {
            if( event.type == SDL_QUIT )
            {
                quit = true;
            }
        }
    }

    clean_up();

    return 0;
}

``` 

When I run make ld returns 1 exit status and undefined references to Screen::Screen(int, int, int) and Screen::flip()
Is this because the shared object hasn't been compiled properly?

---

### Post by crazyfuturamanoob on 2010-07-04
```

main: $(SONAME) ${TESTNAME}.o
	$(CXX) -o $(TESTNAME)  $(TESTNAME).o -L. -lSDL -lSDL_image

```

You forgot -lsdlframework.

---

### Post by matmatmat on 2010-07-04
> **crazyfuturamanoob said:**
> ```

main: $(SONAME) ${TESTNAME}.o
	$(CXX) -o $(TESTNAME)  $(TESTNAME).o -L. -lSDL -lSDL_image

```

You forgot -lsdlframework.

Thanks for the quick reply!
When I add this it compiles fine, but when run:
```

./test: error while loading shared libraries: libsdlframework.so: cannot open shared object file: No such file or directory

```

BTW: I tried -l libsdlframework before, why didn't this work?

---

### Post by crazyfuturamanoob on 2010-07-04
Your linker does not find the library because it doesn't search it from right directory.
Try:
```

LD_LIBRARY_PATH=. ./test

```
And read: [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)
A better(?) solution would be to make your program load it's libraries by itself: [http://tldp.org/HOWTO/Program-Library-HOWTO/dl-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/dl-libraries.html)

---

### Post by dwhitney67 on 2010-07-04
When you build your app, you are not linking with the library that you created.

There are several things I would recommend:
1.  Clean up the C++ code (ie. bring it up to a higher standard);

2.  Update the Makefile;

3.  Avoid naming an application as 'test'; a utility named 'test' already exists in /usr/bin.


As for the Makefile, try something like:
```

SONAME   = libsdlframework.so

LIBSRCS  = screen.cpp
LIBOBJS  = $(LIBSRCS:.cpp=.o)

TESTAPP  = sdl_test

CXXFLAGS = -Wall -pedantic `pkg-config --cflags sdl`
LDFLAGS  = -L./ -lsdlframework `pkg-config --libs sdl` -lSDL_image


$(TESTAPP): $(SONAME)
        $(CXX) $(CXXFLAGS) $@.c -o $@ $(LDFLAGS)


$(SONAME): $(LIBOBJS)
        $(CXX) $^ -shared -Wl,-soname,$@ -o $@


.cpp.o:
        $(CXX) $(CXXFLAGS) -fPIC -c $<


clean:
        $(RM) $(TESTAPP) $(LIBOBJS) $(SONAME)

```
Above you will notice that I made some changes, namely to the name of the test application, and also to the name of the object file that is produced from the library source code.

I also broke apart the step that is necessary for building the object file(s) needed by the library.

I do not recommend that you join the building of the test application with the library, but test purposes I suppose it is ok.  Instead I recommend that you create separate Makefiles.

P.S.  After you build your test application, you will need to run it similar to the following:
```

LD_LIBRARY_FLAGS=./ sdl_test

```

---

### Post by crazyfuturamanoob on 2010-07-05
> **dwhitney67 said:**
> 
P.S.  After you build your test application, you will need to run it similar to the following:
```

LD_LIBRARY_FLAGS=./ sdl_test

```

Is *LD_LIBRARY_FLAGS* same as *LD_LIBRARY_PATH*? (I searched with google, dogpile, yippy/clusty and yahoo but they didn't find any documentation about it.)

---

### Post by dwhitney67 on 2010-07-05
> **crazyfuturamanoob said:**
> Is *LD_LIBRARY_FLAGS* same as *LD_LIBRARY_PATH*? (I searched with google, dogpile, yippy/clusty and yahoo but they didn't find any documentation about it.)

That was a typo; LD_LIBRARY_PATH is the correct variable name.

---

