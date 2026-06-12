---
title: "Programming challenge: Ulam Spiral"
date: 2008-10-24
forum: Programming Talk
---

### Post by alberto ferreira on 2008-10-24
[SIZE=4]**What is it:**[/SIZE]

Ulam spiral is a spiral that shows a pattern in prime numbers. Here it is the link to what it's all about:
[http://en.wikipedia.org/wiki/Ulam_spiral](http://en.wikipedia.org/wiki/Ulam_spiral)

If you are curious you can see this related links too although it's not required:
[http://en.wikipedia.org/wiki/Chaos_theory](http://en.wikipedia.org/wiki/Chaos_theory)
[http://en.wikipedia.org/wiki/Number_theory](http://en.wikipedia.org/wiki/Number_theory)
[http://en.wikipedia.org/wiki/Sacks_spiral](http://en.wikipedia.org/wiki/Sacks_spiral)



_[SIZE=3]**Challenge:**[/SIZE]_
 Generate an Ulam Spiral that gets printed in a terminal or outputted to a file. Use dots to represent the prime numbers.

The output format is what you wish it to be as long as the graph doesn't lose proportions or become distorted or is too small (thus becoming hard to read)  as the objective is to use the drawing for mathematical studies.

**_[SIZE=3]Bonus:[/SIZE]_**
- Allow the user to specify the biggest number that gets tested (so the program will then find and draw all primes until that number)
- Instead of starting from 1, allow the user to set the starting point

[SIZE=3]**_Rules:_**[/SIZE]
- Post the source code
- Post the result (screenshot, file, etecetera)


[COLOR=Blue]I'll try to do this too in python, however I don't know how can I output to the terminal or to a file in a practical way, choosing the exact position in which to output my (in this case) dots. Help would be appreciated :D[/COLOR]

Good luck!

---

### Post by PandaGoat on 2008-10-24
I am in.  I just started, but I will finish it this weekend.

If you are curious, I'm going to use ruby.

---

### Post by namegame on 2008-10-24
> **alberto ferreira said:**
> 

[COLOR=Blue]I'll try to do this too in python, however I don't know how can I output to the terminal or to a file in a practical way, choosing the exact position in which to output my (in this case) dots. Help would be appreciated :D[/COLOR]



I'm not sure how much you know about image manipulation, but you could generate an image and traverse the pixels and set each prime as black. It would look similar to the image from the wikipedia article you mentioned. The one disadvantage to this is that if there is no maximum input, the image you create may become extremely large.

---

### Post by Can+~ on 2008-10-24
> **alberto ferreira said:**
> 
_[SIZE=3]**Challenge:**[/SIZE]_
 Generate an Ulam Spiral that gets printed in a terminal** or outputted to a file**. Use dots to represent the prime numbers.

Bitmap included?

---

### Post by alberto ferreira on 2008-10-24
[COLOR=Red]I have updated the challenge, nothing was modified, it was just to make things clearer.[/COLOR]


@ [PandaGoat]("http://ubuntuforums.org/member.php?u=257349") : I'll definitely be waiting for your solution in ruby because I started learning python almost 1 week ago and maybe ruby will be my next language :)

@ [namegame]("http://ubuntuforums.org/member.php?u=508815") : By my previous answer you now know that I know nothing about python lol, though I'll google it, thanks!

@ [Can+~]("http://ubuntuforums.org/member.php?u=366174") : Yes, the output may be in text with dots or in a bitmap, or any other way as long as proportions of the drawing are not lost or it would lose sense and the spiral would be meaningless. Please re-read the challenge. Good luck



Thanks for input and 
Good programming everyone!

---

### Post by PandaGoat on 2008-10-25
You may be disappointed because I did not follow your guidelines precisely.  I used a graphics library called gosu and drew pixels to a window instead of outputting to a file.

When you run it, it prompts for the length of a side of a square to represent the ulam spiral and the number to start at; it forces the length of the side of a square to be an odd number so there is an exact center, and each pixel represents a number.  Moreover, I make the pixel white if the number is prime.

The size of the window is the exact size of the spiral which is bad for small spirals.  I was ambitious at first and was going to add zooming features, but gosu is very limited, and setting up the spiral is already convoluted enough (I could not really find an elegant way).

Anyway, I attached the source code and a screenshot. To run it you will have to install ruby, rubygems, and gosu (through rubygems)

Use apt to install the ruby interpreter and rubygems.  Then do "sudo gem install gosu"

Then you can run it by just doing "ruby ulamspiral.rb"

---

### Post by alberto ferreira on 2008-10-25
That's great! Could you make the dots bigger? They are too small however I couldn't try it yet, I've tried installing ruby and rubygems:

```
sudo apt-get install ruby rubygems
```then as you said I do:

```
sudo rubygems install gosu
```and the following error occurs:

> bash: rubygems: command not found

---

### Post by PandaGoat on 2008-10-25
Woops, I mean "sudo gem install gosu"


Yeah, I did not like the dots either, but for the interesting generations with large numbers, bigger dots would be too big.  I'm trying to think of a way to compensate based on the number of dots.

---

### Post by alberto ferreira on 2008-10-25
I don't know what's going on:
> ~/ruby$ sudo gem install gosu

Bulk updating Gem source index for: [http://gems.rubyforge.org/](http://gems.rubyforge.org/)
Building native extensions.  This could take a while...
ERROR:  Error installing gosu:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install gosu
extconf.rb:5:in `require': no such file to load -- mkmf (LoadError)
    from extconf.rb:5


Gem files will remain installed in /var/lib/gems/1.8/gems/gosu-0.7.10.3 for inspection.
Results logged to /var/lib/gems/1.8/gems/gosu-0.7.10.3/linux/gem_make.out


---

### Post by alberto ferreira on 2008-10-26
Well I've searched the web but I'm really lost.

How can I in python draw dots and output the result in a window as PandaGoat did or to a image file?

---

### Post by jimi_hendrix on 2008-10-26
panda goat used a library called gosu...but try searching something like python graphics engine

---

### Post by y-lee on 2008-10-26
> **alberto ferreira said:**
> Well I've searched the web but I'm really lost.

How can I in python draw dots and output the result in a window as PandaGoat did or to a image file?

Just about any of pythons [GUI frameworks]("http://wiki.python.org/moin/GuiProgramming") can draw points and lines and stuff in a window and display the result. Some can also save the image to a file. If you want to do this challenge in python and display the image in a window I would suggest pygame as the easiest to use closely followed by tkinter and wxPython. But i haven't used many of the others listed on that page.

If you would rather just generate an image file then [Python Imaging Library]("http://www.pythonware.com/products/pil/") is perhaps the most common module used for that tho there are several if not many more.

Anyway good luck :)

---

### Post by tom66 on 2008-10-26
I am currently struggling. My program does not even produce a spiral: I cannot nail down the correct 'formula'. I looked at the Ruby script for an idea about what I would need to do, but it still doesn't work. Perhaps it will help someone or somebody could help. (It's in C++, using GD)

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <gd.h>

#include "ulam.h"

char _debug_msg[100];
bool _enable_debug_messages = true;

gdImagePtr image;

bool is_prime(int n)
{
	int y = 0;
	int max = 0;
	
	max = (int)ceil(sqrt(n));
	
	for(y = 2; y < max; y++)
	{
		if(n % y == 0)
		{
			return false;
		}
	}
	
	return true;
}

int main(int argc, char *argv[])
{
	int size = 0;
	int x = 0, y = 0;
	int move_amount = 0, amount = 1;
	int dir = 0;
	int n = 0;
	int black = 0, white = 0;
	int q = 0;
	
	FILE *fp;
	
	printf("Enter x/y size (must be odd): ");
	scanf("%d", &size);
	
	if(size > 0)
	{
		if(size % 2 == 1)
		{
			DEBUG("Creating image. ");
			
			image = gdImageCreateTrueColor(size, size);
			
			black = gdImageColorAllocate(image, 0, 0, 0);
			white = gdImageColorAllocate(image, 255, 255, 255);
			
			x = y = size / 2;
			
			for(n = 0; n < (size * size); n++)
			{
				if(move_amount < amount)
				{
					if(dir == 0) 		{ x++; }
					else if(dir == 1) 	{ y++; }
					else if(dir == 2) 	{ x--; }
					else 			{ y--; }	
					
					move_amount++;
				}
				else
				{
					move_amount = 0;
					
					if(q == 0)
					{
						dir++;
						if(dir > 3) dir = 0;
				
						amount++;
						q = 0;
					}
					else
					{
						q = 1;
					}
				
					if(is_prime(n) == true)
					{
						gdImageSetPixel(image, x, y, black);
					}
					else
					{
						gdImageSetPixel(image, x, y, white);
					}
				}
				
				printf("%d (%d, %d) by %d with direction %d\n", n, x, y, amount, dir);
			}
			
			fp = fopen("output.png", "w+");
			gdImagePng(image, fp);
		}
		else
		{
			FATAL("Size should be odd. ");
		}
	}
	else
	{
		FATAL("Size should be at least 1 (use 201 for good effect). ");
	}
}

```

---

### Post by WW on 2008-10-26
For those of you interested in using Python to create a PNG file for your output, my post in [this thread](http://ubuntuforums.org/showthread.php?t=740511) shows a simple example of using the Python Image Library to create a PNG file.

---

### Post by PandaGoat on 2008-10-26
> **tom66 said:**
> I am currently struggling. My program does not even produce a spiral: I cannot nail down the correct 'formula'. I looked at the Ruby script for an idea about what I would need to do, but it still doesn't work. Perhaps it will help someone or somebody could help. (It's in C++, using GD)

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <gd.h>

#include "ulam.h"

char _debug_msg[100];
bool _enable_debug_messages = true;

gdImagePtr image;

bool is_prime(int n)
{
	int y = 0;
	int max = 0;
	
	max = (int)ceil(sqrt(n));
	
	for(y = 2; y < max; y++)
	{
		if(n % y == 0)
		{
			return false;
		}
	}
	
	return true;
}

int main(int argc, char *argv[])
{
	int size = 0;
	int x = 0, y = 0;
	int move_amount = 0, amount = 1;
	int dir = 0;
	int n = 0;
	int black = 0, white = 0;
	int q = 0;
	
	FILE *fp;
	
	printf("Enter x/y size (must be odd): ");
	scanf("%d", &size);
	
	if(size > 0)
	{
		if(size % 2 == 1)
		{
			DEBUG("Creating image. ");
			
			image = gdImageCreateTrueColor(size, size);
			
			black = gdImageColorAllocate(image, 0, 0, 0);
			white = gdImageColorAllocate(image, 255, 255, 255);
			
			x = y = size / 2;
			
			for(n = 0; n < (size * size); n++)
			{
				if(move_amount < amount)
				{
					if(dir == 0) 		{ x++; }
					else if(dir == 1) 	{ y++; }
					else if(dir == 2) 	{ x--; }
					else 			{ y--; }	
					
					move_amount++;
				}
				else
				{
					move_amount = 0;
					
					if(q == 0)
					{
						dir++;
						if(dir > 3) dir = 0;
				
						amount++;
						q = 0;
					}
					else
					{
						q = 1;
					}
				
					if(is_prime(n) == true)
					{
						gdImageSetPixel(image, x, y, black);
					}
					else
					{
						gdImageSetPixel(image, x, y, white);
					}
				}
				
				printf("%d (%d, %d) by %d with direction %d\n", n, x, y, amount, dir);
			}
			
			fp = fopen("output.png", "w+");
			gdImagePng(image, fp);
		}
		else
		{
			FATAL("Size should be odd. ");
		}
	}
	else
	{
		FATAL("Size should be at least 1 (use 201 for good effect). ");
	}
}

```

When iterating about the spiral, we move a certain amount before we switch direction.  Moreover, we move this amount only two times about two sides, then we increase the amount we move before we switch directions again.  The purpose of "q" in your code is to emulate this.

We set q to 0; let's call this the first side we move.  After we reach the amount we move on this side, we set it to 1.  Then after we reach the same amount to move on this side, we set it back to 0 and increase the amount we need to move by one.

And you need to check for every number if its prime or not.

Anyway, it seems you did not understand almost anything I did :P, although I do not blame you.  It is really confusing.

I fixed the code for you, however, I had to remove the stuff you have in your header so I could compile it:
[php]
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <gd.h>

char _debug_msg[100];
bool _enable_debug_messages = true;

gdImagePtr image;

bool is_prime(int n)
{
	int y = 0;
	int max = 0;
	
	max = (int)ceil(sqrt(n));
	
	for(y = 2; y < max; y++)
	{
		if(n % y == 0)
		{
			return false;
		}
	}
	
	return true;
}

int main(int argc, char *argv[])
{
	int size = 0;
	int x = 0, y = 0;
	int move_amount = 0, amount = 1;
	int dir = 0;
	int n = 0;
	int black = 0, white = 0;
	int q = 0;
	
	FILE *fp;
	
	printf("Enter x/y size (must be odd): ");
	scanf("%d", &size);
	
	if(size > 0)
	{
		if(size % 2 == 1)
		{
			image = gdImageCreateTrueColor(size, size);
			
			black = gdImageColorAllocate(image, 0, 0, 0);
			white = gdImageColorAllocate(image, 255, 255, 255);
			
			x = y = size / 2;
			
			for(n = 0; n < (size * size); n++)
			{
				if(move_amount < amount)
				{
					if(dir == 0) 		{ x++; }
					else if(dir == 1) 	{ y++; }
					else if(dir == 2) 	{ x--; }
					else 			{ y--; }	
					
					move_amount++;
				}
				else
				{
					move_amount = 0;
					dir++;
					if(dir > 3) dir = 0;						
					
					if(q == 0)
					{
						q = 1;
					}
					else
					{
						q = 0;
						amount++;
					}
			       
				}
				
				if(is_prime(n) == true)
				{
					gdImageSetPixel(image, x, y, black);
				}
				else
				{
					gdImageSetPixel(image, x, y, white);
				}

				printf("%d (%d, %d) by %d with direction %d\n", n, x, y, amount, dir);
			}
			
			fp = fopen("output.png", "w+");
			gdImagePng(image, fp);
		}
		else
		{
		
		}
	}
	else
	{
		
	}
}

[/php]

---

### Post by Ferrat on 2008-10-27
Well the code is ugly as hell I know but hey it works ;P 

C++, drawing with SDL, you get to enter how many numbers you want to check/draw etc, any questions just ask :P

needs to be started via terminal so you can enter how many numbers to use (current window can handle up to ~85'000 before pixels starts going outside the viewport).

There, made the first version to simple so it got messed up on higher numbers :) now it should be A-OK \\:D/

---

### Post by Xavieran on 2008-10-27
I'll use the python's curses library.

OP: I'm sure ruby has a curses library to control exactly where text is output, or you could use spaces and tabs...

---

### Post by tom66 on 2008-10-27
GD. I got it to 5,001 x 5,001 pixels or 25,010,001 pixels (yes, 25 megapixels). A 2.6 MB PNG image. Took about 2 minutes to generate...!

Attached are the files. You'll need to install libgd-dev (sudo apt-get install libgd-dev then select the version with XPM - you don't have to, but you might as well have XPM in case you need it), I've provided a pre-compiled version for your viewing pleasure, but you'll still need libgd. 

You can see some of the graphics here (it is not recommended you open them with your web browser): [http://www.tgohome.com/ulam](http://www.tgohome.com/ulam)

It is run from the command-line. First parameter is width (same value is used for height), second is start point, third is mode (supports primes, semiprimes and squares - should be a number 1, 2 or 3 respectively) Primes is the only one which produces something pretty. Width/height must be odd.

Thanks to PandaGoat for helping me out.

---

### Post by alberto ferreira on 2008-10-27
Looking very cool guys! Wish I could do that...hopefully one day i'll get there :)

@tom66:I generate the image but all i see is a blank canvas with no dots. I have installed libgd with xpm and I ran:
> ./ulam 555/555 1 primes
:s:(

I'd like to see more people trying the challenge :D

---

### Post by tom66 on 2008-10-27
Try this:

```

./ulam 555 1 1

```

First parameter should only be a single number, as it only supports squares at the moment.

Second parameter is where to start at. Make this zero for a default spiral.

Third parameter is a number, where 1=primes, 2=semiprimes and 3=squares.

---

### Post by alberto ferreira on 2008-10-27
It works!!! Awesome!! :D and it's really fast!

---

### Post by MaxIBoy on 2008-10-27
This Python code runs until it errors out. However, you can see it draw the spiral in realtime.
```
from time import *

#setup grid:
grid = []
width = input("width of your terminal window: ", )-1
height = input("lines in your terminal window: ", )-1
for i in range(height): #lines
    temp = []
    for j in range(width): #columns
        temp += [False]
    grid += [temp]


def printGrid(grid):
    toPrint = ""
    for i in grid:
        templine = ""
        for j in i:
            if j:
                templine += "*"
            else:
                templine += " "
        toPrint += templine
        toPrint += '\n'
    print toPrint


def isPrime(num):
    temp = float(num-1)
    num = float(num)
    while temp > 1:
        if num/temp == int(num/temp):
            return False
        temp -= 1
    return True
        

#setup the spiral
#lower number is further left and highter number is further right
furthestLeft = furthestRight = currentHoriz = width/2+1

#remember that a lower number means higher up and so on
currentVert = furthestDown = furthestUp = height/2+1


currentDirect = 'r'

#get input of first number:
count = input("enter starting number: ", )

printGrid(grid)
grid[currentVert][currentHoriz] = isPrime(count) #start it off
currentHoriz += 1

#I have no idea what corner the spiral will end at, nor do I currently care
while 1:
    
    grid[currentVert][currentHoriz] = isPrime(count)

    count += 1



    #setup the coordinates of the next part of the spiral
    if currentDirect == 'r':
        currentHoriz += 1

    if currentDirect == 'l':
        currentHoriz -= 1

    if currentDirect == 'u':
        currentVert -= 1

    if currentDirect == 'd':
        currentVert += 1

    if currentHoriz > furthestRight:
        currentDirect = 'u'
        furthestRight = currentHoriz

    if currentHoriz < furthestLeft:
        currentDirect = 'd'
        furthestLeft = currentHoriz

    if currentVert > furthestDown:
        currentDirect = 'r'
        furthestDown = currentVert

    if currentVert < furthestUp:
        currentDirect = 'l'
        furthestUp = currentVert



    sleep (0.02)
    printGrid(grid)
    

```

---

### Post by ashmew2 on 2008-10-27
Im not really a programmer ( but i hope to be one atleast)..but i'd like to say that Ulam did something which ive been considering impossible for about 7 years ( since i know about primes) lol...

Nice work Ulam!

---

### Post by MaxIBoy on 2008-10-27
It's not really a pattern, not really. But it's as close as you can get.

---

### Post by tom66 on 2008-10-27
To see if you've reached the end, iterate until n is size squared, e.g. 'while n < (size * size);'

---

### Post by MaxIBoy on 2008-10-27
Not if the user input is used as the starting number...

---

### Post by tom66 on 2008-10-27
Same formula, but subtract the starting number from n.

---

### Post by MaxIBoy on 2008-10-27
Yeah, I was just being difficult. :)

I didn't consider it important enough to fix, as the program works just as well even with the error.

---

### Post by alberto ferreira on 2008-10-27
Definitely ashmew2 though I'm still waiting for more entries.

MaxIBoy, what is that trophy thing? I've registered as Phobia but there's no account called trophy. Anyways, I'll see how your solution works because I'm still trying to do my own in python.

---

### Post by MaxIBoy on 2008-10-27
(The trophy is in a *thread*, and the *thread* is in an *admin-only* forum. I didn't say it would be easy.)


Anyway, my solution works pretty well, although the flickering is a little annoying (and gets worse as you increase the size of the grid.)

---

### Post by alberto ferreira on 2008-10-27
So I have to hack the site?

---

### Post by MaxIBoy on 2008-10-27
EDIT: Oh, I see what you're referring to.

I do not condone the cracking-open of Invsion's servers. 


So far, it's impossible to get the trophy. I'm going to add more steps to get there, but that's not yet finished. Rest assured, it will eventually be possible to get *without* breaking the law.

---

### Post by Xavieran on 2008-10-28
Here's my (rather limited) solution.

I've used curses, and an abstraction of a pixel...(oooh... ;) )

I borrowed the prime calculating algorithm from MaxIBoy (hope you don't mind...).

It's pretty limited because a terminal has a low resolution...
I'll try and work on something with a matrice instead of a curses screen...

---

### Post by MaxIBoy on 2008-10-28
No problem. 

I also just realized you can double the performance of the prime algorithm by using ```
temp = int(num/2)+1.0
``` instead.

---

### Post by PandaGoat on 2008-10-28
I don't mean to sound snobby, but I believe I implemented a better way to check if a number is prime.  Surely python has the modulus operator.

Anyway, moreover, you can just check from 2 to sqrt(number) to check if its prime.

[The post under me has the best method to check if a number is prime]

---

### Post by cb951303 on 2008-10-28
my entry
didn't test it much but it seems like working
[php]
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <math.h>
#include <gd.h>

bool isPrime(int x)
{
    double sqrtX = sqrt(x);

    // Few exceptions
    switch(x)
    {
        case 1:
            return false;
            break;

        case 2:
            return true;
            break;
    }

    // If number is not even search for odd divisors
    if(x % 2)
    {
        for(int i = 3; i <= sqrtX; i += 2)
            if(!(x % i))
                return false;

        return true;
    }

    return false;
}

int **createSpiral(int gridSize, int startingNumber)
{
    enum _dir { east, north, west, south };
    int **spiral;
    int steps     = 1;
    int direction = east;
    int number    = startingNumber;
    int currentY  = gridSize / 2;
    int currentX  = gridSize % 2 ? currentY : currentY - 1;

    // Create a 2D array for spiral
    spiral = (int**)calloc(gridSize, sizeof(int*));
    if(!spiral)
    {
        fprintf(stderr, "Memory allocation error!\n");
        exit(1);
    }

    for(int i = 0; i < gridSize; i++)
    {
        spiral[i] = (int*)calloc(gridSize, sizeof(int));
        if(!spiral[i])
        {
            fprintf(stderr, "Memory allocation error!\n");
            exit(1);
        }
    }

    // Set starting point's value
    spiral[currentY][currentX] = isPrime(number++);

    // Build the spiral
    for(int y = 1; y < gridSize * 2; y++)
    {
        switch(direction)
        {
            case east:
                // Go 'steps' times east and set values
                for(int j = 0; j < steps; j++)
                    spiral[currentY][++currentX] = isPrime(number++);

                // Set new direction
                direction = north;
                break;

            case north:
                // Go 'steps' times north and set values
                for(int k = 0; k < steps; k++)
                    spiral[--currentY][currentX] = isPrime(number++);

                // Set new direction
                direction = west;
                break;

            case west:
                // Go 'steps' times west and set values
                for(int l = 0; l < steps; l++)
                    spiral[currentY][--currentX] = isPrime(number++);

                // Set new direction
                direction = south;
                break;

            case south:
                // Go 'steps' times south and set values
                for(int m = 0; m < steps; m++)
                    spiral[++currentY][currentX] = isPrime(number++);

                // Set new direction
                direction = east;
                break;
        }

        // Increment 'steps' every 2 changes in direction
        // We need to stop incrementing 'steps' at the final turn
        if(!(y % 2))
            if(steps + 1 < gridSize)
                steps++;
    }

    return spiral;
}

void destroySpiral(int **spiral, int gridSize)
{
    for(int i = 0; i < gridSize; i++)
        free(spiral[i]);
    free(spiral);
}

void spiralToConsole(int **spiral, int gridSize)
{
    // Echo spiral to stdout
    for(int i = 0; i < gridSize; i++)
    {
        for(int j = 0; j < gridSize; j++)
            fprintf(stdout, "%c", spiral[i][j] ? '.' : ' ');

        fprintf(stdout, "\n");
    }
}

void spiralToImage(int **spiral, int gridSize, char *fileName)
{
    FILE *imageFile;
    gdImagePtr spiralImage;
    int black;
    int white;

    // Create a new image
    spiralImage = gdImageCreate(gridSize, gridSize);
    white = gdImageColorAllocate(spiralImage, 255, 255, 255);
    black = gdImageColorAllocate(spiralImage, 0, 0, 0);

    // Prepare image data
    for(int i = 0; i < gridSize; i++)
        for(int j = 0; j < gridSize; j++)
            if(spiral[j][i])
                gdImageSetPixel(spiralImage, i, j, black);

    // Write image data to the file
    imageFile = fopen(fileName, "wb");
    if(!imageFile)
    {
        fprintf(stderr, "Cannot create PNG file!\n");
        exit(1);
    }

    gdImagePng(spiralImage, imageFile);

    // Clean
    fclose(imageFile);
    gdImageDestroy(spiralImage);
}

int main(int argc, char *argv[])
{
    // Get arguments
    if(argc != 4)
    {
        fprintf(stderr, "Usage: ./ulam [GRID_SIZE] [STARTING_NUMBER] [IMAGE_NAME]\n");
        exit(1);
    }

    int gridSize       = atoi(argv[1]);
    int startingNumber = atoi(argv[2]);
    char *fileName     = argv[3];
    int **newSpiral    = createSpiral(gridSize, startingNumber);

    // Output to image and console
    spiralToImage(newSpiral, gridSize, fileName);
    spiralToConsole(newSpiral, gridSize);

    // Clean
    destroySpiral(newSpiral, gridSize);

    return 0;
}[/php]
```

linux:~/Desktop$ gcc -o ulam main.c -lgd -lpng -lz -lm --std=c99
linux:~/Desktop$ ./ulam 5000 1 5000.png > 5000.txt
```

UPDATE:
*Added output to image and tested it with 5000x5000 just to make sure that there isn't any mysterious pattern :lol: You need libgd2-dev to compile. Output file and image are here: [http://www.MegaShare.com/514539](http://www.MegaShare.com/514539)
*Removed 4 unnecessary conditionals that left from before implementing output to png.

---

### Post by MaxIBoy on 2008-10-28
Of course Python has modulus. But I wasn't particularly focused on that part of the algorithm. This was a create-an-Ulmam-spiral thread, not a check-if-a-number-is-prime thread.


So what if I noticed a performance tweak for the prime number checker? It was only a few characters different. I wasn't *searching* for it.

---

### Post by alberto ferreira on 2008-10-28
For greater spirals this method of finding prime numbers seems to be much quicker but I don't have any clue about implementing it. It's called AKS method:
[http://wikislice.webaroo.com/external/AKS_primality_test?wikitrail=Primality%20tests,Prime%20numbers](http://wikislice.webaroo.com/external/AKS_primality_test?wikitrail=Primality%20tests,Prime%20numbers)

MaxIBoy is right, people shouldn't have to be concerned about finding a fast method to test if a number is prime unless they want to,so I suggest this method for simplicity purposes(it was modified from MaxIBoy's for speed and it's extremely fast taking only 15 miliseconds to say if number 611953 is prime - and it is! (this is good because the worst case scenario is a prime(more numbers have to be checked))):
[COLOR=Red]This is for python:[/COLOR]
[php]#the next two lines are optional, they speed up the program considerably but you must have python-psyco installed (it's less than 1MB download so... DO IT!! :D)
import psyco
psyco.full()
from math import sqrt
def is_prime(num):
    if num % 2 == 0:
       return False
    temp = int(sqrt(num)+1)
    #num = int(num) #this is to error-check float numbers
    while temp > 1:
        if num % temp == 0:
            return False
        temp -= 1
    return True[/php]

You are welcomed to use this algorithm in your program.

---

### Post by MaxIBoy on 2008-10-29
Did you try it without the psycho lines? 

I know that particular method would be faster than mine, but 15 milliseconds seems a little far beyond belief.

---

### Post by alberto ferreira on 2008-10-30
My specs:
AMD Opteron 146 2.0GHz >> overclocked at 2.85GHz
2GBs of RAM DDR at 200MHz

Ok, I miscounted it wasn't miliseconds but it was 15 hundred parts of a second, I don't know how it's called but see for yourself: <<Look at the image>>

As you can see, first I ran it WITH psyco and it took 0.014s then WITHOUT it and it took 0.010s. It was faster without psyco maybe due to calling the module but for bigger numbers psyco makes it faster.

---

### Post by MaxIBoy on 2008-10-30
That makes sense.

---

### Post by DaymItzJack on 2008-10-31
Python?

[php]from Tkinter import *
from math import sqrt

h = 700
w = 700
def drawSpiral():
    count = 1
    turns = 0
    goto = 1
    direction = 1
    x = w/2
    y = h/2
    
    drawPixel(x, y, 'red')
    
    while count < 100000:
        if goto == 0:
            turns += 1
            
            direction += 1
            if direction == 5:
                direction = 1
                
            goto = (turns/2 + 1)
        
        if direction == 1:   # Right
            x += 2
        elif direction == 2: # Up
            y -= 2
        elif direction == 3: # Left
            x -= 2
        else:                # Down
            y += 2
        
        if isPrime(count):
            drawPixel(x, y)
        
        goto -= 1
        count += 1

def drawPixel(x, y, c='white'):
    canvas.create_rectangle(x-1, y-1, x+1, y+1, fill=c)

def isPrime(num):
    if num % 2 == 0: return (num==2)
    if num % 3 == 0: return (num==3)
    if num % 5 == 0: return (num==5)
    if num % 7 == 0: return (num==7)
  
    limit = int(sqrt(num))
    for i in xrange(11, limit, 30):
      if num % i == 0:        return False
      if num % (i + 2)  == 0: return False
      if num % (i + 6)  == 0: return False
      if num % (i + 8)  == 0: return False
      if num % (i + 12) == 0: return False
      if num % (i + 18) == 0: return False
      if num % (i + 20) == 0: return False
      if num % (i + 26) == 0: return False
    
    return True

root = Tk()

canvas = Canvas(root, height=h, width=w, bg='black')
canvas.pack()

drawSpiral()

root.mainloop()[/php]

---

### Post by MaxIBoy on 2008-10-31
Dear DaymItzJack,
[INDENT]
I regret to inform you that you tried too hard.
> **alberto ferreira said:**
> 
_[SIZE=3]**Challenge:**[/SIZE]_
 Generate an Ulam Spiral that gets printed in a **terminal or outputted to a file**. Use dots to represent the prime numbers.

The output format is what you wish it to be as long as the graph doesn't lose proportions or become distorted or is too small (thus becoming hard to read)  as the objective is to use the drawing for mathematical studies.

[/INDENT]
-Max

---

### Post by DaymItzJack on 2008-10-31
> Rules:
- Post the source code
- Post the result (screenshot, file, etecetera)

Also, I didn't try too hard if I didn't have to try at all. Actually, my way is probably easier than trying to get the spacing right in a terminal or text file.

---

### Post by Bichromat on 2008-10-31
When you only test odd numbers* you get a denser spiral which has some interesting features too.

*instead of testing the primality of:
```

5 4 3
6 1 2
7 8 9

```

test:
```

9  7  5
11 1  3
13 15 17

```

---

### Post by jimi_hendrix on 2008-10-31
this challenge reminds me of the book *Sphere* by Micheal Crichton...this one alien communicated by giving a number corresponding to a key on the keybord radiatinf from h where 1 is h, 2 is j (if i remember) 3 is n...etc...</ot>

---

### Post by steveydoteu on 2008-10-31
**DaymItzJack **what is your wallpaper? May I have the file please?

---

### Post by alberto ferreira on 2008-10-31
Is there a way to save [DaymItzJack]("http://ubuntuforums.org/member.php?u=273097")'s drawing into a file? - Is there a function in Tkinter or in other library that allows one to save the content of a window into a file?

@[Bichromat]("http://ubuntuforums.org/member.php?u=575481"): Interesting observation :p.

---

### Post by pp. on 2008-10-31
> **DaymItzJack said:**
> Python?

The preview version of your screenshot gives some interesting artifacts. On my screen it is shown as an array of smallish squares, each one containing some cloud or bird dropping shaped squiggle.

---

### Post by DaymItzJack on 2008-10-31
> **alberto ferreira said:**
> Is there a way to save [DaymItzJack]("http://ubuntuforums.org/member.php?u=273097")'s drawing into a file? - Is there a function in Tkinter or in other library that allows one to save the content of a window into a file?

I could just crop the screenshot.

> **steveydoteu said:**
> **DaymItzJack **what is your wallpaper? May I have the file please?

It's a picture from a friend's eye, so I'd rather not, but I can post a screenshot I guess?

---

### Post by alberto ferreira on 2008-10-31
> I could just crop the screenshot.
But that would distort the image :(

---

### Post by DaymItzJack on 2008-10-31
> **alberto ferreira said:**
> But that would distort the image :(

Cropping doesn't distort, resizing does.

[php]import Image
from math import sqrt

h = 700
w = 700
img = Image.new('RGBA', (w, h), (0, 0, 0))

def drawSpiral():
    count = 2
    turns = 0
    goto = 1
    direction = 1
    x = w/2
    y = h/2
    
    img.putpixel((x, y), (255, 0, 0))
    
    while count < 100000:
        if goto == 0:
            turns += 1
            
            direction += 1
            if direction == 5:
                direction = 1
                
            goto = (turns/2 + 1)
        
        if direction == 1:   # Right
            x += 2
        elif direction == 2: # Up
            y -= 2
        elif direction == 3: # Left
            x -= 2
        else:                # Down
            y += 2
        
        if isPrime(count):
            img.putpixel((x, y), (255, 255, 255))
        
        goto -= 1
        count += 1
        
def isPrime(num):
    if num % 2 == 0: return (num==2)
    if num % 3 == 0: return (num==3)
    if num % 5 == 0: return (num==5)
    if num % 7 == 0: return (num==7)
  
    limit = int(sqrt(num))
    for i in xrange(11, limit, 30):
      if num % i == 0:        return False
      if num % (i + 2)  == 0: return False
      if num % (i + 6)  == 0: return False
      if num % (i + 8)  == 0: return False
      if num % (i + 12) == 0: return False
      if num % (i + 18) == 0: return False
      if num % (i + 20) == 0: return False
      if num % (i + 26) == 0: return False
    
    return True
    
drawSpiral()
img.save("ulam.png")[/php]

This will draw the pixels directly to an image and save the file as "ulam.png"

---

### Post by elbarto_87 on 2008-11-01
This is my attempt in python, I have wrapped PHP tags on my code so it would have color as the normal code tag came up black only? 

As mentioned before the scaling is out as I have tried to export the data to a text document. The dots still appear to line up along the diagonal but there are still a bit off. I tried to print " . " instead of "." to get the scaling better but the file turned up empty then. I suspect it is an issue with using the numpy array class? 

If someone could have a look at my script and give me some pointers on how to export text a little better that would be great. I am pretty happy with the code up until I start making the new array "B", then it gets a little messy. This is one of my first attempts of writing such a script in python so as much feedback/criticism as possible would be appreciated.

change the variable num_c for a bigger array. its currently set to 101x101 which takes ~3 seconds to calculate and write on my pc.  



[PHP]from numpy import *
import time
start = time.clock()
num_c = 101 #make spiral size = num_c**2
#Note: num_c must be odd
A = zeros((num_c,num_c), int)
mid_ = int(num_c-ceil(num_c/2)-1)
n = mid_
m = mid_

num = 1 # start spriral off at 1
A[n,m] = num # set the centre position to 1

for x in range(1,num_c,2):

    #Right
    num += 1       #at the start of each block
    m += 1         #move one position
    A[n,m] = num   # to the right

    #Up
    for i in range(1,x+1):
        num += 1 
        n = n-1
        A[n,m] = num

    #Left
    for j in range(1,x+2):
        num += 1 
        m = m-1
        A[n,m] = num    

    #Down
    for k in range(1,x+2):
        num += 1 
        n = n+1
        A[n,m] = num     

    #Right
    for l in range(1,x+2):
        num += 1 
        m = m+1
        A[n,m] = num


def testodd(num):
#http://ubuntuforums.org/showthread.php?t=940561&highlight=test+odd
    if num < 2:
            return 0
    else:
            for div in range(2, (num/2)+1):
                    if num%div==0:
                            return 0
            else:
                    return 1
        

B = zeros((num_c,num_c), str)#make a string array
for n in range(0,num_c):
    for m in range(0,num_c):
        if testodd(A[n,m])==1:
              B[n,m] = "."#array does not work when adjusting these ie " . "
        else:
              B[n,m]= " "#"   "

print A


f = open("ulum_spiral.txt", "w")

for m in range(0,num_c):
    st = ''
    for n in range(0,num_c):
        st = st + B[m,n]
    f.writelines(st + '\n')
f.close()
print '\n Runtime = ', (time.clock()-start), ' seconds'[/PHP]

Regards Elbarto

---

### Post by Xavieran on 2008-11-09
I've translated my python script into php, you can find it at this web address...

[http://xavieran.com/ulam_form.html]("http://xavieran.com/ulam_form.html")

:D :D

---

### Post by alberto ferreira on 2008-11-13
Elbato, I'd like to help but I know nothing about arrays.

I'm basing my algorithm in [DaymItzJack]("http://ubuntuforums.org/member.php?u=273097")'s

This is python:
[php]from Tkinter import *
from math import sqrt
import psyco
psyco.full()

#User customization
h = 500
w = h
size = 1
start=1

#Variables
x = w/2
y = h/2
path_size = 2 * size
side=1
counter=0
dir=1
number=start

#Functions
def drawPixel(x, y, c='white'):
    canvas.create_rectangle(x-size, y-size, x+size, y+size, fill=c)
def isPrime(n):
    if n % 2 == 0:
       return False
    p = int(sqrt(n)+1)
    while p > 1:
        if n % p == 0:
            return False
        p -= 1
    return True  
def move(dir):
#Directions: 1-Up, 2-Left, 3-Down, 4-Right
    global y,x,path_size,counter,number
    if dir == 1:y += path_size
    if dir == 2:x -= path_size
    if dir == 3:y -= path_size
    if dir == 4:x += path_size
    counter += 1
    number += 1
def change_direction(d):
    global side,counter,dir
    if dir == 4:dir = 1
    else:
        dir += 1
    counter = 0
    side += 1
def drawSpiral():
    while x < w or y < h:
        while counter < side:
            move(dir)
            if isPrime(number): drawPixel(x,y,'white')
        change_direction(dir)
    


#Rendering
root = Tk()
canvas = Canvas(root, height=h, width=w, bg='black')
canvas.pack()
drawSpiral()
root.mainloop()

[/php]

My drawing seems awkward, any suggestions ?

---

### Post by akari no ryu on 2008-12-09
This is my solution. It is perhaps not the most efficient C++ solution possible, but I'm a PHP developer by trade not a C++ developper.
I know basic C so I'm just using what I know.

[php]
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <Magick++.h>
#include <vector>
#include <iostream>
using namespace std;
using namespace Magick;

bool isPrime(int aNumber)
{
	// 2 is deemed to be a prime whereas 1 is deemed not to be
	if(aNumber == 2) return true;
	if(aNumber == 1) return false;
	// this is the simplest calculation. All non 2 even numbers are not prime
	if(aNumber % 2 == 0) return false;
	
	// determine whether there is a factor.
	// start from 2 and increment, if aNumber divided by i has no modulus, it has a factor
	int root = (int)(ceil(sqrt(aNumber)));
	int i; i = 3;
	bool hasFactor; hasFactor = false;
	
	while(i <= root && !hasFactor)
	{
		if (aNumber % i == 0) hasFactor = true;
		i += 2;
	}
	
	if(hasFactor) return false;
	return true;
}

int main( int argc, char *argv[]) 
{
	vector<string> args(argv, argc+argv);
	
	if(args.size() != 4)
	{
		cout << "Usage:\n\t./Ulam <start> <depth> <name>\n\t";
		cout << "The start argument represents the number to start the sequence at\n\t";
		cout << "The depth argument represents the width of the square array to build for population.\n\t";
		cout << "The depth argument must be an odd number for the script to work properly.\n";
		cout << "The program will generate a <depth>x<depth> image in the Ulam spiral.\n";
		cout << "This script is licenced under the GPL and is copyright of Eamonn Kearns 2008";
		return 0;
	}
	
	// convert the argument to an integer and ensure it's not divisible by 2
	int s = atoi(args[1].c_str());
	int d = atoi(args[2].c_str());
	string name = args[3];
	if(d % 2 == 0)
	{
		cout << "The depth argument must be odd.\n";
	}
	
	
	cout << "Initialising ImageMagick\n";
	// initialise image magic with what it needs.
	InitializeMagick(argv[0]);
	Image image(Geometry(d, d), "white");
	image.type(TrueColorType);
	image.modifyImage();
	image.magick("png");
	cout << "Done\n";
	
	// for loops
	int i; int j; int lastPercent; int currentLastPercent;
	
	lastPercent = 0; currentLastPercent = 0;
	
	cout << "Initialising data array\n";
	// create an array to hold the Ulam spiral
	int **data;
	data = new int*[d];
	for(i = 0; i < d; i++)
	{
		currentLastPercent = (int)(i * 10 / d) * 10;
		if(currentLastPercent != lastPercent)
		{
			cout << currentLastPercent << "% ";
			lastPercent = currentLastPercent;
		}
		data[i] = new int[d];
	}
	cout << "\nDone\n";
	
	// start the counter at the centre.
	int x; int y;
	x = y = (int)(ceil(d/2));
	
	// this number represents how many integers we're checking.
	// It is the result of squaring the depth argument
	int d2; d2 = d * d;
	
	// an integer to represent the direction
	// 1 is right, 2 is up, 3 is left, 4 is left
	int dir; dir = 1;
	
	// steps
	int steps; steps = 1;
	int changes; changes = 0;
	int xInc; xInc = 1; int yInc; yInc = 0;
	
	i = s; lastPercent = 0; currentLastPercent = 0;
	cout << "Building array\n";
	
	while(i < (d2 + s))
	{
		// go <steps> steps in the current direction
		currentLastPercent = (int)((i - s) *10/ d2) * 10;
		if(currentLastPercent != lastPercent)
		{
			cout << currentLastPercent << "% ";
			lastPercent = currentLastPercent;
		}
		
		for(j = 0; j < steps; j++)
		{
			data[x][y] = isPrime(i) ? 0 : 1;
			x += xInc; y += yInc; i++;
		}
		
		changes++;
		if(changes % 2 == 0) steps++;
		dir ++; if (dir == 5) dir = 1;
		if(dir == 1)
		{
			xInc = 1; yInc = 0;
		}
		else if(dir == 2)
		{
			xInc = 0; yInc = -1;
		}
		else if(dir == 3)
		{
			xInc = -1; yInc = 0;
		}
		else if(dir == 4)
		{
			xInc = 0; yInc = 1;
		}
	}
	cout << "\nDone\n";
	
	lastPercent = 0; currentLastPercent = 0;
	int pixelsDone = 0;
	
	cout << "Getting pixel information";
	Pixels view(image);
	PixelPacket *pixels = view.get(0,0, d, d);
	cout << "Done\n";
	
	cout << "Painting image\n";
	for(i = 0; i < d; i++)
	{
		for(j = 0; j < d; j++)
		{
			*pixels++ = (data[i][j] == 0) ? ColorRGB(0.0, 0.0, 0.0) : ColorRGB(1.0, 1.0, 1.0);
			pixelsDone++;
			currentLastPercent = (int)((pixelsDone * 10)/ (d*d)) * 10;
			if(currentLastPercent != lastPercent)
			{
				cout << currentLastPercent << "% ";
				lastPercent = currentLastPercent;
			}
		}
	}
	cout << "\nDone.\n";
	
	for(i = 0; i < d; i++) delete data[i];
	delete data;
	
	cout << "Writing " << name << ".png\n";
	view.sync();
	image.write(name+".png");
	return 0;
}
[/php]
Sample output
[IMG]http://i297.photobucket.com/albums/mm233/CuAnnan/testNewCount.png[/IMG]

---

