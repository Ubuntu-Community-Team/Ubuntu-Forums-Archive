---
title: "why is this segfaulting"
date: 2008-11-26
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-26
heres the code

[php]#include "SDL/SDL.h"
#include <string>
#include "SDL/SDL_image.h"
#include <cstdlib>
#include <ctime>

//Constants
const int SCREEN_WIDTH = 630;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;
const int FRAMES_PER_SECOND = 20;
const int STAR_NUMBER = 25;
//prototypes
SDL_Surface *loadImage( std::string filename, int Red = 0, int Green = 0, int Blue = 0);
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination);
class Ship;
class Player;
class Timer;
class Missile;
class Star;
//SDL variables
SDL_Surface *screen = NULL;
SDL_Surface *ship = NULL;
SDL_Surface *bullet = NULL;
SDL_Surface *stars[STAR_NUMBER];
SDL_Event event;
//classes and structs
class Missile
{
    private:
        int x, y;
        int velY;
    public:
        
        bool fired;
        SDL_Surface* bullet; 

        Missile()
        {
            bullet = loadImage("bullet.bmp", 255, 255, 255);
        }

        void fire(int X, int Y)
        {
            x = X;
            y = Y;

            velY = 20;

            bool fired = false;
            
            applySurface(x, y, bullet, screen);
        }

        void move()
        {
            y += velY;
        }
};
class Star
{
    int velY;
    public:
            int x, y;
        time_t time;
        Star()
        {
            x = (rand()%SCREEN_WIDTH)+1;
            y = -5;
            velY = 5;
        }

        void move()
        {
            y += velY;

            if (y > SCREEN_HEIGHT )
            {
                y = -5;
                x = (rand()%SCREEN_WIDTH)+1;
            }
        }
};

class Ship
{
    protected:
      int x, y, velX, velY; 
      Missile *ammo;
    public:
      void show()
      {
        applySurface(x, y, ship, screen);
      }

};
class Player: public Ship
{
    int ammoSlot;
    public:
    Player(int X, int Y, int VelX, int VelY = 0)
    {
        x = X;
        y = Y;
        velX = VelX;
        velY = VelY;

        ammo = new Missile[10];
    }

    void handleInput()
    {            
        Uint8* Keys = SDL_GetKeyState(NULL);

        if(Keys[SDLK_LEFT])
        {
            if (x >= 0)
            {
                x -= velX;
            }
        }

        if(Keys[SDLK_RIGHT])
        {
            if (x <= SCREEN_WIDTH - 70)
            {
                x += velX;
            }
        }

        if(Keys[SDLK_SPACE])
        {
            if(ammo[ammoSlot].fired = false)
            {
                ammo[ammoSlot].fire(x + 35, y);            
            }
        }
    }

    void show()
    {
        applySurface(x, y, ship, screen);
    }

};

class Timer
{
    private:
    //The clock time when the timer started
    int startTicks;
    
    //The ticks stored when the timer was paused
    int pausedTicks;
    
    //The timer status
    bool paused;
    bool started;
    
    public:
    //Initializes variables
    Timer();
    
    //The various clock actions
    void start();
    void stop();
    void pause();
    void unpause();
    
    //Gets the timer's time
    int get_ticks();
    
    //Checks the status of the timer
    bool is_started();
    bool is_paused();    
};
//outside class methods
Timer::Timer()
{
    //Initialize the variables
    startTicks = 0;
    pausedTicks = 0;
    paused = false;
    started = false;    
}

void Timer::start()
{
    //Start the timer
    started = true;
    
    //Unpause the timer
    paused = false;
    
    //Get the current clock time
    startTicks = SDL_GetTicks();    
}

void Timer::stop()
{
    //Stop the timer
    started = false;
    
    //Unpause the timer
    paused = false;    
}

void Timer::pause()
{
    //If the timer is running and isn't already paused
    if( ( started == true ) && ( paused == false ) )
    {
        //Pause the timer
        paused = true;
    
        //Calculate the paused ticks
        pausedTicks = SDL_GetTicks() - startTicks;
    }
}

