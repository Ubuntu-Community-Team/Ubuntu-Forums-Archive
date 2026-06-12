---
title: "Segmentation Fault (SDL Parachute Deployed)??"
date: 2006-03-19
forum: Programming Talk
---

### Post by pranith on 2006-03-19
hi ppl,
      I installed sdl successfully but when I run my program this error is coming
[COLOR="Red"]Fatal signal: Segmentation Fault (SDL Parachute Deployed)[/COLOR]
This is a bug  in sdl 1.2.8 as per the searches... on google and this forum
one person said he switched back to 1.2.7 version
how should we switch back to 1.2.7??
sdl-config --version tells the version number...
thanks in anticipation
pranith

---

### Post by hod139 on 2006-03-19
I never had any problems with SDL and Breezy.  If there is a bug, I wouldn't suggest downgrading to version 1.2.7, I would suggest upgrading to version 1.2.9.  You will have to go to libSDL.org and download the source code and build it all your self though.  Or upgrade to Dapper.

Are you sure that your code isn't causing a seg fault?  You can easily disable the SDL parachute which should make debugging easier:
```

SDL_Init(SDL_FLAGS | SDL_INIT_NOPARACHUTE) 

``` where SDL_FLAGS are whatever flags you are currently using.


All in all, I would try disabling the parachute, and seeing what happens.

---

### Post by wmcbrine on 2006-03-19
Post the code that's giving you the error, and perhaps we can figure out your problem. I definitely wouldn't assume that it's an SDL bug.

I got this when I was trying to call SDL_DisplayFormat() on a couple of surfaces before I'd called SDL_SetVideoMode(), so the display format was undefined. Took me a while to figure out. That's just one example of how it might come up.

---

### Post by pranith on 2006-03-19
#include <iostream>
#include <vector>
#include <SDL.h>
#include <SDL_opengl.h>
#include <math.h>
#include <GL/glut.h>
#define radius 2
#define ORIGINX 0
#define ORIGINY 0
#define ORIGINZ 0

#include "point.h"
#include "sphere.h"
#include "greatcircle.h"
#include "greatarc.h"
#include "polygon.h"
#include "smallcircle.h"
#include "band.h"
#include "pointset.h"


int xrotation=0,yrotation=0;
bool horiz=false,vertical=false;
int main(int argc, char *argv[]);
void render(void);
void init(void);
int main(int argc, char *argv[])
{
    SDL_Init( SDL_INIT_VIDEO ); // Initialise the SDL Video bit

    SDL_WM_SetCaption( "SDL + OpenGL", NULL );

    const SDL_VideoInfo *pSDLVideoInfo = SDL_GetVideoInfo();

    if( !pSDLVideoInfo )
    {
        printf("SDL_GetVideoInfo() failed. SDL Error: %s\n", SDL_GetError());
        SDL_Quit();
        return 1;
    }

    int nFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER | SDL_HWPALETTE;

    if( pSDLVideoInfo->hw_available ) // Hardware surfaces enabled?
        nFlags |= SDL_HWSURFACE;
    else
        nFlags |= SDL_SWSURFACE;

    if( pSDLVideoInfo->blit_hw ) // Hardware supported blitting?
        nFlags |= SDL_HWACCEL;

    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 ); // Enable OpenGL Doublebuffering

    // Create our rendering surface
    SDL_Surface *pSDLSurface = SDL_SetVideoMode( 400, 400, 32, nFlags );

    if( !pSDLSurface )
    {
        printf( "Call to SDL_SetVideoMode() failed! - SDL_Error: %s\n", SDL_GetError() );
        SDL_Quit();
        return 1;
    }

    // Init OpenGL...
    init();

    bool bDone = false;
    SDL_Event Event;

    while( !bDone )
    {
//        printf( "%d\n", bDone );
        while(SDL_PollEvent( &Event ))
        {

        switch( Event.type )
        {
            case SDL_QUIT:
                bDone = true;
                break;
            case SDL_KEYDOWN:
                {
			switch( Event.key.keysym.sym ){
			case SDLK_ESCAPE:
				SDL_Quit();
				exit(0);
				break;
			case SDLK_UP:
				yrotation=(yrotation+5)%360;
				vertical=true;
				break;
			case SDLK_DOWN:
				yrotation=(yrotation-5)%360;
				vertical=true;
				break;
			case SDLK_RIGHT:
				xrotation=(xrotation+5)%360;
				horiz=true;
				break;
			case SDLK_LEFT:
				xrotation=(xrotation-5)%360;
				horiz=true;
				break;
		//	case SDLK_RETURN:
		//		SDL_WM_ToggleFullScreen(pSDLSurface);
		//		break;
			default:
				break;
			}
                }
            case SDL_KEYUP:
                {
			switch( Event.key.keysym.sym ){
			case SDLK_ESCAPE:
				SDL_Quit();
				exit(0);
				break;
			case SDLK_UP:
                                yrotation=(yrotation+5)%360;
                                vertical=true;
                                break;
                        case SDLK_DOWN:
                                yrotation=(yrotation-5)%360;
                                vertical=true;
                                break;
                        case SDLK_RIGHT:
                                xrotation=(xrotation+5)%360;
                                horiz=true;
                                break;
                        case SDLK_LEFT:
                                xrotation=(xrotation-5)%360;
                                horiz=true;
                                break;

		//	case SDLK_RETURN:
		//		SDL_WM_ToggleFullScreen(pSDLSurface);
		//		break;
			default:
				break;
			}

                }
            case SDL_MOUSEBUTTONDOWN:
                {
                    switch( Event.button.button)
		    {
			    case SDL_BUTTON_LEFT:
			//	    up=1;
				    break;
		    }
                }


            default:
		 break;
        }
        }

        render();
//        SDL_Delay(20);
    }

    SDL_Quit();

    return 0;
}

