---
title: "Eclipse OpenGL undefined reference"
date: 2013-12-27
forum: Programming Talk
---

### Post by brick2 on 2013-12-27
Ok so I have installed  libSDL1.2-dev and did the following in the Eclipse:
   
 C/C++ Build>Settings - Tool Settings>GCC C Compiler - Include paths (-l)>"/usr/include/SDL" 
 C/C++ Build>Settings - Tool Settings>GCC C Linker - Libraries (-l)>"SDL"
 

 After looking around on the net, there were a lot of people saying that it is in essence some sort of a linking error, and that the path to the libs should be included. How this would be done at this point I do not know nor whether this is a solution to the problem at hand. Here is my code and the build output.

```
#include <iostream>
#include "SDL/SDL.h"
#include "SDL/SDL_opengl.h"


using namespace std;

int main(int argc, char *argv[])
{
    SDL_Init( SDL_INIT_EVERYTHING );

    //Set memory usage
    SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_GREEN_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_BLUE_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_ALPHA_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_BUFFER_SIZE, 32 );
    SDL_GL_SetAttribute( SDL_GL_DEPTH_SIZE, 16 );
    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 );

    //Window title
    SDL_WM_SetCaption( "Window", 0 );

    //Window Size
    SDL_SetVideoMode( 600, 400, 32, SDL_OPENGL );

    //Screen color
    glClearColor( 1, 1, 1, 1 ); // RED, GREEN, BLUE , APLHA

    //Portion to be displayed
    glViewport( 0, 0, 600, 400 );

    //2D rendering
    glMatrixMode( GL_PROJECTION );

    //Save it
    glLoadIdentity();

    //Disable depth checking
    glDisable( GL_DEPTH_TEST );

    //5 seconds Delay
    SDL_Delay( 5000 );

    SDL_Quit();
}


```


BUILD OUTPUT:

```
Building target: XO_Game
Invoking: Cross G++ Linker
g++  -o "XO_Game"  ./src/XO_Game.o   -l"SDL"
./src/XO_Game.o: In function `main':
/home/relax/workspace/XO_Game/Debug/../src/XO_Game.cpp:28: undefined reference to `glClearColor'
/home/relax/workspace/XO_Game/Debug/../src/XO_Game.cpp:31: undefined reference to `glViewport'
/home/relax/workspace/XO_Game/Debug/../src/XO_Game.cpp:34: undefined reference to `glMatrixMode'
/home/relax/workspace/XO_Game/Debug/../src/XO_Game.cpp:37: undefined reference to `glLoadIdentity'
/home/relax/workspace/XO_Game/Debug/../src/XO_Game.cpp:40: undefined reference to `glDisable'
collect2: ld returned 1 exit status
make: *** [XO_Game] Error 1
```


ERRORS:

```
   
[SIZE=4][COLOR=#ff0000][FONT=Monospace]undefined reference to `glClearColor'[/FONT][/COLOR]
[/SIZE]
[SIZE=4] [/SIZE][SIZE=4][COLOR=#000000][FONT=Monospace]undefined reference to `glViewport'[/FONT][/COLOR][/SIZE]

[SIZE=4] [/SIZE][SIZE=4][COLOR=#000000][FONT=Monospace]undefined reference to `glMatrixMode'[/FONT][/COLOR][/SIZE]
[SIZE=4] [/SIZE][SIZE=4][COLOR=#000000][FONT=Monospace]undefined reference to `glLoadIdentity'[/FONT][/COLOR][/SIZE]

[SIZE=4] [/SIZE][SIZE=4][COLOR=#000000][FONT=Monospace]undefined reference to `glDisable'[/FONT][/COLOR][/SIZE]


```

Using:

Ubuntu 12.04 LTS
Eclipse Kelper CDT
   

[COLOR=#000000][FONT=Monospace][SIZE=2]
[SIZE=4]This is the matter that I need help with. One more time I am really sorry for my previous post that was a mistake on my part.[/SIZE][/SIZE][/FONT][/COLOR]

---

### Post by steeldriver on 2013-12-27
you just need to add "GL" to the list of libraries, I think (corresponding to -lGL on the g++ command line)

---

### Post by brick2 on 2013-12-27
I've seen that sugested somewhere, can you provide me with an example code for this.

Is there a way to compile this from Eclips without comand line, as I ll probably compile it 1000000000 before the programe is done.

---

### Post by steeldriver on 2013-12-27
right where you added "SDL" before, add "GL" as well - then you can just build (compile and link) by pressing the hammer icon on the main Eclipse toolbar

IDEs like Eclipse are great for big projects, but they seem to complicate things for simple builds - I'm a big fan of command line / Makefiles for this kind of stuff

---

### Post by brick2 on 2013-12-27
Than you very much, this has solved the problem. I like the terminal too, but the program will get bigger and I ll need to compile test it a lot of times before it is done, ctrl F11 is justt faster than typing g++ over and over again, that is why I asked, about the IDE and how can you do it in it. Again thank you for your time. 
It is amazing how people are so quick to respond and provide others with solutions on this forum. Best forum ever.

---

### Post by steeldriver on 2013-12-27
You're welcome - good luck with the project!

---