void Timer::unpause()
{
    //If the timer is paused
    if( paused == true )
    {
        //Unpause the timer
        paused = false;
    
        //Reset the starting ticks
        startTicks = SDL_GetTicks() - pausedTicks;
        
        //Reset the paused ticks
        pausedTicks = 0;
    }
}

int Timer::get_ticks()
{
    //If the timer is running
    if( started == true )
    {
        //If the timer is paused
        if( paused == true )
        {
            //Return the number of ticks when the timer was paused
            return pausedTicks;
        }
        else
        {
            //Return the current time minus the start time
            return SDL_GetTicks() - startTicks;
        }    
    }
    
    //If the timer isn't running
    return 0;    
}

bool Timer::is_started()
{
    return started;    
}

bool Timer::is_paused()
{
    return paused;    
}

class Game
{
         public:
             Game()
                   : player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5)
            {
            }
        Player player;
        Timer fps;
};
//globals

Player player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5);
Timer fps;
Star* constalation[STAR_NUMBER];
//Game game;

//functions

void updateStars(Star** array)
{
    for(int i = 0; i < STAR_NUMBER; i++)
    {
        array[i]->move();
        applySurface(array[i]->x, array[i]->y, stars[i], screen);

tryAgain:
        if(array[i]->y < 0 && 1 < difftime(array[i]->time, array[i-2]->time))
        {
            array[i]->move();
            applySurface(array[i]->x, array[i]->y, stars[i], screen);
        }

        else if (array[i]->y < 0)
        {
            goto tryAgain;
        }
    }
}
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination )
{
    //Make a temporary rectangle to hold the offsets
    SDL_Rect offset;
    
    //Give the offsets to the rectangle
    offset.x = x;
    offset.y = y;
    
    //Blit the surface
    SDL_BlitSurface( source, NULL, destination, &offset );
}
SDL_Surface *loadImage( std::string filename, int Red, int Green, int Blue ) 
{ 
    //The image that's loaded 
    SDL_Surface* loadedImage = NULL; 
    
    //The optimized image that will be used 
    SDL_Surface* optimizedImage = NULL; 
    
    //Load the image using SDL_image 
    loadedImage = IMG_Load( filename.c_str() );
       
    //If the image loaded 
    if( loadedImage != NULL ) 
    { //Create an optimized image 
        optimizedImage = SDL_DisplayFormat( loadedImage ); //Free the old image 
        SDL_FreeSurface( loadedImage );
        if( optimizedImage != NULL ) 
        { 
            //Map the color key 
            Uint32 colorkey = SDL_MapRGB( optimizedImage->format, Red, Green, Blue );
            //Set all pixels of color key 
            SDL_SetColorKey( optimizedImage, SDL_SRCCOLORKEY, colorkey ); 
        }     
    } 
    
    //Return the optimized image 
    return optimizedImage; 
}

int init()
{
    //set up randoms
    srand((unsigned)time(0));

    //initiate SDL
    if( SDL_Init( SDL_INIT_EVERYTHING ) == -1 )
        {
        //something went wrong
            return 1;    
        }
    
    for (int i = 0; i < STAR_NUMBER; i++)
    {
        constalation[i] = new Star();
    }

    //set up the screen and check it
    screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );
    
    if (screen == NULL)
    {
        return 1;
    }
    SDL_EnableKeyRepeat(1, 10);
    SDL_WM_SetCaption( "Space Shooter", NULL );
    
    //set up image and blit
    ship = loadImage("player.bmp", 255, 255, 255);
    bullet = loadImage("bullet.bmp", 255, 255, 255);
    
    for(int i = 0; i < STAR_NUMBER; i++)
    {
        stars[i] = loadImage("star.bmp");
    }

    applySurface((SCREEN_WIDTH/2),(SCREEN_HEIGHT-75), ship, screen);

    //Update the screen
    if( SDL_Flip( screen ) == -1 )
           { 
        return 1; 
    } 
    return 0;
}