//-----------------------------------------------------------------------------
// Name: init()
// Desc: Init OpenGL context for rendering.
//-----------------------------------------------------------------------------
void init( void )
{
    glClearColor( 0.0f, 0.0f, 0.0f, 0.0f );
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluPerspective( 50.0f,4/3, 0.1f, 1000.0f);
    glMatrixMode( GL_MODELVIEW );
    glEnable(GL_DEPTH_TEST);
    glDepthFunc(GL_LEQUAL);
}
//-----------------------------------------------------------------------------
// Name: render()
// Desc: Called when the SDL window is ready to render
//-----------------------------------------------------------------------------
void render( void )
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glLoadIdentity();
//-------------------------Ur drawing here-------------------------------------
    float location[] = { 0.0, 1000.0, -100.0 ,0.0};
//    float direction[] = { 0, 0, 10 };
    float color[] = { 1, 1, 1, 0 };
     glEnable( GL_LIGHTING );
    glEnable( GL_LIGHT0 );
    glLightfv( GL_LIGHT0, GL_POSITION, location );
    glLightfv( GL_LIGHT0, GL_AMBIENT, color );
    glLightfv( GL_LIGHT0, GL_SPECULAR, color );
    glLightfv( GL_LIGHT0, GL_DIFFUSE, color );
    glTranslatef(0,0,-10);

    /*glRotatef(xrotation,1,0,0);
    glRotatef(yrotation,0,1,0);

    glPushMatrix( );
    float mat[4];

    mat[0] = 0.0215;
    mat[1] = 0.1745;
    mat[2] = 0.0215;
    mat[3] = 1.0;
    glMaterialfv(GL_FRONT, GL_AMBIENT, mat);
    mat[0] = 0.07568;
    mat[1] = 0.61424;
    mat[2] = 0.07568;
    glMaterialfv(GL_FRONT, GL_DIFFUSE, mat);
    mat[0] = 0.633 ;
    mat[1] = 0.727811;
    mat[2] = 0.633 ;
    glMaterialfv(GL_FRONT, GL_SPECULAR, mat);
    glMaterialf(GL_FRONT, GL_SHININESS, 0.6 * 128.0);

    sphere s;
    s.draw();
    glPopMatrix();

    glMaterialfv(GL_FRONT, GL_AMBIENT, mat);*/

/*    glPushMatrix();
    glColor3f(1,0,0);
    point p(2,0,0);
    greatcircle g(2,0,0);
    band b(p,0.1);
    b.draw();
//    glRotatef(0,1,0,0);
//    drawcircle(2.0,0,0,0);
    glPopMatrix();*/

/*    glPushMatrix();
    glColor3f(1,0,0);
    point p1(2,0,0),p2(1.5,0,0);
    smallcircle sc(p1,p2);
    sc.draw();
    glPopMatrix();

    glPushMatrix();
    point p5(2,0,0),p6(0,2,0);
    greatcircle gc(p5,p6);
    gc.draw();
    glPopMatrix();

    glPushMatrix();
    polygon pol1;
    pol1.addpoint(p1);
    pol1.addpoint(p5);
    pol1.addpoint(p6);
    pol1.draw();
    glPopMatrix();

    point p3(2,0,0),p4(0,2,0);
    cout<< "Distance: " << p3.distance(p4) << endl;
    horiz=false;
    vertical=false;*/
    pointset ps;
    point p1(4,0,0);
    point p2(2,1,0);
    point p3(6,0,1);
    point p4(8,0,1);
    point p5(7,0,1);
    ps.addpoint(p1);
    ps.addpoint(p2);
    ps.addpoint(p3);
    ps.addpoint(p4);
    ps.addpoint(p5);
    ps.sort();
    ps.print();
