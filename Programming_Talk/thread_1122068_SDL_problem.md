---
title: "SDL problem"
date: 2009-04-10
forum: Programming Talk
---

### Post by swappo1 on 2009-04-10
Hello,

I am having a stange problem with a collision program.  It is based off of lazyfoo example 17 for collision detection.  I am using a 50x50 pixel block that I move around the screen with arrow keys.  In the center of the screen is a wall.  When the block collides with the wall it stops.  The problem is that on the right and the left side of the wall, the block stops short of the wall with about a 10 pixel gap.  On the top of the wall there is no gap.  If, I scale the block down to 20x20 then there is no gap on all four sides of the wall.  If I run the lazyfoo program with the block scaled up to 50x50, set the screen size to 800x600 and center the wall to reflect the setting in my program, I get the same gap on either side of the wall.  Since this is happening on two different programs, could this have something to do with the dimensions of the block and SDL_Rect?  Any help would be appreciated.  Here is my code.
```
//The headers

#include "SDL/SDL.h"

#include "SDL/SDL_image.h"

#include <string>
#include <iostream>

using namespace std;



//The screen attributes

const int SCREEN_WIDTH = 800;

const int SCREEN_HEIGHT = 600;

const int SCREEN_BPP = 32;



//The frame rate

const int FRAMES_PER_SECOND = 20;



//The dimensions of the dot

const int BLOCK_WIDTH = 50;

const int BLOCK_HEIGHT = 50;



//The surfaces

SDL_Surface *block = NULL;

SDL_Surface *screen = NULL;
SDL_Surface *background = NULL;



//The event structure

SDL_Event event;

SDL_Rect wall;



//The dot that will move around on the screen

class Block

{

    private:

    //The X and Y offsets of the dot

    SDL_Rect box;



    //The velocity of the dot

    int xVel, yVel;



    public:

    //Initializes the variables

    Block();



    //Takes key presses and adjusts the dot's velocity

    void handle_input();



    //Moves the dot

    void move();



    //Shows the dot on the screen

    void show();
    
    void show_background();

};



//The timer

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



SDL_Surface *load_image( string filename )

{

    //The image that's loaded

    SDL_Surface* loadedImage = NULL;



    //The optimized surface that will be used

    SDL_Surface* optimizedImage = NULL;



    //Load the image

    loadedImage = IMG_Load( filename.c_str() );



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

            //map the colorkey to the transparent background of the sprite
        	Uint32 colorkey = SDL_MapRGB(optimizedImage->format, 0, 0, 0xff); 
            
            //Set all colors of the background to be transparent

        	SDL_SetColorKey(optimizedImage, SDL_SRCCOLORKEY, colorkey);

        }

    }



    //Return the optimized surface

    return optimizedImage;

}



void apply_surface( int x, int y, SDL_Surface* source, SDL_Surface* destination)

{

    //Holds offsets

    SDL_Rect offset;



    //Get offsets

    offset.x = x;

    offset.y = y;



    //Blit

    SDL_BlitSurface( source, NULL, destination, &offset );

}

bool check_collision(SDL_Rect A, SDL_Rect B)
{
	//The sides of the rectangle
	int leftA, leftB;
	int rightA, rightB;
	int topA, topB;
	int bottomA, bottomB;
	
	//Calculate the sides of RectA
	leftA = A.x;
	rightA = A.x + A.w;
	topA = A.y;
	bottomA = A.y + A.h;
	
	//Calculate the sides of RectB
	leftB = B.x;
	rightB = B.x + B.w;
	topB = B.y;
	bottomB = B.y + B.h;
	
	//if any of the sides from A are outside B
	if(bottomA <= topB)
	{
		return false;
	}
	if(topA >= bottomB)
	{
		return false;
	}
	if(rightA <= leftB)
	{
		return false;
	}
	if(leftA >= rightB)
	{
		return false;
	}
	
	//If none of the sides of A are outside of B
	return true;
}



bool init()

{

    //Initialize all SDL subsystems

    if( SDL_Init( SDL_INIT_VIDEO ) == -1 )

    {

        return false;

    }



    //Set up the screen

    screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );



    //If there was an error in setting up the screen

    if( screen == NULL )

    {

        return false;

    }



    //Set the window caption

    SDL_WM_SetCaption( "SDL Practice", "SDL Practice" );



    //If everything initialized fine

    return true;

}



bool load_files()

{


    //Load the dot image

    block = load_image( "block4.bmp" );


	//load the background image
	background = load_image("blockbackground.png");


    //If there was a problem in loading the block or background

    if( block == NULL || background == NULL )

    {

        return false;

    }



    //If everything loaded fine

    return true;

}



void clean_up()

{

    //Free the surface

    SDL_FreeSurface(block);
    SDL_FreeSurface(background);



    //Quit SDL

    SDL_Quit();

}



Block::Block()

{

    //Initialize the offsets

    box.x = 0;

    box.y = 0;
    
    box.w = BLOCK_WIDTH;
    box.h = BLOCK_HEIGHT;



    //Initialize the velocity

    xVel = 0;

    yVel = 0;

}



void Block::handle_input()

{

    //If a key was pressed

    if( event.type == SDL_KEYDOWN )

    {

        //Adjust the velocity

        switch( event.key.keysym.sym )

        {

            case SDLK_UP: yVel -= BLOCK_HEIGHT / 2; break;

            case SDLK_DOWN: yVel += BLOCK_HEIGHT / 2; break;

            case SDLK_LEFT: xVel -= BLOCK_WIDTH / 2; break;

            case SDLK_RIGHT: xVel += BLOCK_WIDTH / 2; break;

        }

    }

    //If a key was released

    else if( event.type == SDL_KEYUP )

    {

        //Adjust the velocity

        switch( event.key.keysym.sym )

        {

            case SDLK_UP: yVel += BLOCK_HEIGHT / 2; break;

            case SDLK_DOWN: yVel -= BLOCK_HEIGHT / 2; break;

            case SDLK_LEFT: xVel += BLOCK_WIDTH / 2; break;

            case SDLK_RIGHT: xVel -= BLOCK_WIDTH / 2; break;

        }

    }

}



void Block::move()

{

    //Move the dot left or right

    box.x += xVel;



    //If the dot went too far to the left or right

    if( ( box.x < 0 ) || ( box.x + BLOCK_WIDTH > SCREEN_WIDTH ) || (check_collision(box, wall)))

    {

        //move back

        box.x -= xVel;

    }



    //Move the dot up or down

    box.y += yVel;



    //If the dot went too far up or down

    if( ( box.y < 0 ) || ( box.y + BLOCK_HEIGHT > SCREEN_HEIGHT ) || (check_collision(box, wall)))

    {

        //move back

        box.y -= yVel;

    }

}



void Block::show()

{

    //Show the dot

    apply_surface( box.x, box.y, block, screen );

}


void Block::show_background()
{
	//show the background
	apply_surface(0, 0, background, screen);
}


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



int main( int argc, char* args[] )

{

    //Quit flag

    bool quit = false;



    //The dot that will be used

    Block myBlock;



    //The frame rate regulator

    Timer fps;



    //Initialize

    if( init() == false )

    {

        return 1;

    }



    //Load the files

    if( load_files() == false )

    {

        return 1;

    }

	
	//Set the wall
	wall.x = 380;
	wall.y = 100;
	wall.w = 40;
	wall.h = 400;
	

    //While the user hasn't quit

    while( quit == false )

    {

        //Start the frame timer

        fps.start();



        //While there's events to handle

        while( SDL_PollEvent( &event ) )

        {

            //Handle events for the dot

            myBlock.handle_input();



            //If the user has Xed out the window

            if( event.type == SDL_QUIT || event.key.keysym.sym == SDLK_ESCAPE)

            {

                //Quit the program

                quit = true;

            }

        }



        //Move the dot

        myBlock.move();



        //Fill the screen white

		myBlock.show_background();
		
//		//Fill the screen white

//        SDL_FillRect( screen, &screen->clip_rect, SDL_MapRGB( screen->format, 0xFF, 0xFF, 0xFF ) );



        //Show the wall

        SDL_FillRect( screen, &wall, SDL_MapRGB( screen->format, 0x77, 0x77, 0x77 ) );


        //Show the dot on the screen

        myBlock.show();



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



    //Clean up

    clean_up();



    return 0;

}

```

---

### Post by PC-XT on 2009-05-04
Perhaps in Block::move(), decrease the back up value, or snug the block with a loop instead of jumping back a whole step?```
void Block::move()

{

    //Move the dot left or right

    box.x += xVel;



    //If the dot went too far to the left or right

    while( ( box.x < 0 ) || ( box.x + BLOCK_WIDTH > SCREEN_WIDTH ) || (check_collision(box, wall)))

    {

        //move back

        box.x -= (xVel>0?1:-1);

    }



    //Move the dot up or down

    box.y += yVel;



    //If the dot went too far up or down

    while( ( box.y < 0 ) || ( box.y + BLOCK_HEIGHT > SCREEN_HEIGHT ) || (check_collision(box, wall)))

    {

        //move back

        box.y -= (yVel>0?1:-1);

    }

}
```I changed the move back parts. You do need to be careful not to get the block between a snugged object and the screen boundary, or it will tunnel through the object or try to keep going through the screen, but if you design the layout to avoid close proximity of objects this is not a problem. If it is a problem, you could add checks to avoid this.

---