int loop()
{
    bool quit = false;

    while (quit == false)
    {
        fps.start();

        while(SDL_PollEvent(&event))
        {
            if (event.type == SDL_QUIT)
            {
                quit = true;
            }
            
            //handle player input
            player.handleInput();
            
        }
        //Fill the screen white
        SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0, 0, 0 ) );
         
        //Show the dot on the screen 
        player.show(); 
        
        updateStars(constalation);

        //Update the screen 
        if( SDL_Flip( screen ) == -1 ) 
        { 
             return 1; 
        } 
        
        //Cap the frame rate 
        if( fps.get_ticks() < 1000 / FRAMES_PER_SECOND ) 
        { 
             SDL_Delay( ( 1000 / FRAMES_PER_SECOND ) - fps.get_ticks() ); 
        } 
    }

    return 0;
}

void close()
{
    //Free the surfaces 
    SDL_FreeSurface(screen);
    SDL_FreeSurface(ship);
    SDL_FreeSurface(bullet);
    //Quit 
    SDL_Quit(); 
}

int main(int argc, char* args[])
{
    int error;
    error = init();
    if (error == 0)
    {
        loop();
        close();
    }
    return error;
}[/php]the problem is probably in the updateStars function...my last modification was the for loop and goto (i know...)

the stars blit the first time in a solid row (they should because i havnt told them not to yet) but they hit the bottom of the screen and segfault

ignore my use of globals please

also i get this error:

