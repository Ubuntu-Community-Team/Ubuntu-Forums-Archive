---
title: "SDL troubles (-lmingw32 not found)"
date: 2010-09-08
forum: Programming Talk
---

### Post by Iubdou on 2010-09-08
Afternoon, folks. I recently had some SDL difficulties and you guys managed to fix them quite quickly, so I'm gonna push my luck and request your assistance once more. I'm trying to run a program that displays sprites based on the direction key you press and it compiles just fine but won't build. Apparently the compiler assumes that the function declarations are just fine but it can't actually find the file mingw32 when it tries to build it (according to various tutorials I looked over before coming here). Anyone have any idea what's producing these errors?
 
/usr/bin/ld: cannot find -lmingw32
collect2: ld returned 1 exit status
Compilation failed.

I'll post the code if it's needed to find the bug. Thanks a bunch.

---

### Post by Ryaether on 2010-09-08
I'm a little unsure of what you're trying to do.

Are you trying to compile for Windows from Ubuntu?  If so, search synaptic for mingw packages and make sure you have them installed.

Otherwise, if you're just trying to build and run it on Ubuntu, then I don't know why you're linking mingw.  It's the Minimalist GNU for Windows, so have you tried just not linking it?  Have you perhaps accidentally downloaded source code for windows?  (although since it's SDL even if you only have source code for windows it might only take a few tweaks to make it build on linux).

I might be able to help more if you could provide a link to the source your trying to build, or gave more info on how your building it (e.g. CodeBlocks? makefile?) and what other libraries you are using.

---

### Post by Iubdou on 2010-09-08
The arguments:
g++ -Wall -c "%f" -lmingw32 -lSDLmain -lSDL

The code itself, with comments for clarity. (Probably buggy in other ways too, but none that I can see)
```
//The headers
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include <string>

//Screen attributes
const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;

//The event structure
SDL_Event event;

// Load the surfaces
//SDL_Surface *background = NULL;
SDL_Surface *playerimage;
SDL_Surface *screen;

// Player sprite data
SDL_Rect up[2];
SDL_Rect down[2];
SDL_Rect left[2];
SDL_Rect right[2];

SDL_Surface *load_image( std::string filename )
{
    //The image that's loaded
    SDL_Surface* loadedImage = NULL;

    //The optimized surface that will be used
    SDL_Surface* optimizedImage = NULL;

    //Load the image
    loadedImage = SDL_LoadBMP( filename.c_str() );

    //If the image loaded
    if( loadedImage != NULL )
    {
        //Create an optimized surface
        optimizedImage = SDL_DisplayFormat( loadedImage );

        //Free the old surface
        SDL_FreeSurface( loadedImage );

        //If the surface was optimized
        if( optimizedImage != NULL )
        {
            //Color key surface
            SDL_SetColorKey( optimizedImage, SDL_SRCCOLORKEY, SDL_MapRGB( optimizedImage->format, 0, 0xFF, 0xFF ) );
        }
    }

    //Return the optimized surface
    return optimizedImage;
}

void apply_surface( int x, int y, SDL_Surface* source, SDL_Surface* destination, SDL_Rect* clip = NULL )
{
    //Holds offsets
    SDL_Rect offset;

    //Get offsets
    offset.x = x;
    offset.y = y;

    //Blit
    SDL_BlitSurface( source, clip, destination, &offset );
}

bool init()
{
    //Initialize all SDL subsystems
    if( SDL_Init( SDL_INIT_EVERYTHING ) == -1 )
    {
        return 0;
    }

    //Set up the screen
    screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );

    //If there was an error in setting up the screen
    if( screen == NULL )
    {
        return 0;
    }

    //Set the window caption
    SDL_WM_SetCaption( "Press an Arrow Key", NULL );

    //If everything initialized fine
    return 1;
}

bool load_files()
{
    //Load the background image
    playerimage = load_image( "herocharsworldmap.bmp" );

    //If there was a problem in loading the sprites
    if( playerimage == NULL )
    {
        return false;
    }

    //If everything loaded fine
    return true;
}

void clean_up()
{
    //Free the surfaces
    SDL_FreeSurface( playerimage );
    SDL_FreeSurface( screen );

    //Quit SDL
    SDL_Quit();
}

int main( int argc, char* args[] )
{
    //Quit flag
    int quit = 0;
    
    //Direction and frame
    int Direct = 0;
    int Frame = 0;

    //Initialize
    if( init() == 0 )
    {
        return 1;
    }

    //Load the files
    if( load_files() == 0 )
    {
        return 1;
    }
    
    //Clip range for down 1
    down[ 0 ].x = 0;
    down[ 0 ].y = 0;
    down[ 0 ].w = 13;
    down[ 0 ].h = 15;

    //Clip range for down 2
    down[ 1 ].x = 14;
    down[ 1 ].y = 0;
    down[ 1 ].w = 13;
    down[ 1 ].h = 15;

    //Clip range for left 1
    left[ 0 ].x = 28;
    left[ 0 ].y = 0;
    left[ 0 ].w = 13;
    left[ 0 ].h = 15;

    //Clip range for left 2
    left[ 1 ].x = 42;
    left[ 1 ].y = 0;
    left[ 1 ].w = 13;
    left[ 1 ].h = 15;
    
    //Clip range for up 1
    up[ 0 ].x = 56;
    up[ 0 ].y = 0;
    up[ 0 ].w = 13;
    up[ 0 ].h = 15;

    //Clip range for up 2
    up[ 1 ].x = 70;
    up[ 1 ].y = 0;
    up[ 1 ].w = 13;
    up[ 1 ].h = 15;

    //Clip range for right 1
    right[ 0 ].x = 84;
    right[ 0 ].y = 0;
    right[ 0 ].w = 13;
    right[ 0 ].h = 15;

    //Clip range for right 2
    right[ 1 ].x = 96;
    right[ 1 ].y = 0;
    right[ 1 ].w = 13;
    right[ 1 ].h = 15;

    //Fill the screen white
    SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0xFF, 0xFF, 0xFF ) );

    //While the user hasn't quit
    while( quit == 0 )
    {
        //If there's an event to handle
        if( SDL_PollEvent( &event ) )
        {
            //If a key was pressed
            if( event.type == SDL_KEYDOWN )
            {
                //Set the proper message surface
                switch( event.key.keysym.sym )
                {
                    case SDLK_DOWN:
                        Direct = 1; break;
                    case SDLK_LEFT:
                        Direct = 2; break;
                    case SDLK_UP:
                        Direct = 3; break;
                    case SDLK_RIGHT:
                        Direct = 4; break;
                    default:
                    break;
                }
            }

            //If the user has Xed out the window
            else if( event.type == SDL_QUIT )
            {
                //Quit the program
                quit = 1;
            }
        }

        //If a message needs to be displayed
        if( Direct != 0 )
        {
            //Fill the screen white
            SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0xFF, 0xFF, 0xFF ) );

            //Apply the sprite centered on the screen
            switch( Direct ){
                case 1:
                apply_surface( ( SCREEN_WIDTH - playerimage->w ) / 2, ( SCREEN_HEIGHT - playerimage->h ) / 2, playerimage, screen, &up[1] );
                break;
                
                case 2:
                apply_surface( ( SCREEN_WIDTH - playerimage->w ) / 2, ( SCREEN_HEIGHT - playerimage->h ) / 2, playerimage, screen, &left[1] );
                break;
                
                case 3:
                apply_surface( ( SCREEN_WIDTH - playerimage->w ) / 2, ( SCREEN_HEIGHT - playerimage->h ) / 2, playerimage, screen, &down[1] );
                break;
                
                case 4:
                apply_surface( ( SCREEN_WIDTH - playerimage->w ) / 2, ( SCREEN_HEIGHT - playerimage->h ) / 2, playerimage, screen, &right[1] );
                break;
            }

            //Reset the direction
            Direct = 0;
            if( Frame == 1 ){
                Frame = 0;
            }
            else{
                Frame = 1;
            }
        }

        //Update the screen
        if( SDL_Flip( screen ) == -1 )
        {
            return 1;
        }
    }

    //Clean up
    clean_up();

    return 0;
}
```

Thanks a bunch

---

### Post by Ryaether on 2010-09-08
Ok, I don't think you want to be linking mingw

I copied your code into a file named 'test.cpp'
then I was able to compile it with
g++ test.cpp -o stuff -Wall -lSDL -lSDL_image

which outputs an executable named 'stuff'
and it seems to run fine for me, so let me know if you're still running into problems

---

### Post by Iubdou on 2010-09-08
Remind me never to take the tutorials word for how things should work in the future. Thanks again. *resumes tweaking code*

---

### Post by ChurroLoco on 2010-09-09
> **Ryaether said:**
> If so, search synaptic for mingw packages and make sure you have them installed.

Heh, I didn't know they had the mingw library in the repo.  Never thought of doing something like that.  Strange way to develop, but that might come in handy.

:popcorn:

---

