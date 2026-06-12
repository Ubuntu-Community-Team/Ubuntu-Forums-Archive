---
title: "forwarding a class in C++"
date: 2008-11-24
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-24
how would i forward a class like a function in C++...like for the function you put the prototype in the top of the code but with a class what do you do?

(yes i asked this in irc last night but i messed up somewhere and do not have chatlogs so here i am again)

---

### Post by StOoZ on 2008-11-24
class name_of_class_to_forward;


its called forward declaration

---

### Post by SledgeHammer_999 on 2008-11-24
or are you asking about class prototyping? (like function prototyping)

---

### Post by monkeyking on 2008-11-24
I don't understand what you want.
Couldn't you just put the class interface in a haederfile and then include this?

If you have problems with multiple includes, then you can use a preprocessor macro

---

### Post by jimi_hendrix on 2008-11-24
example with functions

```
int a();
int b();

int b()
{
return a();
}

int a()
{
return 1;
}

```

---

### Post by iamstrange14 on 2008-11-24
```
class something{
    public:
        int a();
        int b();
};

int main(){
    //use class here
    return 0;
}

int something::a(){
    //code for function a
}
int something::b(){
    //code for function b
}
```

Is that what you were looking for?

---

### Post by jimi_hendrix on 2008-11-24
no...i think the first reply answered it the best

---

### Post by dwhitney67 on 2008-11-25
> **jimi_hendrix said:**
> example with functions

```
int a();
int b();

int b()
{
return a();
}

int a()
{
return 1;
}

```

I do not understand this post; it is not related to class forwarding.  The example above is related to defining (or prototyping) functions, before they are actually implemented.

Class forwarding is something different, but yet conceptually the same.

For example:
[php]
class B;

class A
{
  public:
    A();
  private:
    B* m_bInstance;
};
[/php]
In the example above, the actual definition of class B is not required since I am only declaring a pointer to it; had I declared a reference to class B, the same would also be true.  In essence, I am telling the compiler that there is such a class B, and I will tell the compiler about it at a later time (obviously before run time), within the implementation (.cpp) file for class A.

If I had changed the declaration of m_bInstance to be a regular object (i.e. not a pointer nor a reference), then I would have to declare class B in it's entirety.  Generally class B would be defined in its own header file, and thus this header file would be included in the header file for class A.

P.S.  The whole purpose of class forwarding is to speed up the time it takes to compile files (for very large projects).  For simple projects with one or two modules, class forwarding will not buy much as far as time savings, but the practice of learning how to do it will be beneficial.

---

### Post by dribeas on 2008-11-25
+1 dwhitney

> **dwhitney67 said:**
> In the example above, the actual definition of class B is not required since I am only declaring a pointer to it; had I declared a reference to class B, the same would also be true.  In essence, I am telling the compiler that there is such a class B, and I will tell the compiler about it at a later time (obviously before run time), within the implementation (.cpp) file for class A.

If I had changed the declaration of m_bInstance to be a regular object (i.e. not a pointer nor a reference), then I would have to declare class B in it's entirety.  Generally class B would be defined in its own header file, and thus this header file would be included in the header file for class A.

P.S.  The whole purpose of class forwarding is to speed up the time it takes to compile files (for very large projects).  For simple projects with one or two modules, class forwarding will not buy much as far as time savings, but the practice of learning how to do it will be beneficial.

Class forward declarations can be used with a set of operations: defining a pointer or reference, defining a function that takes or returns an instance of the class, whether it is passed as reference, pointer or by value. Declaring a static variable in a class.

You do need the whole type declaration (not method implementation, but class declaration) whenever you want to declare a member attribute of that type, use any method defined in the class or define an static attribute of that type.

The main use, as dwhitney presented, is what is called compiler firewalls. You do not need to include the header that contains the full definition of the class. This is done for two main reasons: optimizing compilation times and removing source code dependencies.

As an example, consider that many classes must include header a.h that defines class A. Class A uses class B, but only stores pointers/references and uses B internally in its methods. Now, if a.h included b.h as to have a full definition of B when class A is defined, then any change to B (even if it is in a private method) will force you to recompile both A and all other A dependant classes.

