---
title: "Classes (C/C++) and transferring information."
date: 2011-08-10
forum: Programming Talk
---

### Post by Ravenshade on 2011-08-10
I've got myself into a pickle which I could probably do a better way...here's the story. 

I've declared a class, given it some information. For the moment I'm treating it quite simply. I've already defined the class and the constructor elsewhere, and I shan't bore you with the details. 

[PHP]
MyClass Crown;
Crown.jewels = 1;
Crown.metals = 2;
Crown.identification = 001;

[/PHP]

Now I'm trying to figure out how to make my next bit of code scalable, but it's proving tricky. 

I have this line more or less

[PHP]
Crown.get_something(blah, blah)
[/PHP]

Now that's not very scalable, in fact it is quite limiting. Instead I want replace Crown with something like 

[PHP]get_helmet().get_something(blah, blah)[/PHP] with get_helmet doing...

[PHP]get_hemet()
{
    return Helmet that we're current wearing.
}[/PHP]

Thereby earlier in the program I could set a variable that indicates which helmet we're wearing and where to get the information from... 

:-& I think I'm looking for encapsulation... 

Does anyone have any idea?

---

### Post by cgroza on 2011-08-10
I think a little  more of context and a small piece of code showing your problem will not harm anybody and help us giving better advice.

So far, it seems that a class hierarchy, pointers and polymorphism will do the trick.

---

### Post by karlson on 2011-08-10
> **Ravenshade said:**
> 
[PHP]get_helmet().get_something(blah, blah)[/PHP] with get_helmet doing...

[PHP]get_hemet()
{
    return Helmet that we're current wearing.
}[/PHP]

Thereby earlier in the program I could set a variable that indicates which helmet we're wearing and where to get the information from... 

:-& I think I'm looking for encapsulation... 

Does anyone have any idea?

First off what language you are using?

I mean if you need to get this as a get_helmet()....

You need might consider doing something like this:
```

class HeadGear
{
....
    virtual <type> get_something() = 0;
}

class Wearer
{
...
    HeadGear &get_helmet();
}

```

The class inherits from HeadGear, and get_helmet() returns you a reference to the object currently occupying the appropriate value.

---

### Post by Ravenshade on 2011-08-10
(updated the code) 11AUG11(15:00BST(GMT))

Poly... (should have really paid more attention back in class) uhmm... I was hoping that I wouldn't bore but alas. 

I'm doing this bit so that I can work on basically a containment area so that my little movable ball can't go where I don't want him to. 

Anyway...

...loading...

Done. I think that's all that's needed on this one. I had looked into something along these lines
[PHP]Region aria;
void get_name( Region *aria )

get_name( &aria );[/PHP]

However it didn't yield the result I was expecting as it is almost the opposite >.<
region.h
[PHP]#ifndef REGION_H_INCLUDED
#define REGION_H_INCLUDED

#include "SDL/SDL.h"
#include "image_handler.h"
void aria_layer_1(short map_id,
                int map_h, int map_w,
                short border_l, short border_t,
                SDL_Surface *source, SDL_Surface *destination);

class Region
{
    private:
        short map_id;
        int border_left;
        int border_top;
        int maproom_height;
        int maproom_width;

        void layer1( short map_id = 0,
                int map_h = 0,  int map_w = 0,
                short border_l = 0, short border_t = 0,
                SDL_Surface *source = NULL, SDL_Surface *destination = NULL)
        {
            //declare loop
            if(map_id == 1)
            {
                aria_layer_1(map_id, map_h, map_w,
                border_l, border_t,
                source, destination);
            }
        }

        void layer2(short map_id = 0,
                int map_h = 0, int map_w = 0,
                short border_l = 0, short border_t = 0,
                SDL_Surface *source = NULL, SDL_Surface *destination = NULL )
        { //Nothing here yet

        }
    public:


        void set_map_id(short id_holder);
        void set_border_left(int left_holder);
        void set_border_top(int top_holder);
        void set_maproom_height(int height_holder);
        void set_maproom_width(int width_holder);

        void get_map(
                    SDL_Surface *getSource = NULL,
                    SDL_Surface *getDestination = NULL);
};


