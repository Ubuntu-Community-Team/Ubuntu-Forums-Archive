---
title: "Forward Declaration of C++ Classes"
date: 2007-01-24
forum: Programming Talk
---

### Post by MattKemp on 2007-01-24
Can someone point me in the right direction of forward-declaring a class in C++? I've tried tons of options and I'm not having much joy getting them to work.
i'm trying to do is put a class in its own .cpp file and then call it from a different .cpp file. I thought it was something like this, but it gives me nasty linker errors:

**main.cpp**
```
#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif

#include "sdgame.h"
#include <SDL.h>
#include <string>

using namespace std;

int main ( int argc, char** argv )
{
    SDGame* foo;
    foo = new SDGame("moo");
    // initialize SDL video
    if ( SDL_Init( SDL_INIT_VIDEO ) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }

    // make sure SDL cleans up before exit
    atexit(SDL_Quit);

    // create a new window
    SDL_Surface* screen = SDL_SetVideoMode(640, 480, 16,
                                           SDL_HWSURFACE|SDL_DOUBLEBUF);
    if ( !screen )
    {
        printf("Unable to set 640x480 video: %s\n", SDL_GetError());
        return 1;
    }
```

**sdgame.h:**
```
#ifndef SD_GAME
    #define SD_Game 1

    #include <string>
    #include <SDL.h>


    class SDGame
    {
        std::string _name;
        bool _isRunning;
        static int _numGames;

        public:
            SDGame(std::string);
            std::string getName();
            int getNumGames();

            virtual void mainLoop();
            virtual void keyDown(SDL_Event);
            virtual void keyUp(SDL_Event);

            virtual ~SDGame();
    };
#endif

```

**sdgame.cpp:**

```
#include "sdgame.h"
#include <SDL.h>
#include <string>

using namespace std;

SDGame::SDGame(string name) { _name = name; _numGames++; }
string SDGame::getName() { return _name; }
int SDGame::getNumGames() { return _numGames; }

```

however, when I do this, I get this:

```
Compiling: main.cpp
Linking executable: bin/Release/sdl
obj/Release/sdgame.o: In function `SDGame::getNumGames()':
sdgame.cpp:(.text+0x2): undefined reference to `SDGame::_numGames'
obj/Release/sdgame.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0x54): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0x76): undefined reference to `SDGame::_numGames'
obj/Release/sdgame.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0xe4): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0x106): undefined reference to `SDGame::_numGames'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 1 seconds)
0 errors, 0 warnings

```

Which makes it look like it doesn't like what's being done in sdgame.cpp - however, I haven't got a clue what's going on really. Any ideas?

---

### Post by Wybiral on 2007-01-24
Case sensitive...

```

#ifndef SD_GAME
#define SD_Game 1

```

IE, GAME != Game

Also... Compiling it with "g++ sdgame.cpp main.cpp" should do the trick.

---

### Post by MattKemp on 2007-01-24
```
$ g++ sdgame.cpp main.cpp -o moo `sdl-config --cflags`
/tmp/ccQkyiRW.o: In function `SDGame::getNumGames()':
sdgame.cpp:(.text+0x4): undefined reference to `SDGame::_numGames'
/tmp/ccQkyiRW.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0x3a): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0x67): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0x6f): undefined reference to `SDGame::_numGames'
/tmp/ccQkyiRW.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0xa6): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0xd3): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0xdb): undefined reference to `SDGame::_numGames'
/tmp/cc8V9Nce.o: In function `main':
main.cpp:(.text+0xb0): undefined reference to `SDL_Init'
main.cpp:(.text+0xdd): undefined reference to `SDL_GetError'
main.cpp:(.text+0x100): undefined reference to `SDL_Quit'
main.cpp:(.text+0x129): undefined reference to `SDL_SetVideoMode'
main.cpp:(.text+0x137): undefined reference to `SDL_GetError'
main.cpp:(.text+0x167): undefined reference to `SDL_RWFromFile'
main.cpp:(.text+0x177): undefined reference to `SDL_LoadBMP_RW'
main.cpp:(.text+0x185): undefined reference to `SDL_GetError'
main.cpp:(.text+0x215): undefined reference to `SDL_PollEvent'
main.cpp:(.text+0x244): undefined reference to `SDL_MapRGB'
main.cpp:(.text+0x25b): undefined reference to `SDL_FillRect'
main.cpp:(.text+0x27c): undefined reference to `SDL_UpperBlit'
main.cpp:(.text+0x287): undefined reference to `SDL_Flip'
main.cpp:(.text+0x2a1): undefined reference to `SDL_FreeSurface'
collect2: ld returned 1 exit status

```

---

### Post by lnostdal on 2007-01-24
Those are linker errors. You both are compiling and linking in your supplied example but you have only included compiler-options while you need both compiler- and linker-options. I'm guessing something like:

```
g++ sdgame.cpp main.cpp -o moo `sdl-config --cflags --ldflags`
```

edit:
and try to always include -Wall -g too:

```
g++ -g -Wall sdgame.cpp main.cpp -o moo `sdl-config --cflags --ldflags`
```

edit: err .. this post is probably wrong or something ... ignore as needed; i'm tired

---

### Post by MattKemp on 2007-01-24
This gives me the same errors I get form my IDE:
```
$ g++ sdgame.cpp main.cpp -o moo `sdl-config --cflags --libs`
/tmp/ccaIxzX5.o: In function `SDGame::getNumGames()':
sdgame.cpp:(.text+0x4): undefined reference to `SDGame::_numGames'
/tmp/ccaIxzX5.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0x3a): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0x67): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0x6f): undefined reference to `SDGame::_numGames'
/tmp/ccaIxzX5.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0xa6): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0xd3): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0xdb): undefined reference to `SDGame::_numGames'
collect2: ld returned 1 exit status
matt@rustbucket:~/scriptage/sdl$ 

```

So my guess is that it's syntax rather than a compiler error.

I can just put it in the same file, but I wanted to keep it in a separate one so it's easy to bring in as and when I need it.

---

### Post by DrGroove on 2007-01-26
You need to initialize the static member _numGames outside the class. Add the following line to **sdgame.cpp** :

```

int SDGame::_numGames = 0;

```

---

### Post by jblebrun on 2007-01-27
> **MattKemp said:**
> This gives me the same errors I get form my IDE:
```
$ g++ sdgame.cpp main.cpp -o moo `sdl-config --cflags --libs`
/tmp/ccaIxzX5.o: In function `SDGame::getNumGames()':
sdgame.cpp:(.text+0x4): undefined reference to `SDGame::_numGames'
/tmp/ccaIxzX5.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0x3a): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0x67): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0x6f): undefined reference to `SDGame::_numGames'
/tmp/ccaIxzX5.o: In function `SDGame::SDGame(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
sdgame.cpp:(.text+0xa6): undefined reference to `vtable for SDGame'
sdgame.cpp:(.text+0xd3): undefined reference to `SDGame::_numGames'
sdgame.cpp:(.text+0xdb): undefined reference to `SDGame::_numGames'
collect2: ld returned 1 exit status
matt@rustbucket:~/scriptage/sdl$ 

```

So my guess is that it's syntax rather than a compiler error. 

I can just put it in the same file, but I wanted to keep it in a separate one so it's easy to bring in as and when I need it.

Dr. Groove's got your answer above. 

But for the record, an *undefined reference* is always a linker error, not a syntax error.
The compiler can never know if a reference is undefined.

---

