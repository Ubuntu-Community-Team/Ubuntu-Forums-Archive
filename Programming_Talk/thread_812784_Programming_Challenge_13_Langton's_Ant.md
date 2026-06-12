---
title: "Programming Challenge 13: Langton's Ant"
date: 2008-05-30
forum: Programming Talk
---

### Post by Alasdair on 2008-05-30
Langton's ant is a very simple two dimensional Turing machine that uses a incredibly basic set of rules, and yet still manages to produce surprisingly complex behaviour. The rules are as follows; You have a plane with either black or white squares, and one (or more) of these squares is taken to be the 'ant'. The ant can travel either north, south, east or west for every move it makes on the plane. It can move only in accordance with the following rules:
[LIST=1]
[*]When the ant is on a black square, it turns the square white, rotates 90 degrees right and moves one square forward.

[*]When the ant is on a white square, it turns the square black, turns left 90 degrees and moves forward a square.
[/LIST]
The challenge is to simulate this action, and to find a way of visualizing it. You can use any library you want, unless they are specifically for the purpose of simulating Langton's ant (not that such libraries actually exist). Any language is allowed. There are numerous ways to extend this concept, some of which are listed below.
[LIST]
[*]Have multiple ants on the same plane, each ant could be shown with a different color.

[*]You can have more that two colors, instead of just black and white. You could (for example) have red, green, blue and yellow, with the ant turning in a predefined direction for each color it encounters.

[*]Combine the previous two suggestions.

[*]Extend the concept to into 3D - Not sure if this is possible, presumably rather than just right and left you would have right, left up and down with 4 different colors.
[/LIST]
The attached image shows two examples of what the basic two color Langton's ant configuration should look like after a certain number of moves. All entries should be in before 16:00 GMT Friday June 6th, have fun!

---

### Post by Lster on 2008-05-30
It looks interesting but where does the ant start and what is its starting direction?

---

### Post by Alasdair on 2008-05-30
It doesn't really matter where the ant starts, although the middle of the plane would make sense. The direction is also unimportant because it will generate exactly the same pattern, just rotated through 90 degrees or more. Of course, if you have more than one ant you will want to experiment with starting positions to see how they interact with one another. There's a cool animated gif on the wikipedia article that shows multiple ants ([link]("http://en.wikipedia.org/wiki/Image:MulticolorLangtonsAnt.gif")).

---

### Post by Lster on 2008-05-30
OK, thanks! :)

---

### Post by JupiterV2 on 2008-05-30
At what point should the ant terminate? Is there a predetermined number of steps it takes? Time?

---

### Post by Lster on 2008-05-30
I *assume* it should be able to continue until the user aborts.

---

### Post by Alasdair on 2008-05-30
> **Lster said:**
> I *assume* it should be able to continue until the user aborts.
Yes, that's right, it should be able to run endlessly. However with the basic white/black setup it will start a repeating pattern after about 10000 iterations. If the plane doesn't wrap around there's no point continuing (it's more fun if it does though :)). Other setups with multiple colors can form endlessly repeating cycles etc...

---

### Post by JupiterV2 on 2008-05-30
Here is version 1.1 of my ant program in C. It's trivial to add more ants by just "cloning" more of them and running them inside the code. I think I may try to add colour to spice things up a bit.

EDIT: I've added colours and multiple ants now. In order to see the colours, you'll likely have to run the program in a bash terminal. There's minimal error checking and commenting could likely be better but it runs. I should note that when an "ant" reaches the end of the field it "wraps" around to the other side. The only other thing I could implement is running the loop infinitely and waiting for a SIG_ABORT to print the picture.

EDIT2: Updated field size to something more entertaining (width: 10 => 40, length: 10 => 20). Run with a value of 10000 to make it pretty.

EDIT3: Updated main.c to reset terminal to defaults.

** ant.h **
[PHP]#ifndef ANT_H
#define ANT_H

// redifine to change the size of the map
#define FIELD_LENGTH	20
#define FIELD_WIDTH	40

// tile type
#define BLACK	0
#define WHITE	1

// directions ant faces
#define DIR_NORTH	1
#define DIR_EAST	2
#define DIR_SOUTH	3
#define DIR_WEST	4

// ant colours
#define COL_RED 	31
#define COL_GREEN	32
#define COL_ORANGE	33
#define COL_BLUE	34
#define COL_MAGENTA	35
#define COL_CYAN	36
#define COL_GREY	37

//*****************************************************************************
// Data Types
//*****************************************************************************