#endif // REGION_H_INCLUDED
[/PHP]

region.cpp
[PHP]#include "region.h"
#include "SDL/SDL.h"

void Region::set_map_id(short id_holder)
{
    map_id = id_holder;
}
void Region::set_border_left(int left_holder)
{
    border_left = left_holder;
}

void Region::set_border_top(int top_holder)
{
    border_top = top_holder;
}

void Region::set_maproom_height(int height_holder)
{
    maproom_height = height_holder;
}
void Region::set_maproom_width(int width_holder)
{
    maproom_width = width_holder;
}

void Region::get_map(SDL_Surface *get_source, SDL_Surface *get_destination)
{
    layer1( map_id,
            maproom_height, maproom_width,
            border_left, border_top,
            get_source, get_destination);

    layer2( map_id,
            maproom_height, maproom_width,
            border_left, border_top,
            get_source, get_destination);
}
[/PHP]


main
[PHP]/*KChildheart 2011 All rights reserved
 * This is an extension of sdl_game_kai
 *  Changes: This program gets a sprite set,
 *              and allows the user to move it.
 */


#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif
#ifdef __APPLE__
#include <SDL/SDL.h>
#else
#include <SDL.h>
#endif
#include "string"
#include "image_handler.h"

//get the map definitions
#include "region.h"

//Declare important globals
SDL_Surface *world = NULL;
SDL_Surface *character = NULL;

SDL_Surface *display = NULL;


//Inform the program that other functions
//are available to use.
bool init();
bool load_files();

int handle_character(
                     short direction = -1,
                     int loc_x = 0, int loc_y = 0,
                     SDL_Surface *source = NULL, SDL_Surface *destination = NULL);



//Start the functions
void clean_up();

