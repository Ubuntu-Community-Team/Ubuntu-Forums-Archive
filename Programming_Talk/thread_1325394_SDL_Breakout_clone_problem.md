---
title: "SDL Breakout clone problem"
date: 2009-11-13
forum: Programming Talk
---

### Post by matmatmat on 2009-11-13
I have a problem with my berakout clone, I want to change the image file and make it drop down for power-ups (like lbreakout2):
```

//header
class Block {
protected:
    int points;
public:
    std::string name;
    int x, y;
    int yVel;
    SDL_Surface *image;
    Block();
    Block(int ux, int uy, int upoints, SDL_Surface *uimage);
    void move();
    void show(SDL_Surface* screen);
};

//c++ file
#include "block_classes.h"
#include "sdl_functions.h"
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <string>

//Initialize the variables
Block::Block(int ux, int uy, int upoints, SDL_Surface *uimage) {
    x = ux;
    y = uy;
    points = upoints;
    yVel = 0;
    image = uimage;
    yVel = 0;
    name = "NULL";
}

Block::Block(){}

void Block::move(){
    y += yVel;
}

void Block::show(SDL_Surface* screen) {
    apply_surface(x, y, image, screen, NULL);
}

Paddle::Paddle(int ux, int uy, SDL_Surface *uimage, int uimage_height){
    x = ux;
    y = uy;
    image = uimage;
}

void Paddle::move(int ux){
    x = ux;
}

void Paddle::show(SDL_Surface *screen){
    apply_surface(x,y,image,screen,NULL);
}

Ball::Ball(int ux, int uy, int uh, int uw, SDL_Surface *uimage){
    x = ux;
    y = uy;
    h = uh;
    w = uw;
    image = uimage;
    xdirection = 1;
    ydirection = -1;
    xVel = 10;
    yVel = 10;
}

void Ball::move(int sHeight, int sWidth){
    if (x <= 0){
        xdirection = 1;
    }else if (x >= sWidth - 20){
        xdirection = -1;
    }

    if (y <= 0){
        ydirection = 1;
        yVel += xVel += rand()%2 + 1;
        if (xdirection == 1){
            xdirection = -1;
        }else if (xdirection == -1){
            xdirection = 1;
        }
    }else if (y >= sHeight){
        std::cout << "You lose!\n";
        exit(1);
    }

    x += (xVel * xdirection);
    y += (yVel * ydirection);
}

void Ball::show(SDL_Surface* screen) {
    apply_surface(x, y, image, screen, NULL);
}

bool Ball::check_for_collision(SDL_Rect B, int xdir, int ydir){
    SDL_Rect A;
    A.x = x;
    A.y = y;
    A.w = w;
    A.h = h;

    //The sides of the rectangles
    int leftA, leftB;
    int rightA, rightB;
    int topA, topB;
    int bottomA, bottomB;

    //Calculate the sides of rect A
    leftA = A.x;
    rightA = A.x + A.w;
    topA = A.y;
    bottomA = A.y + A.h;

    //Calculate the sides of rect B
    leftB = B.x;
    rightB = B.x + B.w;
    topB = B.y;
    bottomB = B.y + B.h;

    //If any of the sides from A are outside of B
    if( bottomA <= topB )
    {
        return false;
    }

    if( topA >= bottomB )
    {
        return false;
    }

    if( rightA <= leftB )
    {
        return false;
    }

    if( leftA >= rightB )
    {
        return false;
    }

    //If none of the sides from A are outside B
    if (xdir != 10 && ydir != 10){
        xdirection = xdir;
        ydirection = ydir;
        yVel = xVel = 10;
    }
    return true;
}

```

