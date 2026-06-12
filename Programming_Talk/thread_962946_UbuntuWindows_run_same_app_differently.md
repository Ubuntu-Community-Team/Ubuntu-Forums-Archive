---
title: "Ubuntu/Windows run same app differently?"
date: 2008-10-29
forum: Programming Talk
---

### Post by Auraomega on 2008-10-29
I've been writing a game in my bordem lately, all coding is in C++ and SDL as they are platform independant.

The code when compiled with MinGW on the PC runs as it is expected, loading the first level, once complete loading the next, etc, until the final level at which point the game closes. On my Ubuntu setup it runs very differently, not all the maps load correctly (although changing the order allows a map that didn't load to load, at the cost of those maps which did load), after completing the final map, the game fails to close just reloads the map instead.

My discription is vague I guess, I've tried running it through a debugger, but theres not much I can deduce from it?

The offending code is this:
```
for(int stage = 1; !quit; stage++)
	{
		finish = 0;
		char stageName[256];
		sprintf(stageName, "%i.map", stage);
		bool level = mapRead(stageName, &xDim, &yDim, map);
		if(!level)
		{
			quit = 1;
			finish = 1;
		}
		else
		{
			drawMap(xDim, yDim, map);
			drawMapActive();
			
			ballX = startX;
			ballY = startY;
		}
		
		while((!quit) && (!finish))
		{
			if(SDL_PollEvent(&event))
			{
				if(event.type == SDL_KEYDOWN)
				{
					switch(event.key.keysym.sym)
					{
						case SDLK_UP:
							moveUp(xDim, yDim, map);
							break;
							
						case SDLK_DOWN:
							moveDown(xDim, yDim, map);
							break;
							
						case SDLK_LEFT:
							moveLeft(xDim, yDim, map);
							break;
							
						case SDLK_RIGHT:
							moveRight(xDim, yDim, map);
							break;
							
						case SDLK_SPACE: //reset map
							ballX = startX;
							ballY = startY;
							break;						
					}
				}
				else if(event.type == SDL_QUIT)
				{
					quit = 1;
				}
			}
			drawMap(xDim, yDim, map);
			drawMapActive();
			//frame++;
			/*if(fps.get_ticks() < 1000/FPS)
			{
				SDL_Delay((1000/FPS) - fps.get_ticks());
			}*/
		}
	}
	
	SDL_FreeSurface(tileSetI);
	SDL_FreeSurface(mapI);

	SDL_Quit();
	return 0;
``` (Is there spoiler tags here? This takes up a fair bit of space)

If the end of level teleport is reached finish becomes true breaking the loop.

If you need the code and map files let me know and I'll upload them to my website, but as I said I believe those are the offending lines of code.

Thanks.
-Aura

---

### Post by curvedinfinity on 2008-10-29
Heya, I bet you it has something to do with the filesystems, because from my experience, that's the biggest difference when porting to/from Windows with SDL.

Make sure you use slashes (/) as opposed to backslashes (\\), and all of your paths don't rely on case-sensitivity (Windows sees "FiLe" and "file" as the same thing).

---

### Post by Auraomega on 2008-10-29
Well all the maps are in the same directory as the game, and the maps are basically 1.map, 2.map, they all load seperately, but just not together.

I have been thinking about my map files though, for simplicity I have made them using hex, not charactors, I doubt this makes any difference as I am opening the file in read-binary mode, is there anything that fgetc might miss in Ubuntu but not in Windows? (I'm just thinking like scanf missing spaces, etc).

-Aura

---

### Post by curvedinfinity on 2008-10-29
Hmmm ... how specifically do the map loads fudge on Ubuntu?

---

### Post by Auraomega on 2008-10-29
I have 3 maps currently, originally 1, 2 and 3 in order of complexity. Map 1 and map 2 would load fine, but after completeing map 2 it just kept reloading it.

After changing the order (by renaming files), the 3rd map now being map 1, and map 1 being map 2, map 2 being map 3. Map 1 loads but goes into the same loop, had no luck loading the other maps. All the maps work I guess, I just can't understand whats going on. I even flush the array every map load to make sure nothing gets crossed over. If any part of the map fails to load then it returns an error and quit activates, so the maps must be loading correctly. I'd go so far as to say the error must be in the for loop, but I can't understand how thats so...

-Aura

---

### Post by curvedinfinity on 2008-10-29
Can you post mapRead?

---

### Post by Auraomega on 2008-10-29
```
/**
  * NOTES:
  *
  *
  *
  * TODO:
  *
  *
  *
  * FIX:
  *
  *
  *
**/

#include <stdio.h>
#include <stdlib.h>

void flushArray(char* array)
{
	int arraySize = 0;
	arraySize = sizeof(array);
	for(int loop = 0; loop < arraySize; loop++)
	{
		array[loop] = 0;
	}
}

bool mapRead(char* fileName, int* xDim, int* yDim, int* map)
{
	FILE* mapFile;
	
	flushArray((char*)map);
	
	mapFile = fopen(fileName, "rb");
	if(!mapFile)
	{
		return 0;
	}
	
	fscanf(mapFile, "%ix%i", xDim, yDim);
	
	{
		int c = 0;
		int loop = 0;
		do
		{
			c = fgetc(mapFile);
			map[loop] = c;
			loop++;
		}while(c != EOF);
		
		map[loop - 1] = 0;
	}

	fclose(mapFile);
	if((*xDim > 48) || (*yDim > 27))
	{
		xDim = yDim = 0;
		return 0;
	}
	else
	{
		return 1;
	}
}

```

I've put the entire source file on there, as it runs the flush array too and you may want to check that.

-Aura

---

### Post by curvedinfinity on 2008-10-29
One thing I noticed:

In flushArray, sizeof(array) will always return 4, because that's the size of a char pointer. Just store the length of that array, and pass it around that way. I'll tell you if I notice anything else, because that doesn't seem like a show stopper.

---

### Post by curvedinfinity on 2008-10-29
Oh, that's what it is.
```

if(!level)
{
	quit = 1;
	finish = 1;
}

```

should be

```

if(!level)
{
	quit = 0;
	finish = 0;
}

```

right?

Edit: no. hehe.

---

### Post by Auraomega on 2008-10-29
Changed that, its now 48*27, although I have two issues with doing so:
1) Because I'm casting an int to a char, the size goes from 2 bytes to 1 byte, so surely I should do 48*27*2? I could test but I might not know if a buffer overflow is caused until I get more into this, by which point I might end up forgetting I did it...
2) I was trying to find a universal way of doing that, but I'm not 100% sure on pointers at the moment (I forgot my old logical way of doing it a few months back). Should I be doing sizeof(array), or sizeof(&array)?