```
g++ -o test shooter.cpp -lSDL -lSDL_image
/tmp/ccCF2T8K.o: In function `Missile::Missile()':
shooter.cpp:(.text._ZN7MissileC1Ev[Missile::Missile()]+0x45): undefined reference to `Missile::bullet'
/tmp/ccCF2T8K.o: In function `Missile::fire(int, int)':
shooter.cpp:(.text._ZN7Missile4fireEii[Missile::fire(int, int)]+0x3e): undefined reference to `Missile::bullet'
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

---

### Post by jimi_hendrix on 2008-11-26
fixed that error by removing a static keyword (updated code) but now it segfaults on start up

---

### Post by jimi_hendrix on 2008-11-26
[php]#include "SDL/SDL.h"
#include <string>
#include "SDL/SDL_image.h"
#include <cstdlib>
#include <ctime>
#include <iostream>

//Constants
const int SCREEN_WIDTH = 630;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;
const int FRAMES_PER_SECOND = 20;
const int STAR_NUMBER = 25;
//prototypes
SDL_Surface *loadImage( std::string filename, int Red = 0, int Green = 0, int Blue = 0);
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination);
class Ship;
class Player;
class Timer;
class Missile;
class Star;
//SDL variables
SDL_Surface *screen = NULL;
SDL_Surface *ship = NULL;
SDL_Surface *bullet = NULL;
SDL_Surface *stars[STAR_NUMBER];
SDL_Event event;
//classes and structs
class Missile
{
    private:
        int x, y;
        int velY;
    public:
        
        bool fired;
        SDL_Surface* bullet; 

        Missile()
        {
            bullet = loadImage("bullet.bmp", 255, 255, 255);
        }

        void fire(int X, int Y)
        {
            x = X;
            y = Y;

            velY = 20;

            bool fired = false;
            
            applySurface(x, y, bullet, screen);
        }

        void move()
        {
            y += velY;
        }
};
class Star
{
    int velY;
    public:
            int x, y;
        time_t time;
        Star()
        {
            x = (rand()%SCREEN_WIDTH)+1;
            y = -5;
            velY = 5;
        }

        void move()
        {
            y += velY;

            if (y > SCREEN_HEIGHT )
            {
                y = -5;
                x = (rand()%SCREEN_WIDTH)+1;
            }
        }
};

class Ship
{
    protected:
      int x, y, velX, velY; 
      Missile *ammo;
    public:
      void show()
      {
        applySurface(x, y, ship, screen);
      }

};
class Player: public Ship
{
    int ammoSlot;
    public:
    Player(int X, int Y, int VelX, int VelY = 0)
    {
        x = X;
        y = Y;
        velX = VelX;
        velY = VelY;
        ammoSlot = 0;

        ammo = new Missile[10];
    }

    void handleInput()
    {            
        Uint8* Keys = SDL_GetKeyState(NULL);

        if(Keys[SDLK_LEFT])
        {
            if (x >= 0)
            {
                x -= velX;
            }
        }

        if(Keys[SDLK_RIGHT])
        {
            if (x <= SCREEN_WIDTH - 70)
            {
                x += velX;
            }
        }

        if(Keys[SDLK_SPACE])
        {
            if(ammo[ammoSlot].fired == false)
            {
                ammo[ammoSlot].fire(x + 35, y);
                ammo[ammoSlot].fired = true;
                ammoSlot++;
            }
        }
    }

    void show()
    {
        applySurface(x, y, ship, screen);
    }

};

class Timer
{
    private:
    //The clock time when the timer started
    int startTicks;
    
    //The ticks stored when the timer was paused
    int pausedTicks;
    
    //The timer status
    bool paused;
    bool started;
    
    public:
    //Initializes variables
    Timer();
    
    //The various clock actions
    void start();
    void stop();
    void pause();
    void unpause();
    
    //Gets the timer's time
    int get_ticks();
    
    //Checks the status of the timer
    bool is_started();
    bool is_paused();    
};
//outside class methods
Timer::Timer()
{
    //Initialize the variables
    startTicks = 0;
    pausedTicks = 0;
    paused = false;
    started = false;    
}

void Timer::start()
{
    //Start the timer
    started = true;
    
    //Unpause the timer
    paused = false;
    
    //Get the current clock time
    startTicks = SDL_GetTicks();    
}

void Timer::stop()
{
    //Stop the timer
    started = false;
    
    //Unpause the timer
    paused = false;    
}

void Timer::pause()
{
    //If the timer is running and isn't already paused
    if( ( started == true ) && ( paused == false ) )
    {
        //Pause the timer
        paused = true;
    
        //Calculate the paused ticks
        pausedTicks = SDL_GetTicks() - startTicks;
    }
}

void Timer::unpause()
{
    //If the timer is paused
    if( paused == true )
    {
        //Unpause the timer
        paused = false;
    
        //Reset the starting ticks
        startTicks = SDL_GetTicks() - pausedTicks;
        
        //Reset the paused ticks
        pausedTicks = 0;
    }
}

int Timer::get_ticks()
{
    //If the timer is running
    if( started == true )
    {
        //If the timer is paused
        if( paused == true )
        {
            //Return the number of ticks when the timer was paused
            return pausedTicks;
        }
        else
        {
            //Return the current time minus the start time
            return SDL_GetTicks() - startTicks;
        }    
    }
    
    //If the timer isn't running
    return 0;    
}

bool Timer::is_started()
{
    return started;    
}

bool Timer::is_paused()
{
    return paused;    
}

class Game
{
         public:
             Game()
                   : player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5)
            {
            }
        Player player;
        Timer fps;
};
//globals

Player player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5);
Timer fps;
Star* constalation[STAR_NUMBER];
//Game game;

//functions

void updateStars(Star** array)
{
    for(int i = 0; i < STAR_NUMBER; i++)
    {
        array[i]->move();
        applySurface(array[i]->x, array[i]->y, stars[i], screen);

tryAgain:
        if(array[i]->y < 0 && 1 < difftime(array[i]->time, array[i-2]->time))
        {
            array[i]->move();
            applySurface(array[i]->x, array[i]->y, stars[i], screen);
        }

        else if (array[i]->y < 0)
        {
            goto tryAgain;
        }
    }
}
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination )
{
    //Make a temporary rectangle to hold the offsets
    SDL_Rect offset;
    
    //Give the offsets to the rectangle
    offset.x = x;
    offset.y = y;
    
    //Blit the surface
    SDL_BlitSurface( source, NULL, destination, &offset );
}
SDL_Surface *loadImage( std::string filename, int Red, int Green, int Blue ) 
{ 
    //The image that's loaded 
    SDL_Surface* loadedImage = NULL; 
    
    //The optimized image that will be used 
    SDL_Surface* optimizedImage = NULL; 
    
    //Load the image using SDL_image 
    loadedImage = IMG_Load( filename.c_str() );
       
    //If the image loaded 
    if( loadedImage != NULL ) 
    { //Create an optimized image 
        optimizedImage = SDL_DisplayFormat( loadedImage ); //Free the old image 
        SDL_FreeSurface( loadedImage );
        if( optimizedImage != NULL ) 
        { 
            //Map the color key 
            Uint32 colorkey = SDL_MapRGB( optimizedImage->format, Red, Green, Blue );
            //Set all pixels of color key 
            SDL_SetColorKey( optimizedImage, SDL_SRCCOLORKEY, colorkey ); 
        }     
    } 
    
    //Return the optimized image 
    return optimizedImage; 
}

int init()
{
    //set up randoms
    srand((unsigned)time(0));

    //initiate SDL
    if( SDL_Init( SDL_INIT_EVERYTHING ) == -1 )
        {
        //something went wrong
            return 1;    
        }
    
    for (int i = 0; i < STAR_NUMBER; i++)
    {
        constalation[i] = new Star();
    }

    std::cout << "constalation setup" << std::endl;

    //set up the screen and check it
    screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );
    
    if (screen == NULL)
    {
        return 1;
    }
    SDL_EnableKeyRepeat(1, 10);
    SDL_WM_SetCaption( "Space Shooter", NULL );
    
    //set up image and blit
    ship = loadImage("player.bmp", 255, 255, 255);
    bullet = loadImage("bullet.bmp", 255, 255, 255);
    
    for(int i = 0; i < STAR_NUMBER; i++)
    {
        stars[i] = loadImage("star.bmp");
    }

    applySurface((SCREEN_WIDTH/2),(SCREEN_HEIGHT-75), ship, screen);

    //Update the screen
    if( SDL_Flip( screen ) == -1 )
           { 
        return 1; 
    } 
    return 0;
}

int loop()
{
    bool quit = false;

    while (quit == false)
    {
        fps.start();

        while(SDL_PollEvent(&event))
        {
            if (event.type == SDL_QUIT)
            {
                quit = true;
            }
            
            //handle player input
            player.handleInput();
            
        }
        //Fill the screen white
        SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0, 0, 0 ) );
         
        //Show the dot on the screen 
        player.show(); 
        
        updateStars(constalation);

        //Update the screen 
        if( SDL_Flip( screen ) == -1 ) 
        { 
             return 1; 
        } 
        
        //Cap the frame rate 
        if( fps.get_ticks() < 1000 / FRAMES_PER_SECOND ) 
        { 
             SDL_Delay( ( 1000 / FRAMES_PER_SECOND ) - fps.get_ticks() ); 
        } 
    }

    return 0;
}

void close()
{
    //Free the surfaces 
    SDL_FreeSurface(screen);
    SDL_FreeSurface(ship);
    SDL_FreeSurface(bullet);
    //Quit 
    SDL_Quit(); 
}

int main(int argc, char* args[])
{
    int error;
    error = init();
    if (error == 0)
    {
        loop();
        close();
    }
    return error;
}[/php]

updated again...comment out line 110 and it runs

---

### Post by monkeyking on 2008-11-26
You should consider using a debugger, or memory profiling program.

These are quite good at hunting down these kind of errors.


gdb and valgrind

good luck

---

### Post by doojsdad on 2008-11-26
You have bullet as a global and a member of Missle. The global one is probably still NULL after the Missle constructor and you use it somewhere.

---

### Post by jimi_hendrix on 2008-11-26
what debugger do you recommend?

---

### Post by jimi_hendrix on 2008-11-26
i removed the global bullet and commented out all lines it affected...still segfauling

---

### Post by escapee on 2008-11-26
Debug 101: Put some couts in your code around where you think it might be.  Where they stop popping up is likely where your error will be around.  Not valid in all cases, but here will be fine.

---

### Post by jimi_hendrix on 2008-11-26
ok

---

### Post by jimi_hendrix on 2008-11-26
i did this in a few places but ill add a few more

---

### Post by stroyan on 2008-11-26
I tend to use gdb and cgdb, which adds text based windowing to gdb.
The ddd debugger is a more beginner friendly front-end for gdb.
It allows you to debug with mouse buttons and menus.
But it also shows the gdb commands that implement many of the menu selections.
That can gradually lead you into using the text based commands that are more powerful for an experienced user.

  ddd does have some nice features that plain gdb lacks.
You can hover the mouse over a variable name to see its current value.
You can use the right-button menu to "display" a variable in a window that will show structure contents and diagram the structs that pointers point to.

---

### Post by jimi_hendrix on 2008-11-26
thanks for pointing out ddd

---

### Post by monkeyking on 2008-11-26
Hi,
use gdb as so.

Compile your program like

```