typedef struct Ant
{
	int coord_x, coord_y;
	int colour;
	int direction;
} ant_t;

typedef struct Map
{
	unsigned int field[FIELD_LENGTH][FIELD_WIDTH];
	unsigned int field_colour[FIELD_LENGTH][FIELD_WIDTH];
} map_t;

//*****************************************************************************
// Function Declarations
//*****************************************************************************

void ant_init(ant_t* a, int c);

void ant_move(ant_t* a, map_t* m);

void map_init(map_t* m);

void map_print_ant_trail(map_t* m);

#endif // ANT_H[/PHP]

** ant.c **
[PHP]#include "ant.h"

#include <stdio.h>
#include <stdlib.h>

void ant_init(ant_t* a, int c) 
{
	// defaults: centre ant in middle of field and set direction to north
	
	a->direction = DIR_NORTH;
	a->coord_x = FIELD_WIDTH / 2;
	a->coord_y = FIELD_LENGTH / 2;
	
	switch(c)
	{
		case COL_RED: case COL_GREEN: case COL_ORANGE: case COL_BLUE: 
		case COL_MAGENTA: case COL_CYAN: case COL_GREY:
			a->colour = c;
			break;
		default: a->colour = COL_GREY;
	}
}

void ant_move(ant_t* a, map_t* m)
{
	// if current square is white, change it to black and turn right
	// else change it to white and turn left. 
	
	int x = a->coord_x, y = a->coord_y;
	
	m->field_colour[y][x] = a->colour;
	
	if( m->field[y][x] == WHITE )
	{
		m->field[y][x] = BLACK;
		
		if( a->direction + 1 > DIR_WEST ) a->direction = DIR_NORTH;
		else a->direction++;
	}
	else
	{
		m->field[y][x] = WHITE;
		
		if( a->direction - 1 < DIR_NORTH ) a->direction = DIR_WEST;
		else a->direction--;
	}
	
	// once rotated move ahead one square
	
	switch(a->direction)
	{
		case DIR_NORTH:
			if( a->coord_y - 1 < 0 ) a->coord_y = FIELD_LENGTH - 1;
			else a->coord_y--;
			break;
			
		case DIR_EAST:
			if( a->coord_x + 1 >= FIELD_WIDTH - 1 ) a->coord_x = 0;
			else a->coord_x++;
			break;
			
		case DIR_SOUTH: 
			if( a->coord_y + 1 >= FIELD_LENGTH - 1 ) a->coord_y = 0;
			else a->coord_y++;
			break;
			
		case DIR_WEST: 
			if( a->coord_x - 1 < 0 ) a->coord_x = FIELD_WIDTH - 1;
			else a->coord_x--;
			break;
	}
}

void map_init(map_t* m)
{
	// initialize entire field to black
	
	int x, y;
	
	for(y = 0; y < FIELD_LENGTH; y++)
	{
		for(x = 0; x < FIELD_WIDTH; x++)
		{
			m->field[y][x] = BLACK;
			m->field_colour[y][x] = COL_GREY;
		}
	}
}

void map_print_ant_trail(map_t* m)
{
	int x, y;
	
	for(y = 0; y < FIELD_LENGTH; y++)
	{
		for(x = 0; x < FIELD_WIDTH; x++)
		{
			printf("\033[22;%dm%d", m->field_colour[y][x], m->field[y][x]);
		}
		
		printf("\n\033[22;%dm", COL_GREY);
	}
}[/PHP]

** main.c **
[PHP]#include <stdio.h>
#include <stdlib.h>

#include "ant.h"

void exit_with_bad_args(char* name)
{
	printf("Usage: %s <number_of_steps>\n", name);
	exit(1);
}

int main(int argc, char** argv)
{
	int count = 0;
	
	if( argc == 2 ) count = atoi(argv[1]);
	else exit_with_bad_args(argv[0]);
	
	ant_t ant1;
	ant_t ant2;
	ant_t ant3;
	ant_t ant4;
	map_t map;
	
	ant_init(&ant1, COL_BLUE);
	ant_init(&ant2, COL_GREEN);
	ant_init(&ant3, COL_RED);
	ant_init(&ant4, COL_CYAN);
	map_init(&map);
	
	while( count-- )
	{
		ant_move(&ant1, &map);
		ant_move(&ant2, &map);
		ant_move(&ant3, &map);
		ant_move(&ant4, &map);
	}
	
	map_print_ant_trail(&map);
	
	// reset terminal colours to defaults
	printf("\033[0m");
	
	return 0;
}[/PHP]

---