If you only forward declare B, then there is no dependency in the code that relates any of the other code to b.h (where B is defined). Users that include a.h won't care the least about how B is defined, when or how it changes.

This is most often used in the PIMPL idiom. Where most of the internals of a class are pushed into an private class. That way the class itself offers just a clean interface with no auxiliar methods, or data that is unrelated to its interactions with other classes. The internal implementation is defined inside the .cpp file. Users of the external class only have the definition of the public interface (or protected if it is designed to be extended).

---

### Post by nvteighen on 2008-11-25
+1 dwhitney67 and +1 dribeas (= +2 :))

Hmm... "forwarding" is a concept derived from C where you can just tell the compiler that there's some **struct** named "whatever" without specifiying what's inside. So you get the first step towards OOP in C, because you get module-wise encapsulation.

As C structs were superseeded in C++ by classes, this works the same...

As dribeas said, this is called in the C++ world in the PIMPL (?) idiom and in the C world, "Opaque Pointer Technique", as any access will be done through a pointer (Have you ever done GTK+ in C?).

---

### Post by jimi_hendrix on 2008-11-25
ok apparently my class forwarding is messing up... heres the code

[PHP]#include "SDL/SDL.h"
#include <string>
#include "SDL/SDL_image.h"
//Constants
const int SCREEN_WIDTH = 630;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;
const int FRAMES_PER_SECOND = 20;
//prototypes
SDL_Surface *loadImage( std::string filename );
void applySurface( int x, int y, SDL_Surface* source, SDL_Surface* destination, int Red = 0, int Green = 0, int Blue = 0);
class Ship;
class Player;
class Timer;
class Missle;
//SDL variables
SDL_Surface *screen = NULL;
SDL_Surface *ship = NULL;
SDL_Surface *bullet = NULL;
SDL_Event event;
//globals
Player player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5);
Timer fps;
Missile ammo[21];

//classes
class Ship
{
    protected:
      int x, y, velX, velY;
    public:
      void show()
      {
        applySurface(x, y, ship, screen);
      }

};
class Player: public Ship
{
    public:
    Player(int X, int Y, int VelX, int VelY = 0)
    {
        x = X;
        y = Y;
        velX = VelX;
        velY = VelY;
    }

    void handleInput()
    {            
        //get the keystate and begin checking for keydowns
//getKeystate:
        Uint8* Keys = SDL_GetKeyState(NULL);

        if(Keys[SDLK_LEFT])
        {
            x -= velX;
//            goto getKeystate;
        }

        if(Keys[SDLK_RIGHT])
        {
            x += velX;
//            goto getKeystate;
        }

        if(Keys[SDLK_SPACE])
        {
            ammo[ammoSlot].fire((this->x + 32), this->y);
        }
    }

    void show()
    {
        applySurface(x, y, ship, screen);
    }

};

class Missile
{
    private:
        int x, y, velY = 20;
        bool fired;
    public:
        void fire(int X, int Y)
        {
            x = X;
            y = Y;

            bool fired = true;
            
            applySurface(x, y, bullet, screen);
        }