g++ -ggdb yourprogram.cpp

```

Then run your program from within gdb,
thats is
```

gdb ./yourProgram

```

Then type

```
run [YOURPROGRAM PARS]
```

Then gdb should tell which line that cause the segfault.

edit.
I never use ddd,
since I don't really use the debugger part.
I only use it to catch my segfaults ;)

---

### Post by dribeas on 2008-11-26
> **jimi_hendrix said:**
> fixed that error by removing a static keyword (updated code) but now it segfaults on start up

It is confusing when you edit the post to correct the error. Note that there will be no trace of the error and the solution for others to browse in the future. I believe that it would be better by keeping the original problem and the solution together.

I also find confusing the fact that you have (probably) changed the title of the OP but not the contents. The post now has a SEGFAULT in the title but it is centered in a non-existing compilation error!

Now the answer to the original problem. When you declare an static attribute of a class inside the class brackets, you are just defining that it will be defined at some later time. It is perfectly equivalent to a extern declaration in C.

If bullet is meant to be shared by all Missile objects then you should declare it static, and add in one compilation unit (and only one) the following line:

```

        SDL_Surface* Missile::bullet; 

```

That line is what really defines the symbol and reserves space for the pointer in your object code.

Also note that it does not make sense to load the image in each and every Missile object construction. If it is meant to be class wide, you should initialize it once (probably in an static method) and leave it as it is.

It is not recommended either having public data. A user, by mistake or else, could delete the image you have loaded at any given time without your objects noticing, and that will kill your application at a later time with a SIGSEGV.

---

### Post by jimi_hendrix on 2008-11-26
> **dribeas said:**
> It is confusing when you edit the post to correct the error. Note that there will be no trace of the error and the solution for others to browse in the future. I believe that it would be better by keeping the original problem and the solution together.

I also find confusing the fact that you have (probably) changed the title of the OP but not the contents. The post now has a SEGFAULT in the title but it is centered in a non-existing compilation error!

you are right in the first paragraph but wrong in the second...i did not change the title but i had both a segfault and an error at that point

now i have a new segfault in SDL_Display format...in the loadImage function...this worked before too :(

here is my new code i have been fiddling with it


[PHP]#include "SDL/SDL.h"
#include <string>
#include "SDL/SDL_image.h"
#include <cstdlib>
#include <ctime>
#include <iostream>
#include "assert.h"

//Constants
const int SCREEN_WIDTH = 630;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;
const int FRAMES_PER_SECOND = 20;

//prototypes
SDL_Surface *loadImage( std::string filename, int Red = 0, int Green = 0, int Blue = 0);
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination);
class Ship;
class Player;
class Timer;
class Missile;

//SDL variables
SDL_Surface *screen = NULL;
SDL_Surface *ship = NULL;
SDL_Event event;
//classes and structs
class Missile
{
    private:
        int x, y;
        int velY;
    public:
        
        bool fired;
        SDL_Surface* bullet; 

        Missile()
        {
            bullet = loadImage("bullet.bmp", 255, 255, 255);
        }

        void fire(int X, int Y)
        {
            x = X;
            y = Y;

            velY = 20;

            bool fired = false;
            
            applySurface(x, y, bullet, screen);
        }

        void move()
        {
            y += velY;
        }
};

class Ship
{
    protected:
      int x, y, velX, velY; 
      Missile *ammo;
    public:
      void show()
      {
        applySurface(x, y, ship, screen);
      }

};
class Player: public Ship
{
    int ammoSlot;
    public:
    Player(int X, int Y, int VelX, int VelY = 0)
    {
        x = X;
        y = Y;
        velX = VelX;
        velY = VelY;
        ammoSlot = 0;

        ammo = new Missile[10];
    }

    void handleInput()
    {            
        Uint8* Keys = SDL_GetKeyState(NULL);

        if(Keys[SDLK_LEFT])
        {
            if (x >= 0)
            {
                x -= velX;
            }
        }

        if(Keys[SDLK_RIGHT])
        {
            if (x <= SCREEN_WIDTH - 70)
            {
                x += velX;
            }
        }

        if(Keys[SDLK_SPACE])
        {
            if(ammo[ammoSlot].fired == false)
            {
                ammo[ammoSlot].fire(x + 35, y);
                ammo[ammoSlot].fired = true;
                ammoSlot++;
            }
        }
    }

    void show()
    {
        applySurface(x, y, ship, screen);
    }

};

class Timer
{
    private:
    //The clock time when the timer started
    int startTicks;
    
    //The ticks stored when the timer was paused
    int pausedTicks;
    
    //The timer status
    bool paused;
    bool started;
    
    public:
    //Initializes variables
    Timer();
    
    //The various clock actions
    void start();
    void stop();
    void pause();
    void unpause();
    
    //Gets the timer's time
    int get_ticks();
    
    //Checks the status of the timer
    bool is_started();
    bool is_paused();    
};
//outside class methods
Timer::Timer()
{
    //Initialize the variables
    startTicks = 0;
    pausedTicks = 0;
    paused = false;
    started = false;    
}

void Timer::start()
{
    //Start the timer
    started = true;
    
    //Unpause the timer
    paused = false;
    
    //Get the current clock time
    startTicks = SDL_GetTicks();    
}

void Timer::stop()
{
    //Stop the timer
    started = false;
    
    //Unpause the timer
    paused = false;    
}

void Timer::pause()
{
    //If the timer is running and isn't already paused
    if( ( started == true ) && ( paused == false ) )
    {
        //Pause the timer
        paused = true;
    
        //Calculate the paused ticks
        pausedTicks = SDL_GetTicks() - startTicks;
    }
}

void Timer::unpause()
{
    //If the timer is paused
    if( paused == true )
    {
        //Unpause the timer
        paused = false;
    
        //Reset the starting ticks
        startTicks = SDL_GetTicks() - pausedTicks;
        
        //Reset the paused ticks
        pausedTicks = 0;
    }
}

int Timer::get_ticks()
{
    //If the timer is running
    if( started == true )
    {
        //If the timer is paused
        if( paused == true )
        {
            //Return the number of ticks when the timer was paused
            return pausedTicks;
        }
        else
        {
            //Return the current time minus the start time
            return SDL_GetTicks() - startTicks;
        }    
    }
    
    //If the timer isn't running
    return 0;    
}

bool Timer::is_started()
{
    return started;    
}

bool Timer::is_paused()
{
    return paused;    
}

class Game
{
         public:
             Game()
                   : player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5)
            {
            }
        Player player;
        Timer fps;
};
//globals

Player player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5);
Timer fps;
//Game game;

//functions

void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination )
{
    //Make a temporary rectangle to hold the offsets
    SDL_Rect offset;
    
    //Give the offsets to the rectangle
    offset.x = x;
    offset.y = y;
    
    //Blit the surface
    SDL_BlitSurface( source, NULL, destination, &offset );
}
SDL_Surface *loadImage( std::string filename, int Red, int Green, int Blue ) 
{ 
    //The image that's loaded 
    SDL_Surface* loadedImage = NULL; 
    
    //The optimized image that will be used 
    SDL_Surface* optimizedImage = NULL; 
    
    //Load the image using SDL_image 
    loadedImage = IMG_Load( filename.c_str() );
       
    //If the image loaded 
    if( loadedImage != NULL ) 
    { //Create an optimized image 
        optimizedImage = SDL_DisplayFormat( loadedImage ); //Free the old image 
        SDL_FreeSurface( loadedImage );
        if( optimizedImage != NULL ) 
        { 
            //Map the color key 
            Uint32 colorkey = SDL_MapRGB( optimizedImage->format, Red, Green, Blue );
            //Set all pixels of color key 
            SDL_SetColorKey( optimizedImage, SDL_SRCCOLORKEY, colorkey ); 
        }     
    } 
    
    //Return the optimized image 
    return optimizedImage; 
}

void debug(std::string message)
{
    std::cout << message << std::endl;
}

int init()
{
    //set up randoms
    srand((unsigned)time(0));

    //initiate SDL
    if( SDL_Init( SDL_INIT_EVERYTHING ) == -1 )
        {
        //something went wrong
            return 1;    
        }
    
    //set up the screen and check it
    screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );
    
    if (screen == NULL)
    {
        return 3;
    }
    SDL_EnableKeyRepeat(1, 10);
    SDL_WM_SetCaption( "Space Shooter", NULL );
    
    //set up image and blit
    ship = loadImage("player.bmp", 255, 255, 255);
    
    applySurface((SCREEN_WIDTH/2),(SCREEN_HEIGHT-75), ship, screen);

    //Update the screen
    if( SDL_Flip( screen ) == -1 )
           { 
        return 4; 
    } 
    return 0;
}

int loop()
{
    bool quit = false;

    while (quit == false)
    {
            fps.start();

            while(SDL_PollEvent(&event))
            {
                if (event.type == SDL_QUIT)
                {
                    quit = true;
                }
            
                //handle player input
                player.handleInput();
            
        
                //Fill the screen white
                SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0, 0, 0 ) );
         
                //Show the dot on the screen 
                player.show(); 
        
                

                //Update the screen 
                if( SDL_Flip( screen ) == -1 ) 
                {     
                     return 2; 
                }     
        
                //Cap the frame rate 
                if( fps.get_ticks() < 1000 / FRAMES_PER_SECOND ) 
                { 
                    SDL_Delay( ( 1000 / FRAMES_PER_SECOND ) - fps.get_ticks() ); 
                }    
        }
    }

    return 0;
}

void close()
{
    //Free the surfaces 
    SDL_FreeSurface(screen);
    SDL_FreeSurface(ship);
    //SDL_FreeSurface(bullet);
    //Quit 
    SDL_Quit(); 
}

int main(int argc, char* args[])
{
    int error;
    error = init();
    if (error == 0)
    {
        loop();
        close();
    }
    return error;
}[/PHP]

---

### Post by stroyan on 2008-11-27
Globals and c++ constructors are your downfall now.
The "Player player" global has a constructor that runs before
main has a chance to call "init".  That means that the constructor for
"Missile" is called.  It calls "loadImage", which calls "IMG_Load" and
"SDL_DisplayFormat".

  All those SDL calls before "SDL_Init" eventually catch up with you.
"SDL_DisplayFormat" is referencing uninitialized data.

  The program starts up successfully if the "Player player" variable
is made local to the "loop" function.  That delays the running of its
constructor code until "loop" is called after "init" is called.

  This trouble with calling global constructors before main is similar
to another more common error.  The order in which c++ constructors is
run is undefined for a particular variable scope.  You can't count on
the order in which constructors for global variables will be called.
(That also applies to the order for constructors of multiple local
variables.)  Many folks unknowingly write code that depends on having
a particular order for the constructors.  And that seems to work for
a while ... until the order changes.

---

### Post by jimi_hendrix on 2008-11-27
stroyan...i actually just realized that 5 minutes ago...but thank you

---