### Post by ZuLuuuuuu on 2008-06-01
I tried to program a simple version via Io programming language which I learned just yesterday :D I surprisingly liked it. As object oriented as Ruby or Smalltalk and as simple as Python (even simpler). Everything is object, there are even no classes; you create objects by cloning another objects.

**How to run this program:**
1) You should first download Io virtual machine code from:

[http://www.iolanguage.com/downloads/](http://www.iolanguage.com/downloads/)

2) Then compile it with "make" and "sudo make install" commands. It will say that a lot of addons couldn't be installed because of missing packages but it is not important because they are optional, so don't worry.

3) Finally, run the command "io ant.io" while you are on the folder of ant.io file, whose code is given below.

**ant.io**
```
Square := Object clone

//
// Instance variables of Square
//

Square position := List clone	// coordinate in (x, y) format
Square position append(1)	// x coordinate
Square position append(1)	// y coordinate
Square color := "White"

Plane := Object clone

//
// Instance variables of Plane
//

Plane height := 1
Plane width := 1
Plane squares := List clone
Plane squares append(Square clone)

//
// Methods of Plane
//

Plane resetSquares := method(
	self squares removeAll
	self height repeat(y,
		self width repeat(x,
			self squares append(Square clone)
			self squares at((self squares size) - 1) position atPut(0, x + 1)
			self squares at((self squares size) - 1) position atPut(1, y + 1)
		)
	)
	return self
)

Plane setWidth := method(newWidth,
	self width := newWidth
	self resetSquares
)

Plane setHeight := method(newHeight,
	self height := newHeight
	self resetSquares
)

Plane getSquare := method(position,
	return self squares at(((position at(1) - 1) * (self width) + position at(0)) - 1)
)

Plane getSquareColor := method(position,
	return self getSquare(position) color
)

Plane setSquareColor := method(position, color,
	self getSquare(position) color := color
)

Plane drawYourself := method(
	((self width) + 2) repeat("-" print)
	"" println
	self height repeat(y,
	"|" print
		self width repeat(x,
			(self getSquareColor(list(x + 1, y + 1)) == "White") ifTrue(
				" " print
			) ifFalse(
				"X" print
			)
		)
		"|" println
	)
	((self width) + 2) repeat("-" print)
	"\n\n\n\n\n" println
)

Ant := Object clone

//
// Instance variables of Ant
//

Ant position := List clone
Ant direction := "East"

//
// Methods of Ant
//

Ant setPosition := method(x, y,
	self position := list(x, y)
)

Ant setDirection := method(direction,
	self direction := direction
)

Ant moveOn := method(plane,
	(plane getSquareColor(self position) == "White") ifTrue(
		plane setSquareColor(self position, "Black")
		self turnTo("Left")
	) ifFalse(
		plane setSquareColor(self position, "White")
		self turnTo("Right")
	)

	(self direction == "East") ifTrue(
		self position atPut(0, (self position at(0)) + 1)
		(plane width < self position at(0)) ifTrue(
			self position atPut(0, 1)
		)
	)
	(self direction == "South") ifTrue(
		self position atPut(1, (self position at(1)) + 1)
		(plane height < self position at(1)) ifTrue(
			self position atPut(1, 1)
		)
	)
	(self direction == "West") ifTrue(
		self position atPut(0, (self position at(0)) - 1)
		(1 > self position at(0)) ifTrue(
			self position atPut(0, plane width)
		)
	)
	(self direction == "North") ifTrue(
		self position atPut(1, (self position at(1)) - 1)
		(1 > self position at(1)) ifTrue(
			self position atPut(1, plane height)
		)
	)
)

Ant turnTo := method(direction,
	(direction == "Right") ifTrue(
		(self direction == "East") ifTrue(
			self direction := "South"
		) ifFalse((self direction == "South") ifTrue(
			self direction := "West"
		) ifFalse((self direction == "West") ifTrue(
			self direction := "North"
		) ifFalse((self direction == "North") ifTrue(
			self direction := "East"
		))))
	) ifFalse(
		(self direction == "East") ifTrue(
			self direction := "North"
		) ifFalse((self direction == "North") ifTrue(
			self direction := "West"
		) ifFalse((self direction == "West") ifTrue(
			self direction := "South"
		) ifFalse((self direction == "South") ifTrue(
			self direction := "East"
		))))
	)		
)

//
// The main program
//

plane := Plane clone
ant := Ant clone

////////////////////////
plane setWidth(10)
plane setHeight(10)

ant setPosition(1, 1)
ant setDirection("East")
////////////////////////

loop(
	ant moveOn(plane)
	plane drawYourself
	wait(0.5)
)
```