//-----------------------------------------------------------------------------
    SDL_GL_SwapBuffers();
}

---

### Post by wmcbrine on 2006-03-20
[QUOTE=pranith]
#include "point.h"
#include "sphere.h"
#include "greatcircle.h"
#include "greatarc.h"
#include "polygon.h"
#include "smallcircle.h"
#include "band.h"
#include "pointset.h"
[/QUOTE]
Where do these come from?

---

### Post by pranith on 2006-03-20
those are part of my program 
this program is working fine on my other suse box but when I tried to run it on mu ubuntu box it is giving this error

---

### Post by biocrasher on 2006-03-20
&#919;&#953;.

I've compiled your program like shown below and I got a normal window( it's the same code without the commented lines and with two dummy classes).

I have SDL 1.2.8 on breezy,so I would suggest that you look for any recent changes on your classes.


```

#include <iostream>
#include <vector>
#include <SDL/SDL.h>
#include <SDL/SDL_opengl.h>
#include <math.h>
#include <GL/glut.h>
#define radius 2
#define ORIGINX 0
#define ORIGINY 0
#define ORIGINZ 0

// #include "point.h"
// #include "sphere.h"
// #include "greatcircle.h"
// #include "greatarc.h"
// #include "polygon.h"
// #include "smallcircle.h"
// #include "band.h"
// #include "pointset.h"
class point{
    public:
        int x,y,z;
        point(int x1,int y1,int z1){
            x=x1;
            y=y1;
            z=z1;
        };
};
class pointset{
    public:
        void sort(){/*stub*/};
        void print(){/*stub*/};
        void addpoint(point p){/*stub*/};
};
int xrotation=0,yrotation=0;
bool horiz=false,vertical=false;
int main(int argc, char *argv[]);
void render(void);
void init(void);

int main(int argc, char *argv[]){
    SDL_Init( SDL_INIT_VIDEO ); // Initialise the SDL Video bit
    SDL_WM_SetCaption( "SDL + OpenGL", NULL );
    const SDL_VideoInfo *pSDLVideoInfo = SDL_GetVideoInfo();
    if( !pSDLVideoInfo ){
        printf("SDL_GetVideoInfo() failed. SDL Error: %s\n", SDL_GetError());
        SDL_Quit();
        return 1;
    }
    int nFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER | SDL_HWPALETTE;
    if( pSDLVideoInfo->hw_available ) // Hardware surfaces enabled?
        nFlags |= SDL_HWSURFACE;
    else
        nFlags |= SDL_SWSURFACE;
    if( pSDLVideoInfo->blit_hw ) // Hardware supported blitting?
        nFlags |= SDL_HWACCEL;
    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 ); // Enable OpenGL Doublebuffering
    // Create our rendering surface
    SDL_Surface *pSDLSurface = SDL_SetVideoMode( 400, 400, 32, nFlags );
    if( !pSDLSurface ){
        printf( "Call to SDL_SetVideoMode() failed! - SDL_Error: %s\n", SDL_GetError() );
        SDL_Quit();
        return 1;
    }
    // Init OpenGL...
    init();
    bool bDone = false;
    SDL_Event Event;

    while( !bDone ){
        // printf( "%d\n", bDone );
        while(SDL_PollEvent( &Event )){
            switch( Event.type ){
                case SDL_QUIT:
                    bDone = true;
                break;
                case SDL_KEYDOWN:{
                    switch( Event.key.keysym.sym ){
                        case SDLK_ESCAPE:
                            SDL_Quit();
                            exit(0);
                        break;
                        case SDLK_UP:
                            yrotation=(yrotation+5)%360;
                            vertical=true;
                            break;
                        case SDLK_DOWN:
                            yrotation=(yrotation-5)%360;
                            vertical=true;
                            break;
                        case SDLK_RIGHT:
                            xrotation=(xrotation+5)%360;
                            horiz=true;
                            break;
                        case SDLK_LEFT:
                            xrotation=(xrotation-5)%360;
                            horiz=true;
                            break;
                    // case SDLK_RETURN:
                    // SDL_WM_ToggleFullScreen(pSDLSurface);
                    // break;
                        default:
                            break;
                    }
                }
                case SDL_KEYUP:{
                    switch( Event.key.keysym.sym ){
                        case SDLK_ESCAPE:
                            SDL_Quit();
                            exit(0);
                            break;
                        case SDLK_UP:
                            yrotation=(yrotation+5)%360;
                            vertical=true;
                            break;
                        case SDLK_DOWN:
                            yrotation=(yrotation-5)%360;
                            vertical=true;
                            break;
                        case SDLK_RIGHT:
                            xrotation=(xrotation+5)%360;
                            horiz=true;
                            break;
                        case SDLK_LEFT:
                            xrotation=(xrotation-5)%360;
                            horiz=true;
                            break;
                        // case SDLK_RETURN:
                        // SDL_WM_ToggleFullScreen(pSDLSurface);
                        // break;
                        default:
                            break;
                    }
                }
                case SDL_MOUSEBUTTONDOWN:{
                    switch( Event.button.button){
                        case SDL_BUTTON_LEFT:
                            // up=1;
                            break;
                    }
                }
                default:
                    break;
                }
        }
        render();
    // SDL_Delay(20);
    }
    SDL_Quit();
    return 0;
}

//-----------------------------------------------------------------------------
// Name: init()
// Desc: Init OpenGL context for rendering.
//-----------------------------------------------------------------------------
void init( void ){
    glClearColor( 0.0f, 0.0f, 0.0f, 0.0f );
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluPerspective( 50.0f,4/3, 0.1f, 1000.0f);
    glMatrixMode( GL_MODELVIEW );
    glEnable(GL_DEPTH_TEST);
    glDepthFunc(GL_LEQUAL);
}
//-----------------------------------------------------------------------------
// Name: render()
// Desc: Called when the SDL window is ready to render
//-----------------------------------------------------------------------------
void render( void ){
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glLoadIdentity();
    //-------------------------Ur drawing here-------------------------------------
    float location[] = { 0.0, 1000.0, -100.0 ,0.0};
    // float direction[] = { 0, 0, 10 };
    float color[] = { 1, 1, 1, 0 };
    glEnable( GL_LIGHTING );
    glEnable( GL_LIGHT0 );
    glLightfv( GL_LIGHT0, GL_POSITION, location );
    glLightfv( GL_LIGHT0, GL_AMBIENT, color );
    glLightfv( GL_LIGHT0, GL_SPECULAR, color );
    glLightfv( GL_LIGHT0, GL_DIFFUSE, color );
    glTranslatef(0,0,-10);
    pointset ps;
    point p1(4,0,0);
    point p2(2,1,0);
    point p3(6,0,1);
    point p4(8,0,1);
    point p5(7,0,1);
    ps.addpoint(p1);
    ps.addpoint(p2);
    ps.addpoint(p3);
    ps.addpoint(p4);
    ps.addpoint(p5);
    ps.sort();
    ps.print();
    //-----------------------------------------------------------------------------
    SDL_GL_SwapBuffers();
} 


```

