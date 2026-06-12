---
title: "Eclipse /bin/sh: 1: Syntax error: &quot;(&quot; unexpected"
date: 2013-12-27
forum: Programming Talk
---

### Post by brick2 on 2013-12-27
I do not really even understand my problem completely. The idea was to make a window using c++ with Eclipse, the code will be posted bellow. Every time I search for the solution I always manage to find something similar to my problem but never quite it.

 
Using:

Eclipse Kelper CDT


 Things done thus far:

 

 apt-get install libSDL1.2-dev
 apt-get update
 apt-get upgrade

 

 Project>Properties 
     C/C++ Build>Settings - Tool Settings>GCC C Compiler - Include paths (-l)>"/usr/include/SDL" 
     C/C++ Build>Settings - Tool Settings>GCC C Linker - Libraries (-l)>"SDL"

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



   

[SIZE=3][SIZE=2]Build output:[/SIZE]
[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
[/SIZE]
[SIZE=3] [/SIZE]```
[SIZE=3][COLOR=#000000][FONT=Monospace]make all [/FONT][/COLOR] 
[/SIZE]
[SIZE=3] [/SIZE][SIZE=3][COLOR=#000000][FONT=Monospace]Building target: XO_Game[/FONT][/COLOR][/SIZE]
[SIZE=3] [/SIZE][SIZE=3][COLOR=#000000][FONT=Monospace]/bin/sh: 1: Syntax error: "(" unexpected[/FONT][/COLOR][/SIZE]
[SIZE=3] [/SIZE][SIZE=3][COLOR=#000000][FONT=Monospace]Invoking: Cross G++ Linker[/FONT][/COLOR][/SIZE]
[SIZE=3] [/SIZE][SIZE=3][COLOR=#000000][FONT=Monospace]make: *** [XO_Game] Error 2[/FONT][/COLOR][/SIZE]
[SIZE=3] [/SIZE][SIZE=3][COLOR=#000000][FONT=Monospace]g++  -o "XO_Game"  ./src/XO_Game.o   -l(-l)>"SDL"[/FONT][/COLOR][/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
[/SIZE]

```[SIZE=3] [/SIZE][SIZE=3][FONT=Monospace]Error:[/FONT][/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
[/SIZE]
[SIZE=3] [/SIZE]```
[SIZE=3][COLOR=#000000][FONT=Monospace]/bin/sh: 1: Syntax error: "(" unexpected[/FONT][/COLOR][/SIZE]


```



   Could anyone shed some light on this matter and help me out, I am really stuck here

[SIZE=3] [/SIZE]

---

### Post by Bachstelze on 2013-12-27
Looks like a bug in Eclipse... As a workaround, try

```
sudo dpkg-reconfigure dash
```

in a terminal, and choose "No".

---

### Post by brick2 on 2013-12-27
Ah I m so sorry I wrote a question but than I figured it out, I just repaced the libs to be added. Failed to see this for like 4h. Now I need to ask something compeatly diffrent but copy pasted this. I am so sorry for this.

---

### Post by brick2 on 2013-12-27
I l lmake another post. Please diregard this one.

---

### Post by steeldriver on 2013-12-27
> **brick2 said:**
> 
 Project>Properties 
     C/C++ Build>Settings - Tool Settings>GCC C Compiler - Include paths (-l)>"/usr/include/SDL" 
     C/C++ Build>Settings - Tool Settings>GCC C Linker - Libraries [COLOR=#ff0000]**(-l)>"SDL"**[/COLOR]


what do you mean by this exactly? did you literally enter [COLOR=#ff0000]**(-l)>"SDL"**[/COLOR] into the 'Libraries' box? that would explain why the gcc command line is showing as

```
g++  -o "XO_Game"  ./src/XO_Game.o   -l[COLOR=#ff0000]**(-l)>"SDL"**[/COLOR]
```

You should just enter the word SDL into the box like this:

[ATTACH=CONFIG]248963[/ATTACH]

Some other libraries will be required as well I think - but that should fix your current error

---

### Post by brick2 on 2013-12-27
OMG yes I jsut copy pasted it [COLOR=#ff0000]**(-l)>"SDL"**[/COLOR] . I mean how stupid can I get. Again I am realy sorry.

---