**Notes:**
 - You can change plane's dimensions from lines 167 and 168.
 - You can change ant's first position from line 170.
 - You can change ant's first direction (East, South, West or North) from line 171.
 - Coordinates begin from number 1 not 0.
 - Upper left coordinate is (1, 1).
 - It displays the plane via text on terminal. X means square is black, emptiness means square is white.
 - Once run, you cannot stop the animation, you have to close terminal (sorry for that).
 - You can change the animation speed by changing the number on line 177. It is how many seconds to wait between steps.

---

### Post by nvteighen on 2008-06-01
> **JupiterV2 said:**
> (...)

Great, but after running, bash font color doesn't change back to original until I close terminal.

I know it's a very low priority bug, of course. ;)

---

### Post by klange on 2008-06-01
Hmm. I'll play. Python and PyGame will do perfectly.

```
#!/usr/bin/python
# Langston's Ant

import pygame, random # should be all we need.

pygame.display.init()
boardsize = 64
screenbuffer=pygame.display.set_mode((boardsize,boardsize),pygame.SWSURFACE,24)
direction = 0 # right, down, left, up, k? +1 = turn right, -1 = turn left.
rand = random.Random()
antLocation = [rand.randint(0,boardsize-1),rand.randint(0,boardsize-1)] # Start us off somewhere.
for i in range(0,boardsize):
    for j in range(0,boardsize):
        if (rand.randint(0,40) > 0):  # makes a very white board.
            screenbuffer.set_at((i,j),(255,255,255))
while True:
    if (screenbuffer.get_at(antLocation)[0] == 255):
        direction -= 1
        screenbuffer.set_at(antLocation, (0,0,0))
    else:
        direction += 1
        screenbuffer.set_at(antLocation, (255,255,255))
    if (direction < 0):
        direction += 4
    if (direction > 3):
        direction -= 4
    if (direction == 0):
        antLocation[0] += 1
    elif (direction == 1):
        antLocation[1] += 1
    elif (direction == 2):
        antLocation[0] -= 1
    elif (direction == 3):
        antLocation[1] -= 1
    if antLocation[0] < 0:
        antLocation[0] += boardsize
    elif antLocation[0] > boardsize - 1:
        antLocation[0] -= boardsize
    if antLocation[1] < 0:
        antLocation[1] += boardsize
    if antLocation[1] > boardsize-1:
        antLocation[1] -= boardsize
    pygame.display.flip()
pygame.display.quit()
```

---

### Post by AZzKikR on 2008-06-03
Alright, I had nothing to do so here's my go. It's in C++. My first try was in C only, but decided to make it a little more object oriented :)

Features:
- Outputs to a terminal
- Wraps around the plane

Other mentionable stuff:
- The boardsize can not be set dynamically as it is now. I've declared two static const integers for the width and height.
- It's totally NOT configurable through any other means than editing source code ;)

I wanted to make some OpenGL rendering too, but my RedHat workstation is a bit flaky, so I'll just leave it at that... or I'll have to do it at home :D

Source code is also downloadable for this post, including the Makefile.

Code listing:

**./src/langton.hpp**
```

#ifndef LANGTON_HPP_
#define LANGTON_HPP_
/**
 * Ant class. Only has some basic information like position, and the
 * current travelling direction. Only real modifier functions are 
 * for turning left or right.
 */
class Ant {
public:
	
	/// Direction, NESW.
	enum Direction {
		DIR_NORTH, DIR_SOUTH, DIR_WEST, DIR_EAST
	};

	/**
	 * Constructor.
	 */
	Ant();
	
	/**
	 * Destructor.
	 */
	~Ant();

	/**
	 * Turns left. Dependend on the current direction, the x or y
	 * coordinate of the ant is changed.
	 */
	void turnLeft();
	
	/**
	 * Turns right. Dependend on the current direction, the x or y
	 * coordinate of the ant is changed.
	 */
	void turnRight();
	
	/**
	 * Gets the current x position of the ant.
	 * @return the x position.
	 */
	int getX();

	/**
	 * Gets the current y position of the ant.
	 * @return the y position.
	 */
	int getY();
	
	/**
	 * Sets the x position of the ant.
	 * @param x The x position to set.
	 */
	void setX(int x);
	
	/**
	 * Sets the y position of the ant.
	 * @param y the y position of the ant to set.
	 */
	void setY(int y);

private:
	/// The current direction.
	Direction m_direction;
	
	/// The current x position.
	int m_x;
	
	// The current y position.
	int m_y;
};

/**
 * The 'board' of the ant to move on, with a predetermined size. 
 * I couldn't figure out how to make this multidimensional array
 * dynamic (some people told me to use std::vector on #irc on 
 * freenode.org, but I found that too much of a hassle just for 
 * this programming challenge :-)).
 */
class Plane {
public:
	
	/// The width of the plane.
	static const int WIDTH = 30;
	
	/// Height of the plane.
	static const int HEIGHT = 18;
	
	/// Is a space 'on'?
	static const int ON = 1;
	
	/// Is a space 'off'?
	static const int OFF = 0;

	/**
	 * Constructor.
	 */
	Plane();
	
	/**
	 * Destructor.
	 */
	~Plane();

	/// Meh, can't be arsed to comment this further.
	
	void setAnt(Ant*);
	void flipColor(Ant*);
	int getColorAt(Ant*);
	int getWidth();
	int getHeight();
	void output();
	void checkWrap();
	void moveAnt();
	
private:
	int m_plane[HEIGHT][WIDTH];

	Ant* m_ant;
};

#endif /*LANGTON_HPP_*/


```