---

### Post by pranith on 2006-03-20
Thanks it worked...

---

### Post by hod139 on 2006-03-20
Why are you including GLUT if you are using SDL?

---

### Post by pranith on 2006-03-20
some of my modules needed glut also...

---

### Post by net-x on 2006-03-22
Can't found "SDL/SDL_opengl.h", why?

---

### Post by hod139 on 2006-03-22
You may have wanted to start your own thread to ask this question.

First, make sure you have libsdl1.2-dev installed.
```
sudo apt-get install libsdl1.2-dev
``` 
In your source files, you should be writing:
#include <SDL.h>
and using sdl-config to set up include and linking paths.  For the correct include paths you type:
```
sdl-config --cflags
```

And for library settings you type
```
sdl-config --libs
```

Then you can compile your file as
```
g++ -o foo `sdl-config --cflags` `sdl-config --libs` foo.cpp
``` 
Or, if you have a makefile, you can do something like this 
```
 
SDL_CFLAGS := $(shell sdl-config --cflags)
SDL_LDFLAGS := $(shell sdl-config --libs)

##Debug build
CPPFLAGS =  -g3 -Wall ##Plus other CPP_FLAGS 
CPPFLAGS +=  ${SDL_CFLAGS}
LDFLAGS = ## Any Linking flags e.g. -lGL
LDFLAGS += ${SDL_LDFLAGS}

```

---

### Post by net-x on 2006-03-22
Thanks for help.
I compile as 
```
g++ sdl.cpp -o sdl `sdl-config --libs --cflags` -I/opt/mesa/include -lGL -lGLU
```

---

### Post by biocrasher on 2006-03-23
Did you write #include "SDL/SDL_opengl.h" ?
I've seen this in a few tutorials and it is not correct.
If so, you should include as <SDL/SDL_opengl.h>

---

### Post by net-x on 2006-03-24
Sorry, It's my mistake.
I compile as ```
g++ sdl.cpp -o sdl `sdl-config --libs --cflags` -I/opt/mesa/include -lGL -lGLU
```
It's Ok. Thanks everyone.

---