Oh, and you were right, its not the actual problem, but handy to get sorted I guess.

-Aura

---

### Post by curvedinfinity on 2008-10-29
An int is four bytes, actually. -- (well, it actually depends on the platform, but for you, its probably 4)

sizeof only tells you the length of the datatype ... not the actual data. So, since a pointer is the size of a platform's memory address, in your case, probably 32 bits, a pointer is four bytes long. The way you figure out the size of an array of binary data is by storing the size when you make it in the first place, and passing that number around. :)

---

### Post by Auraomega on 2008-10-29
Well you learn something new every day :D

Sorry, most, if not all my knowledge comes from programming on the PSP, and obviously the hardware never altered so I thought these things were always constants and not hardware/OS dependent

-Aura

---

### Post by Ferrat on 2008-10-29
If you're not sure of how many bytes on a specific system that the variables are going to use, just run something easy like this 

```

#include <iostream> 
using namespace std;

	int main()
{
	cout << "Size of int:\t" << sizeof(int) << " byte.\n";
	cout << "Size of short:\t" << sizeof(short) << " byte.\n";
	cout << "Size of long:\t" << sizeof(long) << " byte.\n";
	cout << "Size of char:\t" << sizeof(char) << " byte.\n";
	cout << "Size of float:\t" << sizeof(float) << " byte.\n";
	cout << "Size of double:\t" << sizeof(double) << " byte.\n";

	return 0;
}


```

---

### Post by Auraomega on 2008-10-30
Ok, thanks for that it seems a pretty sensible way of going about checking.

Seeing as we've still not found the cause of whats going on I've uploaded the source code to Mediafire (I forgot my FTP password for my site >.>), the code is [here]("http://www.mediafire.com/?h1wnmxjzqmj"). Its not the prettiest, I've not gone through and tidied it or anything. I've also included the 3 map files plus the tileset.

I can't remember if I put the right makefile in or the makefile which includes -lmingw32, just remove if its that one.

-Aura

---