```

#include <iostream>
#include <fstream>
#include <string.h>
#include <vector>
#include <stdio.h>
#include <stdlib.h>
#include <string>
#include <time.h>
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "block_classes.h"
#include "sdl_functions.h"
using namespace std;

//surfaces
SDL_Surface *screen    = NULL;
SDL_Surface *irblock   = NULL;
SDL_Surface *igblock   = NULL;
SDL_Surface *ibblock   = NULL;
SDL_Surface *ipaddle   = NULL;
SDL_Surface *iball     = NULL;
SDL_Surface *ifspecial = NULL;

//Screen attributes
const int SCREEN_WIDTH = 480;
const int SCREEN_HEIGHT = 605;
const int SCREEN_BPP = 32;

//Blocks attributes
const int BLOCK_WIDTH = 55;
const int BLOCK_HEIGHT = 15;

//Paddle attributes
int PADDLE_HEIGHT = 16;
int PADDLE_WIDTH = 64;

//The frame rate
const int FRAMES_PER_SECOND = 30;

//event
SDL_Event event;

bool init() {
    srand(time(NULL));
    if (SDL_Init(SDL_INIT_EVERYTHING) == -1) {
        return false;
    }

    screen = SDL_SetVideoMode(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP,
            SDL_SWSURFACE);

    if (screen == NULL) {
        return false;
    }

    SDL_WM_SetCaption("Breakout", NULL);

    return true;
}

bool load_files() {
    irblock = load_image("data/rblock.png");
    if (irblock == NULL) {
        return false;
    }

    igblock = load_image("data/gblock.png");
    if (igblock == NULL) {
        return false;
    }

    ibblock = load_image("data/bblock.png");
    if (ibblock == NULL) {
        return false;
    }

    ipaddle = load_image("data/bat.png");
    if (ipaddle == NULL){
        return false;
    }

    iball = load_image("data/ball.png");
    if (iball == NULL){
        return false;
    }

    ifspecial = load_image("data/fspecial.png");
    if (ifspecial == NULL){
        return false;
    }

    return true;
}

void clean_up() {
    SDL_FreeSurface(irblock);
    SDL_FreeSurface(igblock);
    SDL_FreeSurface(ibblock);
    SDL_FreeSurface(ipaddle);
    SDL_FreeSurface(iball);
    SDL_Quit();
}

int main(int argc, char **argv) {
    int x = 0, y = 0, i = 0, i2 = 0, mousex, mousey;
    int numofblocks = 0;
    char block_map[300];
    if (argc == 2) {
        read_map_from_file(block_map, argv[1]);
    } else {
        strcpy(block_map, "rrrrrrrrrrrrrrrrrrrr");
    }
    for (i2 = 0; block_map[i] != '\0'; i++) {
        numofblocks++;
    }

    //Initialize
    if (init() == false) {
        return -1;
    }
    if (load_files() == false) {
        return -1;
    }

    std::vector<Block*> blocks;
    std::vector<Block*>::iterator it;
    i = 0;
    for (y = 0; y <= SCREEN_HEIGHT; y += BLOCK_HEIGHT) {
        for (x = 0; x <= SCREEN_WIDTH; x += BLOCK_WIDTH) {
            if (i <= numofblocks) {
                blocks.push_back(new Block(x, y, 10, irblock));
                i++;
            }
        }
    }
    bool quit = false;
    Timer fps;

    //block for 'for' loop
    Block block;

    Ball ball(300, 550, 20, 20, iball);

    SDL_Rect rect;

    bool collision;

    //bat
    Paddle bat((SCREEN_WIDTH - PADDLE_WIDTH)/2, SCREEN_HEIGHT - PADDLE_HEIGHT, ipaddle, PADDLE_HEIGHT);


    while (quit == false) {
        //Start the frame timer
        fps.start();

        //While there's events to handle
        while (SDL_PollEvent(&event)) {

            //If the user has Xed out the window
            if (event.type == SDL_QUIT) {
                //Quit the program
                quit = true;
            }
        }

        //Fill the screen white
        SDL_FillRect(screen, &screen->clip_rect, SDL_MapRGB(screen->format,
                0xFF, 0xFF, 0xFF));

        if (blocks.size() == 0){
            cout << "well done, you won!\n";
            break;
        }

        for (i = 0; i < blocks.size(); i++) {
            block = *blocks.at(i);
            block.move();
            block.show(screen);
            rect.x = block.x;
            rect.y = block.y;
            rect.h = BLOCK_HEIGHT;
            rect.w = BLOCK_WIDTH;
            collision = ball.check_for_collision(rect,10,10);
[b]            if (collision == true && block.name == "NULL" && block.yVel  != 5){
                if (rand()%2 == 0){
                    if (rand()%3 == 0){
                        string a = "fs";
                        block.name = a;
                        block.image = ifspecial;
                        block.yVel = 5;
                        block.show(screen);
                        break;
                    }
                }else if (block.name == "NULL"){
                    blocks.erase(blocks.begin()+i, blocks.begin()+i+1);
                }
            }[/b]
        }

        SDL_GetMouseState(&mousex, &mousey);
        bat.move(mousex-(PADDLE_WIDTH/2));
        bat.show(screen);

        ball.move(SCREEN_HEIGHT, SCREEN_WIDTH);
        ball.show(screen);
        rect.x = bat.x;
        rect.y = bat.y;
        rect.h = PADDLE_HEIGHT;

        //1st half of bat
        rect.w = PADDLE_WIDTH/2;
        ball.check_for_collision(rect, -1, -1);

        //2nd half of bat
        rect.x += PADDLE_WIDTH/2;
        ball.check_for_collision(rect, 1, -1);


        //Update the screen
        if (SDL_Flip(screen) == -1) {
            return -1;
        }

        //Cap the frame rate
        if (fps.get_ticks() < 1000 / FRAMES_PER_SECOND) {
            SDL_Delay((1000 / FRAMES_PER_SECOND) - fps.get_ticks());
        }
    }

    //Clean up
    clean_up();
    return 1;
}

```
as soon as the image is changed the object is deleted, I think it is something to do with the else if, but not sure, please help

---

### Post by dwhitney67 on 2009-11-13
For starters, fix your Block constructors.  Both constructors need to initialize the class' member data in the initialization area, and in the proper order in which the member data is declared.

You are only initializing the class' member data in the constructor that accepts parameters.

The 'initialization area' of a constructor is as follows:
```

class SomeClass
{
public:
   SomeClass(type1 d1, type2 d2);
   SomeClass();
private:
   type1 data1;
   type2 data2;
};

SomeClass::SomeClass(type1 d1, type2 d2)
 : data1(p1),
   data2(p2)
{
   // this is not the initialization area!
}

SomeClass::SomeClass()
: data1(someDefaultValue),
  data2(someDefaultValue)
{
   // this is not the initialization area!
}

```
I do not know from your code if by chance, you are calling the Block default constructor.  If so, the 'name' member data field is uninitialized; thus instead of being "NULL", it is merely "".

---

### Post by unknownPoster on 2009-11-14
I believe there are a few memory leaks in your code as well. Every SDL_Surface needs to be freed at some point, including the screen and "image" within your Block class.

---