        void move()
        {
            y += velY;
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
//functions
SDL_Surface *loadImage( std::string filename ) 
{
    //The image that's loaded
    SDL_Surface* loadedImage = NULL;
    
    //The optimized image that will be used
    SDL_Surface* optimizedImage = NULL;
    
    //Load the image
    loadedImage = IMG_Load( filename.c_str() );
    
    //If the image loaded
    if( loadedImage != NULL )
    {
        //Create an optimized image
        optimizedImage = SDL_DisplayFormat( loadedImage );
        
        //Free the old image
        SDL_FreeSurface( loadedImage );
        
        //If the image was optimized just fine
        if( optimizedImage != NULL )
        {
            //Map the color key
            Uint32 colorkey = SDL_MapRGB( optimizedImage->format, 0, 0, 0 );
            
            //Set all pixels of color R 0, G 0xFF, B 0xFF to be transparent
            SDL_SetColorKey( optimizedImage, SDL_SRCCOLORKEY, colorkey );
        }
    }
    
    //Return the optimized image
    return optimizedImage;
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
SDL_Surface *loadImage( std::string filename, int Red = 0, int Green = 0, int Blue = 0 ) 
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
        return 1;
    }

    SDL_WM_SetCaption( "Hello World", NULL );
    
    //set up image and blit
    ship = loadImage("player.bmp", 255, 255, 255);
    bullet = loadImage("bullet.bmp", 255, 255, 255);

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
}[/PHP]

heres the errors

```
g++ -o test shooter.cpp -lSDL -lSDL_image
shooter.cpp:22: error: variable 'Player player' has initializer but incomplete type
shooter.cpp:23: error: aggregate 'Timer fps' has incomplete type and cannot be defined
shooter.cpp:24: error: 'Missile' does not name a type
shooter.cpp: In member function 'void Player::handleInput()':
shooter.cpp:70: error: 'ammo' was not declared in this scope
shooter.cpp: At global scope:
shooter.cpp:84: error: ISO C++ forbids initialization of member 'velY'
shooter.cpp:84: error: making 'velY' static
shooter.cpp:84: error: ISO C++ forbids in-class initialization of non-const static member 'velY'
shooter.cpp: In function 'int init()':
shooter.cpp:323: error: call of overloaded 'applySurface(int, int, SDL_Surface*&, SDL_Surface*&)' is ambiguous
shooter.cpp:11: note: candidates are: void applySurface(int, int, SDL_Surface*, SDL_Surface*, int, int, int)
shooter.cpp:259: note:                 void applySurface(int, int, SDL_Surface*, SDL_Surface*)
make: *** [all] Error 1

```

---

### Post by dwhitney67 on 2008-11-25
When you instantiate an object, you need to define that object (i.e. give the compiler a clue how big that object is).  A forward declaration will *not* do this for you.

Thus, these three statements will not be satisfied until you precede them with the class definitions that define the objects:
[php]
...
Player player((SCREEN_WIDTH/2), (SCREEN_HEIGHT - 75), 5);
Timer fps;
Missile ammo[21];
...
[/php]
As for the forward declaration for "class Ship", this is not needed because a few lines down you define the object.

P.S.  Not that it really matters, but the forward declaration for Missile is misspelled.

P.S.S.  You are writing code in C++, right?  There is absolutely no need for global variables.  Declare your Player, Timer, and Missile objects in your main function, then pass these objects around as needed.

---

### Post by jimi_hendrix on 2008-11-25
uhhh they are defined in my code?

---

### Post by dwhitney67 on 2008-11-25
> **jimi_hendrix said:**
> uhhh they are defined in my code?

Perhaps my reply was not clear; thus I edited it.  Before an object can be instantiated, the object definition must *precede* the location where the instantiation takes place.

So this is ok:
[php]
class Foo
{
  ...
};

Foo foo[3];
[/php]

This is *not* ok:
[php]
class Foo;

Foo foo[3];

class Foo
{
  ...
};
[/php]

Also, like I stated in my previous post, global variables should not be needed in C++.  I would suggest that you don't bring your bad C habits to C++.

---

### Post by jimi_hendrix on 2008-11-25
im just using globals for the player timer and an array of enemies...(i got rid of ammo) this is so they can be accessed from the three main methods...without a bunch of parameters

---

### Post by dwhitney67 on 2008-11-25
If your methods are related, encapsulate them and your Player and Enemy objects within a class.

---

### Post by jimi_hendrix on 2008-11-25
what are these errors

```
shooter.cpp:79: error: ISO C++ forbids initialization of member 'velY'
shooter.cpp:79: error: making 'velY' static
shooter.cpp:79: error: ISO C++ forbids in-class initialization of non-const static member 'velY'

```

---

### Post by dwhitney67 on 2008-11-25
In your Missile class, the initialization of velY as you have it below is not permissible for non-static variables.  You need to initialize velY in your class constructor.
[php]
class Missile
{
...
        int x, y, velY = 20;
...
};
[/php]

---

### Post by jimi_hendrix on 2008-11-25
ok thanks

errors should be less criptic

---