**./src/langton.cpp**
```

#include "langton.hpp"

#include <iostream>

using namespace std;

Ant::Ant() {
	m_direction = DIR_NORTH;
}

Ant::~Ant() {
}

int Ant::getX() {
	return m_x;
}

int Ant::getY() {
	return m_y;
}

void Ant::setX(int x) {
	m_x = x;
}

void Ant::setY(int y) {
	m_y = y;
}

void Ant::turnRight() {
	// turn 90 degress right, which is dependent on the current direction.
	switch (m_direction) {
		case DIR_NORTH: m_direction = DIR_EAST; m_x += 1; break; // move right in array
		case DIR_EAST: m_direction = DIR_SOUTH; m_y += 1; break; // move down in array
		case DIR_SOUTH: m_direction = DIR_WEST; m_x -= 1; break; // move left in array
		case DIR_WEST: m_direction = DIR_NORTH; m_y -= 1; break; // move up in array.
		default: m_direction = DIR_NORTH; break; // should not happen.
	}
}

void Ant::turnLeft() {
	// turn 90 degress left, which is dependent on the current direction.
	switch (m_direction) {
		case DIR_NORTH:	m_direction = DIR_WEST;	m_x -= 1; break; // move right in array
		case DIR_WEST: m_direction = DIR_SOUTH; m_y += 1; break; // move down in array
		case DIR_SOUTH: m_direction = DIR_EAST; m_x += 1; break; // move left in array
		case DIR_EAST: m_direction = DIR_NORTH; m_y -= 1; break; // move up in array.
		default: m_direction = DIR_NORTH; break;
	}
}

//-----------------------------------------------------------------------------

Plane::Plane() {
	// initialize an array with all zeroes. 
	for (int i = 0; i < Plane::HEIGHT; i++) {
		for (int j = 0; j < Plane::WIDTH; j++) {
			m_plane[i][j] = 0;
		}
	}
}

Plane::~Plane() {
}

void Plane::setAnt(Ant* ant) {
	m_ant = ant;
}

void Plane::flipColor(Ant* ant) {
	/* 
	 * NOTE: This color flipping could also just be done using the ! 
	 * operator, because I'm using ones and zeroes only. But that'll
	 * pose a problem in some (possible) future expansion, so I just left
	 * it like this. 
	 */ 
	
	int color = m_plane[ant->getY()][ant->getX()];
	
	if(color == Plane::OFF) {
		m_plane[ant->getY()][ant->getX()] = Plane::ON;
	} else {
		m_plane[ant->getY()][ant->getX()] = Plane::OFF;
	}
}

int Plane::getColorAt(Ant* ant) {
	// simply gets the value on the plane where the ant is residing.
	return m_plane[ant->getY()][ant->getX()];
}

void Plane::moveAnt() {
	flipColor(m_ant); // flip a color where the current ant is.
	
	if(getColorAt(m_ant) == Plane::OFF) {
		// if the color is off, turn left.
		m_ant->turnLeft(); 
	} else if(getColorAt(m_ant) == Plane::ON) {
		// and if on, turn right.
		m_ant->turnRight();
	}
	
	// check whether we went out of bounds of the array. If so,
	// wrap around (i.e. x > width -> x = 0, etc.
	checkWrap();
}

void Plane::checkWrap() {
    // make sure we wrap around the thing:
    if(m_ant->getX() < 0) {
        m_ant->setX(Plane::WIDTH - 1);
    } 

    if(m_ant->getY() < 0) {
        m_ant->setY(Plane::HEIGHT - 1);
    }

    if(m_ant->getX() > Plane::WIDTH - 1) {
    	m_ant->setX(0);
    }

    if(m_ant->getY() > Plane::HEIGHT - 1) {
    	m_ant->setY(0);
    }
}

void Plane::output() {
	// simple outputting here
	for(int i = 0; i < Plane::HEIGHT; i++) {
		for(int j = 0; j < Plane::WIDTH; j++) {
			if(m_plane[i][j] == Plane::OFF) {
				cout << "."; // for OFF colors, print a dot
			} else if (m_plane[i][j] == Plane::ON) {
				cout << "*"; // for ON colors, print an asterisk0rize
			}
		}
		cout << '\n'; // no endl for this plx.
	}
}



```