//Function to display the map
int main ( int argc, char** argv )
{

    //initialise the SDL and the screens
    if (init() == false)
    {
        //ERROR CODE:1
        //Init failed
        return 1;
    }

    if(load_files() == false)
    {
        return 2;
    }

    //Declare Aria
    Region aria;
    //aria.define_region = (1, 4, 3, 10, 10);
    aria.set_map_id(1);
    aria.set_border_left(4);
    aria.set_border_top(3);
    aria.set_maproom_height(10);
    aria.set_maproom_width(10);



    //flip



    bool quit = false; //declare the main loop sequence.

    aria.get_map(world, display);
    //declare starting location in aria

    int region_start_x = 7*32;
    int region_start_y = 5*32;
    //don't wait, just display the character.
    const short down = 0;
    const short up = 3;
    const short right = 2;
    const short left = 1;

    //init the character as not doing anything in its
    //start location


    //this should always be true

        handle_character(4, (region_start_x), (region_start_y), character, display);



    if(SDL_Flip(display) == -1)
    {
        return false;
    }

    //declare directions



    while(quit == false)
    {



        SDL_Event event;
        while( SDL_PollEvent(&event))
        {

            //else handle character
            if(event.type == SDL_KEYDOWN)
            {
                //which key? Do something


                switch(event.key.keysym.sym)
                {
                    case SDLK_UP:
                        aria.get_map(world, display);
                        region_start_y = handle_character(up, (region_start_x ), (region_start_y ), character, display);


                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_DOWN:
                        aria.get_map(world, display);
                        region_start_y = handle_character(down, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_RIGHT:
                        aria.get_map(world, display);
                        region_start_x = handle_character(right, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_LEFT:
                        aria.get_map(world, display);
                        region_start_x = handle_character(left, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    default:
                        aria.get_map(world, display);
                        handle_character(4, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }

                        break;

                }


            }

            if(event.type == SDL_QUIT)
            {
                quit = true;
            }
            if(SDL_Flip(character) == -1)
        {
                return 3;
        }



        }


    }

    clean_up();
    //apply the map
    return 0;
}

[/PHP]


-----------

Edit. 

-----------

Ah thank you very much for that. I shall take a look into virtual types. I'm using C++ but... I'm being a accused of C >.< so I put both in just to appease.

If I don't stop pressing ctrl s in a minute I'm throwing the keyboard.

---

### Post by karlson on 2011-08-10
> **Ravenshade said:**
> 
```
/*KChildheart 2011 All rights reserved
 * This is an extension of sdl_game_kai
 *  Changes: This program gets a sprite set,
 *              and allows the user to move it.
 */


#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif
#ifdef __APPLE__
#include <SDL/SDL.h>
#else
#include <SDL.h>
#endif
#include "string"
#include "image_handler.h"

//get the map definitions
#include "region.h"

//Declare important globals
SDL_Surface *world = NULL;
SDL_Surface *character = NULL;

SDL_Surface *display = NULL;


//Inform the program that other functions
//are available to use.
bool init();
bool load_files();

int handle_character(
                     short direction = -1,
                     int loc_x = 0, int loc_y = 0,
                     SDL_Surface *source = NULL, SDL_Surface *destination = NULL);

void create_region()
{

}


//Start the functions
void clean_up();

//Function to display the map
int main ( int argc, char** argv )
{

    //initialise the SDL and the screens
    if (init() == false)
    {
        //ERROR CODE:1
        //Init failed
        return 1;
    }

    if(load_files() == false)
    {
        return 2;
    }

    //Declare Aria
    Region aria;
    aria.map_id = 1;
    aria.maproom_height = 10;
    aria.maproom_width = 10;
    aria.border_left = 4;
    aria.border_top = 3;



    //flip



    bool quit = false; //declare the main loop sequence.

///It's this thing I'd like to change!
    aria.get_map(world, display); //to...
//  get_region().get_map(world, display);




    //declare starting location in aria

    int region_start_x = 7*32;
    int region_start_y = 5*32;
    //don't wait, just display the character.
    const short down = 0;
    const short up = 3;
    const short right = 2;
    const short left = 1;

    //init the character as not doing anything in its
    //start location


    //this should always be true

        handle_character(4, (region_start_x), (region_start_y), character, display);



    if(SDL_Flip(display) == -1)
    {
        return false;
    }

    //declare directions



    while(quit == false)
    {



        SDL_Event event;
        while( SDL_PollEvent(&event))
        {

            //else handle character
            if(event.type == SDL_KEYDOWN)
            {
                //which key? Do something


                switch(event.key.keysym.sym)
                {
                    case SDLK_UP:
                        aria.get_map(world, display);
                        region_start_y = handle_character(up, (region_start_x ), (region_start_y ), character, display);


                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_DOWN:
                        aria.get_map(world, display);
                        region_start_y = handle_character(down, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_RIGHT:
                        aria.get_map(world, display);
                        region_start_x = handle_character(right, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    case SDLK_LEFT:
                        aria.get_map(world, display);
                        region_start_x = handle_character(left, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }
                        break;
                    default:
                        aria.get_map(world, display);
                        handle_character(4, (region_start_x ), (region_start_y ), character, display);
                        if(SDL_Flip(display) == -1)
                        {
                            return false;
                        }

                        break;

                }


            }

            if(event.type == SDL_QUIT)
            {
                quit = true;
            }
            if(SDL_Flip(character) == -1)
        {
                return 3;
        }



        }


    }

    clean_up();
    //apply the map
    return 0;
}

```


-----------

Edit. 

-----------

Ah thank you very much for that. I shall take a look into virtual types. I'm using C++ but... I'm being a accused of C >.< so I put both in just to appease.

If I don't stop pressing ctrl s in a minute I'm throwing the keyboard.

Not to be a smart... but from reading your code I think you should invest into the following

[http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=sr_1_1?ie=UTF8&qid=1313032574&sr=8-1](http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=sr_1_1?ie=UTF8&qid=1313032574&sr=8-1)
[http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=sr_1_3?ie=UTF8&qid=1313032574&sr=8-3](http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=sr_1_3?ie=UTF8&qid=1313032574&sr=8-3)
[http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/ref=sr_1_1?s=books&ie=UTF8&qid=1313032702&sr=1-1](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/ref=sr_1_1?s=books&ie=UTF8&qid=1313032702&sr=1-1)

Your code really does look like C instead of C++ as normally if you want to set parameters in the object it normally is done by passing them to the constructor and make the parameters private rather then public and the interface you expose  should be functions rather then parameters as you have.

I think you should rethink the design and more importantly the objects.

Namely you have several objects to think about:

1.  Character.  Think of what properties you have for the character and what you need to be able to read.
2.  Map cells.  Think of what properties you have for the cell think of what you need to get or set.
3.  Full map. 

This will give you a good start of how to design your objects and will give you a clearer ability to define relationship between objects.

---

### Post by Ravenshade on 2011-08-11
If I see them in the library I'll be sure to pick them up. Not all of us have cash flowing out of our ears. However, do you think passing the parameters through the constructor will solve the problem at hand?

Edit, 

I have no clue whether it is c or not, as I've mentioned before, I'm using LazyFoo's SDL tutorial and [http://www.learncpp.com/](http://www.learncpp.com/) , both of which are telling me this is the way to code c++

---

### Post by dwhitney67 on 2011-08-11
> **Ravenshade said:**
>  
I have no clue whether it is c or not, as I've mentioned before, I'm using LazyFoo's SDL tutorial and [http://www.learncpp.com/](http://www.learncpp.com/) , both of which are telling me this is the way to code c++

Here's perhaps a better C++ Tutorial:  [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

The key word that you are missing from your programming repertoire is "encapsulation".

A Game contains a Board/Map/Region, a Player/Person (or more), and an Engine that dictates what can transpire between the Player's and the Board.

I'm not a game developer, so I may have missed some other attributes that can be associated with a game or perhaps used the wrong nomenclature, but the point I'm trying to make is that you need to start thinking in term of "objects" -- that is, if you want to be successful in C++, Java, or any other popular OOP language.

Terms that you should become familiar with when thinking of objects are:  "is-a", "has-a", "uses".

The "is-a" term implies that an object is derived, and is a type of a super-object.  For example, a Triangle, Circle, and Rectangle all share an "is-a" relationship with a Shape object.  A Square is-a Rectangle (the converse is not true).

A Shape may have attributes associated with it; these are the "has-a" relationships.  For example, a Point on the screen, which is represented by X and Y coordinates (perhaps even a Z coordinate).  Another attribute could be Color.  Each of these objects have no direct relationship to Shape, but are attributes of the Shape itself.

A "uses" relationship could be something like rotating a Shape using some Render Algorithm defined elsewhere.  This algorithm is not an attribute of the Shape, but is merely used by the Shape or by some other object that manages the Shape itself.

---

### Post by Ravenshade on 2011-08-11
Ah yes you are quite right, I'm still trying to get into the swing of that. Albeit...defining those parameters through a function is decidedly tricky, I keep getting a "perhaps you forgot the &" but I haven't used any pointers... (I'm just missing something obvious...like a brain perhaps).

Thanks for your help and I'll try to read more into encapsulation. 

Although original problem still stands.

---

### Post by karlson on 2011-08-11
> **Ravenshade said:**
> Ah yes you are quite right, I'm still trying to get into the swing of that. Albeit...defining those parameters through a function is decidedly tricky, I keep getting a "perhaps you forgot the &" but I haven't used any pointers... (I'm just missing something obvious...like a brain perhaps).

Thanks for your help and I'll try to read more into encapsulation. 

Although original problem still stands.

When you move from C to C++ or any other Object Oriented language you should change the way you think somewhat for example setting the parameter through a function is not tricky.
```

class test
{
private:
     int test_param;
public:
     void set_test_params(int value)
     {
         test_param = value; 
     }
};

test test_obj;
test_obj.set_test_params(1);

```

Also when someone mentions "perhaps you forgot a &" that doesn't mean a pointer although it could but normally it means that you pass the object by value rather then by reference.  This means that you are not passing a copy of an object to the function.

As far as encapsulation is concerned you should look at what individual subjects you have in the game.  That will give you the way to encapsulate...

---

### Post by Ravenshade on 2011-08-11
Hm, I did as you suggested but the problem stems from me trying to do multiple things at the same time. I.e shorten my code. 

reminder... 

my original problem is with aria.get_map(world, display) and I'd like to be able to 'change' the first part of that so basically...

get_class_name().get_map(world, display)

strangely, everyone is going after my encapsulation, which I'm working on. You guys should have seen the first release, I wasn't even using header files! (This is the first class I've used in this program). 

That being said what I was trying to do was..

//won't someone please install a c++ version of this php tag? >.<
[PHP]
class test
{
private:
     int test_param;
     int test_param2;
     int test_param3;
public:
     void set_test_params(int x, int y, int z)
     {
         test_param = x; 
         test_param2 = y;
         test_param3 = z;
     }
};

test test_obj;
test_obj.set_test_params(10, 9, 8);
[/PHP]

That's when I get the & issue. Just declaring the one variable is fine but... I don't see why I should write extra code...just for the sake of writing code, where I'm basically writing 3 sets of set_test_param just to get each variable.

That being said, I need the practice, so I've gone ahead and done it >.<;

edit

I only have one thing really to encapsulate at he moment and that is the regions. 

Aria is a Region

---

### Post by Ravenshade on 2011-08-11
Okay I think I have a solution to my own problem. Since no one else is helping...  and that is to make class Region belong to class Zone

and then return the variable ... *brain spasm* 

I think I might be along the right tracks, but I don't have the techie know how yet. 

That being said. I have however solved my ulterior motive for this thread and that was for my limitations. So yeah.

---

### Post by dwhitney67 on 2011-08-11
> **Ravenshade said:**
> 
reminder... 

my original problem is with aria.get_map(world, display) and I'd like to be able to 'change' the first part of that so basically...

get_class_name().get_map(world, display)


I cannot provide you with a direct answer, because a) I'm not privy to knowing your s/w design, and b) from what you have posted, it seems that a lot of re-factoring is in order.

However, to show you an example of encapsulation and of chaining method calls together, I threw this silly program together (beware it is lacking error checking):
```

#include <map>
#include <string>
#include <iostream>

// abstract class (cannot be instantiated)
class Helmet
{
public:
   virtual std::string getType() = 0;
};

// specific class; implements Helmet
class Crown : public Helmet
{
public:
   std::string getType() { return "Crown"; }
};

// specific class; implements Helmet
class PaperHat : public Helmet
{
public:
   std::string getType() { return "Paper Hat"; }
};

// Player class; player has-a Helmet.
class Player
{
public:
   enum Role { GRUNT, WELL_TO_DO, MAGISTRATE, GOVERNOR, KING };

   Player(const Role role)
   {
      switch (role)
      {
         case GRUNT: myHelmet = new PaperHat; break;
         case KING:  myHelmet = new Crown; break;
         //...
      }
   }

   Helmet& getHelmet() const { return *myHelmet; }

private:
   Helmet* myHelmet;
};

class Game
{
public:
   void addPlayer(const std::string& name, const Player::Role& role)
   {
      myPlayers.insert(std::make_pair<std::string, Player*>(name, new Player(role)));
   }

   Player& getPlayer(const std::string& name)
   {
      return *myPlayers.find(name)->second;
   }

private:
   // key = name of player, value = Player object
   std::map<std::string, Player*> myPlayers;
};

int main()
{
   Game game;
   game.addPlayer("Pauper", Player::GRUNT);
   game.addPlayer("George", Player::KING);

   std::cout << "Pauper has a " << game.getPlayer("Pauper").getHelmet().getType() << std::endl;
   std::cout << "George has a " << game.getPlayer("George").getHelmet().getType() << std::endl;
}

```

---

### Post by karlson on 2011-08-11
> **Ravenshade said:**
> Hm, I did as you suggested but the problem stems from me trying to do multiple things at the same time. I.e shorten my code. 

reminder... 

my original problem is with aria.get_map(world, display) and I'd like to be able to 'change' the first part of that so basically...

get_class_name().get_map(world, display)


Which is the wrong way to go.

The better way to go is:
```

character.get_display().get_world().get_map();

```

since all your maps are tied to the characters.

> 
strangely, everyone is going after my encapsulation, which I'm working on. You guys should have seen the first release, I wasn't even using header files! (This is the first class I've used in this program). 

That being said what I was trying to do was..

//won't someone please install a c++ version of this php tag? >.<


How about using code tag?

> 
[PHP]
class test
{
private:
     int test_param;
     int test_param2;
     int test_param3;
public:
     void set_test_params(int x, int y, int z)
     {
         test_param = x; 
         test_param2 = y;
         test_param3 = z;
     }
};

test test_obj;
test_obj.set_test_params(10, 9, 8);
[/PHP]


The best way to do this is:
```

class test
{
private:
     int test_param;
     int test_param2;
     int test_param3;
public:
     test(int x, int y, int z)
         : test_param(x)
         , test_param2(y)
         , test_param3(z)
     {}
     void set_test_param1(int x)
     {
         test_param = x; 
     }
};

test test_obj(10, 9, 8);

```

> 
That's when I get the & issue. Just declaring the one variable is fine but... I don't see why I should write extra code...just for the sake of writing code, where I'm basically writing 3 sets of set_test_param just to get each variable.

That being said, I need the practice, so I've gone ahead and done it >.<;


Don't try to limit the amount of code you write until you have a clear understanding of C++ and OO design and interfaces.  Trying to limit the amount of code you write will force you to take shortcuts that will cause you grief when trying to modify or maintain the code.  Like:
Character:
Need to move up
Need to move down
Need to move left
need to move right
need to get position
need to report slots

Based on this you define your public functions and define relationships to other classes of objects.

> 
I only have one thing really to encapsulate at he moment and that is the regions. 

Aria is a Region

In C++ speak that means:

```

class Aria : public Region

```

You need to understand the "is a" and "has a" relationship.

---

### Post by Ravenshade on 2011-08-11
Thank you very much for that program, it does demonstrate an idea that might be useful. I haven't looked at it properly just yet but I plan to as I'll do that for the next stage in my programs development. (After...after I've put an orb down that...jack can collect)

As for tying character to map, that's what I'm trying to separate with character part of it's own and region part of it's own. (Of course, I don't have a class of character...yet). This might be what you mean, or I may not have any other choice. That being said it looks similar to Whitney's solution so of course, I will be looking into it. 

I'm not 'trying' to limit my code as such... but if I see

```
int get (x);
int get (y);
int get (z);
```

I'd sooner have...

```
int mega_get(x, y, z);
```

edit. 

I am..officially confused but thanks for the help ^_^

---

### Post by karlson on 2011-08-11
> **Ravenshade said:**
> 
I'm not 'trying' to limit my code as such... but if I see

```
int get (x);
int get (y);
int get (z);
```

I'd sooner have...

```
int mega_get(x, y, z);
```

edit. 

I am..officially confused but thanks for the help ^_^

Do you ever need to get individual parameters?  If not then the get function would look like:

```

void mega_get(int &x, int &y, int &z);

```

---

### Post by Ravenshade on 2011-08-11
Thank you again and apologies for any seemingly 'stubborness' it's just in my nature. 

Just like how pointers still confuse me (I think I understand them, but be damned if I know how to use them half the time) the & (by ref?) also confuses the hell out of me DX No matter how many times I read that chapter. 

Thanks again.

---

### Post by karlson on 2011-08-11
> **Ravenshade said:**
> Thank you again and apologies for any seemingly 'stubborness' it's just in my nature. 

Just like how pointers still confuse me (I think I understand them, but be damned if I know how to use them half the time) the & (by ref?) also confuses the hell out of me DX No matter how many times I read that chapter. 

Thanks again.

There is no difference between pointer and a reference in the background.  If the analogy would make it any better is reference is the same as the symbolic link in the file system, a different name representing the same object.

---

### Post by Ravenshade on 2011-08-11
Well apart from the fact that passing by value, copies information while passing by reference doesn't >.>; (It creates something but it's not as much...apparently)

But thanks for that analogy it does make it a little easier to understand.

---

### Post by karlson on 2011-08-11
> **Ravenshade said:**
> Well apart from the fact that passing by value, copies information while passing by reference doesn't >.>; (It creates something but it's not as much...apparently)


I think delving into the internals of how pass by reference is implemented is a little to early.

---

