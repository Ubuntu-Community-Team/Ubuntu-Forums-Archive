---
title: "SDL woes."
date: 2008-09-27
forum: Programming Talk
---

### Post by Thesuperchang on 2008-09-27
I think I'm now on my 5th attempt at getting into SDL. Unfortunately it's looking as though it won't be my last crack at it. All I can really say at the moment is, somebody help me please.

I've had experience in Visual Basic and Python where I had graphics going however my algorithm design was not at its best. My favoured programming language is C. I been coding in C for about 7 months now and I feel quite confident in it. I've made programs such as a hex editor, bitmap loader(of course with no display option:confused:), logic gate analyser and other small programs alike.

I've been to this wiki countless times;
[http://gpwiki.org/index.php/C:SDL_tutorials#General](http://gpwiki.org/index.php/C:SDL_tutorials#General)
However I feel like a goat ramming a wall. Nothing in the SDL department seems to want cooperate with me. I'm few error messages away from working with a hammer. Would some one please tell me how I should set up my dev environment (preferably gcc) to work with SDL.

This is the current source I'm trying to run.
However when I execute it, I get this message,
"Unable to initialize SDL: No available video device".
[PHP]#include "include/SDL/SDL.h"

int main(void)
{
	SDL_Surface *screen;

	if (SDL_Init(SDL_INIT_VIDEO) != 0)
	{
		printf("Unable to initialize SDL: %s\n", SDL_GetError());
		return -1;
	}

	while(1)
	{
		screen = SDL_SetVideoMode(640, 480, 16, SDL_DOUBLEBUF | SDL_FULLSCREEN);
		if (screen == NULL)
		{
			printf("Unable to set video mode: %s\n", SDL_GetError());
			return -1;
		}
	}

	SDL_Quit();

	return 0;
}[/PHP]

Thanks in advance,
C. Anderson

---

### Post by Sockerdrickan on 2008-09-27
[php]#include <SDL/SDL.h>

int main(int argc, char **argv) 
{ 
    SDL_Surface *screen; 

    if (SDL_Init(SDL_INIT_VIDEO) != 0) 
    { 
        printf("Unable to initialize SDL: %s\n", SDL_GetError()); 
        return -1; 
    } 

        screen = SDL_SetVideoMode(640, 480, 16, SDL_DOUBLEBUF | SDL_FULLSCREEN); 
        if (!screen) 
        { 
            printf("Unable to set video mode: %s\n", SDL_GetError()); 
            return -1; 
        } 

    SDL_Quit(); 

    return 0; 
} [/php] try this

---

### Post by Mickeysofine1972 on 2008-09-27
You could try the Ubuntu Games Developer Wiki

[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

It has a good stack of articles on SDL including 2d and 3d stuff and its all in C/C++

Mike

---

### Post by Thesuperchang on 2008-09-28
Still no success. I started using X yesterday. It seems to be very complex. But atleast its wokring. Thanks for your help guys.

---

### Post by ankursethi on 2008-09-28
You might want to remove that while(1) loop. This is what happens when you run your program :
1. SDL is initialized, everything works fine.
2. The control goes into the while(1) loop. The screen surface is initialized and memory for it is allocated. Everything still works fine.
3. The while loop continues. It tries to initialize and set up the screen once again. This is where it fails. The allocated screen bounces in and out of existence so quickly that you barely get a chance to see it.

You might want to change the code to this :
```

#include "<SDL/SDL.h>" 

int main(void) 
{ 
    SDL_Surface *screen; 

    if (SDL_Init(SDL_INIT_VIDEO) != 0) 
    { 
        printf("Unable to initialize SDL: %s\n", SDL_GetError()); 
        return -1; 
    } 
 
    screen = SDL_SetVideoMode(640, 480, 16, SDL_DOUBLEBUF | SDL_FULLSCREEN); 
    if (screen == NULL) 
    { 
        printf("Unable to set video mode: %s\n", SDL_GetError()); 
        return -1; 
    }

    getchar() ;
    SDL_Quit(); 

    return 0; 
}   

```

The getchar() makes the program halt for input, so you can see the newly allocated screen. You can hit RETURN or input a character to exit the program.

(NOTE: I haven't compiled this program. I've had a very limited exposure to SDL and what I'm telling you is purely based on what my intuition tells me.)

Also try : [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)
Very nice SDL tutorials.

---