**./src/main.cpp**
```
#include <iostream>

#include "langton.hpp"

using namespace std;

int main(int argc, char* argv[]) {
	Ant* ant = new Ant();
	ant->setX(Plane::WIDTH / 2);
	ant->setY(Plane::HEIGHT / 2); // starting position.
	
	Plane* plane = new Plane();
	plane->setAnt(ant);
	
	while(true) {
		plane->output();
		plane->moveAnt();
		cout << '\n'; // std::endl may result in some buffering performance drawbacks.
		usleep(10000);
	}
	
	delete ant;
	delete plane;
}

```

---

### Post by Alasdair on 2008-06-04
Some good entries so far! All of them work nicely on my machine (although the io version needed a few config files to be tweaked).

---

### Post by matja on 2008-06-04
Nice entries so far!

I gave it a go with with C++ and SDL. To compile it you need Boost v1.35 and since I only can find 1.34 in the repository, it probably needs to be downloaded from [http://www.boost.org]("http://www.boost.org") and manually installed. In particular Boost.Thread and Boost.Program_options are needed with compiled libraries. Oh, and I used a newer version of the SCons build system than the one in the repository, but hopefully it should work with that one as well. Otherwise, let me know. For those of you willing to go through the trouble, more detailed instructions are found in the README included in the attached tar archive. Once you got it compiled, just click on the squares to insert ants. This is my first go with both SDL and threads in C++, so feel free to comment on my code!

For those of you that aren't willing to go through the trouble, I included a screenshot ;)

Great challenge, Alasdair!

Mattias

---

### Post by BeardlessForeigner on 2008-06-04
Here is my try in Haskell. I just started learning Haskell a few weeks ago with *The Haskell School of Expression*, and so I used an implementation of the graphics library it uses, called Graphics.SOE.Gtk. This is part of the libghc6-soegtk-dev package in the repos. Unfortunately this library (or my program) seems to have some issues, and my program starts lagging after 30 secs or so. I'll see if I can fix it and update my code. If you have ghc6 and the graphics library installed, run the command runhaskell LangtonsAnt.hs to run, and press any key to quit. Anyways, here it is.

```
import Graphics.SOE.Gtk
import Array
import Control.Concurrent

-- Types
data Direction = North | East | South | West 
    deriving (Show, Eq, Enum)

type Position = (Int, Int)
type Plane = Array Position Color
type Ant = (Position, Direction)

-- Constants
size, wSize, bSize, delay :: Int
size = 20 -- Width & height of the plane as a # of blocks
wSize = 800 -- Width & height of the window in px
bSize = wSize `div` size -- Width of the blocks in px
delay = 80 -- Length of delay added after every step in milliseconds

ant :: Ant
ant = ((10,10),North) -- Initial ant

plane :: Plane
plane = array ((0,0),(size-1,size-1)) [((x,y),White) | x <- r, y <- r]
        where r = [0..size-1]

-- Functions
right, left :: Direction -> Direction
right d = toEnum $ succ (fromEnum d) `mod` 4
left d = toEnum $ pred (fromEnum d) `mod` 4

turnRight, turnLeft :: Ant -> Ant
turnRight (pos, dir) = (pos, right dir)
turnLeft (pos, dir) = (pos, left dir)

move :: Ant -> Ant
move ((x,y), dir) = ((x',y'), dir) where
    (x',y') = case dir of
                 North -> (x, (y-1) `mod` size)
                 East  -> ((x+1) `mod` size, y)
                 South -> (x, (y+1) `mod` size)
                 West  -> ((x-1) `mod` size, y)

drawBlock :: Window -> Position -> Color -> IO ()
drawBlock w (x,y) c = drawInWindow w pic where
    x0, y0 :: Int
    x0 = x*bSize
    y0 = y*bSize
    pic :: Graphic
    pic = withColor c $ polygon [(x0,y0), (x0+bSize,y0), 
                                 (x0+bSize,y0+bSize), (x0,y0+bSize)]

drawPlane :: Window -> Plane -> IO ()
drawPlane w p = sequence_ [drawBlock w (x,y) (p!(x,y)) | x <- r, y <- r]
    where r = [0..size-1]

step :: Window -> Plane -> Ant -> IO (Plane, Ant)
step w p a@((x,y),dir) = do
    case p!(x,y) of
         White -> do drawBlock w (x,y) Black
                     return (p//[((x,y),Black)], (move . turnLeft) a)
         Black -> do drawBlock w (x,y) White
                     return (p//[((x,y),White)], (move . turnRight) a)

loop :: Window -> Plane -> Ant -> IO ()
loop w p a = do
    (p',a') <- step w p a
    threadDelay (1000*delay)
    loop w p' a'

main :: IO ()
main = do
    runGraphics $
        do w <- openWindow "Langton's Ant" (wSize,wSize)
           drawPlane w plane
           loopTh <- forkIO $ loop w plane ant
           k <- getKey w
           killThread loopTh
           closeWindow w

```

---

### Post by Lau_of_DK on 2008-06-05
Hey,


I didn't think I'd have the time to enter, but I managed to find a few hours to spare.

There's a new language in town called Clojure which sits on the JVM. Its a Lisp-1 and sports immutable persistant datastructures. My entry is a GUI swing application written in Clojure. Its based losely on Rich Hickeys Ant-farm simulator. The interesting thing is that the ants (4 by default) are independant worker-threads that interact with the board by atomically mutating references. There is a seperate animator thread which reads a snapshot of the board every 50 ms and prints it. Clojure is by default thread-safe, because everything is immutable.

The code is a mess, but it works.

To run the code, install a Java JVM on your system and get [Clojure.zip]("http://dfn.dl.sourceforge.net/sourceforge/clojure/clojure_20080329.zip"). In this zipfile you'll find clojure.jar, put it somewhere and browse to that folder. then in a terminal type

```

java -cp clojure.jar clojure.lang.Repl

```

Then you'll get a working repl. In it type (load-file "/path/to/ants.clj") <enter> and then (go)<enter>. This will run on any platform, since its a Java Swing application. (yes, I can make this easier, but I'm due for work in a few hours and need sleep)

If you disregard the GUI (which is cool if you're into Clojure) then the basic logic is this

```

(defstruct cell :color)

(def board    
     (apply vector 
            (map (fn [_] 
                   (apply vector
                          (map (fn [_] (ref (struct cell white))) 
                                      (range dim)))) 
                 (range dim))))


(defn coordinate [[x y]]
  (-> board (nth x) (nth y)))

(defstruct ant :dir) 

(defn spawn-ant 
  [loc dir]
    (dosync
      (let [p (coordinate loc)
            a (struct ant dir)]
        (alter p assoc :ant a)
        (agent loc))))


(defn setup 
  []
  (dosync
     (doall
       (for [x (range dim) y (range dim)]
         (if (and (= 0 (rem x 2)) (= 0 (rem y 2)))
          (do (alter (coordinate[x y]) assoc :color white)))))
     (doall
       (for [x (range 4)]
         (do (spawn-ant [(rand-int dim) (rand-int dim)] (rand-int 4)))))))



(def dir-delta {0 [0 1]
                1 [1 0]
                2 [0 -1]
                3 [-1 0]})
                
                

(defn next-loc 
  [[x y] dir]
    (let [[dx dy]
          (dir-delta dir)]
      [(bound dim (+ x dx)) (bound dim (+ y dy))]))


;; As original
(defn bound 
  "returns n wrapped into range 0-b"
  [b n]
    (let [n (rem n b)]
      (if (neg? n) 
        (+ n b) 
        n)))
      
(defn turn 
  "turns the ant at the location by the given amount"
  [loc amt]
     (let [p (coordinate loc)
           ant (:ant @p)]
       (alter p assoc :ant (assoc ant :dir (bound 4 (+ (:dir ant) amt)))))
    loc)

(defn move 
  "moves the ant in the direction it is heading. Must be called in a
  transaction that has verified the way is clear"
  [loc]
     (let [oldp (coordinate loc)
           ant (:ant @oldp)
           newloc (next-loc loc (:dir ant))
           p (coordinate newloc)]
         ;move the ant
       (alter p assoc :ant ant)
       (alter oldp dissoc :ant)
        newloc))


(defn behave 
  "the main function for the ant agent"
  [loc]
  (let [p (coordinate loc)
        ant (:ant @p)
        ahead (coordinate (next-loc loc (:dir ant)))]
    (dosync
     (when running
       (send-off *agent* #'behave))
     (. Thread (sleep ant-sleep-ms))
     (if (= black (:color @p))
       (do
         (alter p assoc :color white)
         (move (turn loc 1)))
       (do
         (alter p assoc :color black)
         (move (turn loc -1)))))))
       

```

In setup I spawn 4 "ants", which are working threads with references to the board. The board itself is never changed, but the references are changed in (dosync) nests. Dosync starts a transaction which ensures that the reader (animator) is always looking at a consistant view of the board - ie. no ants overlapping or half changed cells. This approach is completely threadsafe. When the alteration of references is atomic, then there is no state-in-between. If you up the number of ants to 60, you would have (in addition to a slow program) 61 threads working together in perfect harmony. This is part of the magic of Clojure - Everything is immutable by default, everything happends in transactions so the world-view is consistant.

/Lau

---

### Post by Alasdair on 2008-06-06
Clojure looks cool, I'll have to check it out once I have more free time. Unfortunately, I can't seem to get your program to work. I get the repl working nicely, but when I load your file...

Edit: Ignore this: I got it working by pasting the definition for the bound function in your post into the repl. It's very nice :).

```
java.lang.Exception: Unable to resolve symbol: bound in this context
clojure.lang.Compiler$CompilerException: ants.clj:78: Unable to resolve symbol: bound in this context
        at clojure.lang.Compiler.analyzeSeq(Compiler.java:3364)
        at clojure.lang.Compiler.analyze(Compiler.java:3296)
        at clojure.lang.Compiler.analyze(Compiler.java:3271)
        at clojure.lang.Compiler.access$100(Compiler.java:37)
        at clojure.lang.Compiler$VectorExpr.parse(Compiler.java:2347)
        at clojure.lang.Compiler.analyze(Compiler.java:3298)
        at clojure.lang.Compiler.analyze(Compiler.java:3271)
--- about 20 or so more lines of java nonsense ---
```
Maybe I'm missing some java packages I need.

Only 3 hours left! Every entry runs well, it's going to be  a tough decision.:)

---

### Post by Lau_of_DK on 2008-06-06
Alasdair,


I just need to be sure I understand. You wrote "Edit: Ignore this: I got it working" - Does that mean you didn't get it working?

It shouldn't require anything in addition to sun-java6-jre as far as I know, and as long as bound is defn'ed above the functions that need it, it shouldn't need to be declared in the Repl.

If its still not working, let me know,
/Lau

---

### Post by Alasdair on 2008-06-06
Yes I was able to get it working, hence the 'ignore this' message. Sorry if it wasn't 100% clear. Bound appears to be defined below next-loc which uses it, so defining it in the repl solved the problem I had.

--------------------------------

Anyway the time limit for this challenge is officially up, so congratulations to **matja** for his winning C++ entry! Being able to add ants on the fly by clicking on the plane was a nice touch, it was easy to change the size and speed of the simulation, and it was also really fast and smooth even with a huge board and tonnes of ants. All in all a really solid entry, even if it was a bit tricky to get it set up with boost and scons.:)

Special mention should go to Lau for his interesting Clojure version, and both WindowsSucks and BeardlessForeigner for providing succinct graphical implementations in Python and Haskell respectively.

---

### Post by nvteighen on 2008-06-06
Congrats, matja!

---

### Post by Lau_of_DK on 2008-06-06
Yea Congratz Matja,

I knew I was beat when I noticed the click-to-add feature. Good job!

/Lau

---

### Post by Lster on 2008-06-06
Congrats matja! :KS

I just knew I was beat when I realized... I forgot to enter!

---

### Post by matja on 2008-06-06
Wow, thanks a lot guys! Nice to know the hours spent was worth the effort :) I really liked the rest of the contributions, I definitely didn't win the "feature per line of code" price!

Right now I'm out in the swedish contry side, lying in the sun and drinking cold beers, so I'll probably won't post the next challenge until monday. I hope that's ok. Any suggestions are most welcome by the way.

Thanks again for this great challenge, Alasdair!

Mattias

---

### Post by JupiterV2 on 2008-06-06
Congrats Matja! Well done!

---

### Post by ZuLuuuuuu on 2008-06-06
Congratulations :)

---

