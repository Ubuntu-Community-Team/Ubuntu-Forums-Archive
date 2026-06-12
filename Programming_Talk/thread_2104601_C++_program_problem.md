---
title: "C++ program problem"
date: 2013-01-13
forum: Programming Talk
---

### Post by linuxonbute on 2013-01-13
I am trying to make a simple oscilloscope but I am new to c programming and am trying to use C++ and SDL ( which I have not used before ) to slowly build the program.
I started off just using rand() to generate a value to plot. I had a for loop and managed to get a simple display to work.
Since then I have bought a USB to bi-directional parallel port lead.
I read up about setting the data pins to input with a view to hooking up an ADC and controlling it. 
Now I have not got the ADC board set up yet but have a strange problem with the lead plugged in.
Here is my code:
```

/* *Modified from : * Professional Linux Programming - SDL image test *  compile with:
 *  g++ -o newstuff2 newstuff2.cpp  `pkg-config --cflags --libs sdl` *  you will need the SDL library files on your system to compile it * */
#include <stdio.h>
#include <SDL/SDL.h>
#include <string.h>  /* String function definitions */
#include <unistd.h>  /* UNIX standard function definitions */
#include <fcntl.h>   /* File control definitions */
#include <errno.h>   /* Error number definitions */
#include <termios.h> /* POSIX terminal control definitions */
#include <sys/types.h>
#include <sys/stat.h>
#include <time.h>
#include <stdlib.h>
#include <sys/io.h>

#define FALSE 0
#define TRUE 1

//#define BASEPORT 0x3bc /* lpo */
#define BASEPORT 0x378 /* lp1 */

volatile int STOP=FALSE; 
int fd;
ssize_t size = 9;
fd_set input_fdset;
int mybuf[1010];
int itter=1;

int main(int argc, char **argv)
{
   SDL_Surface *screen, *image1, *image2, *image6;
   SDL_Rect location1, location2;
   int delay = 4;
   int j = 0;
   int tes;
   int store;
   int change;
   int dport;
   int tem;
   if (ioperm(BASEPORT, 3, 1)) {perror("ioperm"); exit(1);}
	
   tem = fcntl(0, F_GETFL, 0);
   fcntl (0, F_SETFL, (tem | O_NDELAY));
   dport= inb(BASEPORT + 2);
   outb(dport && 32, BASEPORT + 2);

   if (SDL_Init(SDL_INIT_VIDEO) < 0)
   {
      perror("SDLInit");
      return 1;
   }
   printf("SDL initialized.\n");

   screen = SDL_SetVideoMode(1200, 600, 0, 0);
   if (screen == NULL)
   {
      printf("Problem: %s\n", SDL_GetError());
      return 1;
   }

printf("Video mode set.\n");

   SDL_WM_SetCaption("Scope Sim", "testing");
   image1 = SDL_LoadBMP("image3.bmp");

   if (image1 == NULL)
   {
     printf("Problem: %s\n", SDL_GetError());
      return 1;
   }

   printf("image1 loaded.\n");
  location2.x = 1100;
   location2.y = 250; 
   location2.w = image2->w;
   location2.h = image2->h;

   image2 = SDL_LoadBMP("image5.bmp");
   if (image2 == NULL)
   {
    printf("Problem: %s\n", SDL_GetError());
    return 1;
   }
   printf("image2 loaded.\n");
   if (SDL_BlitSurface(image2, NULL, screen, &location2) < 0)
   {
    printf("Problem: %s\n", SDL_GetError());
    return 1;
   }
   image6 = SDL_LoadBMP("image6.bmp"); 
   if (image6 == NULL)
   {
     printf("Problem: %s\n", SDL_GetError());
      return 1;
   }
   printf("image6 loaded.\n");

   SDL_UpdateRects(screen, 1, &location2);

 
   if (SDL_BlitSurface(image1, NULL, screen, &location1) < 0)
   {
      printf("Problem: %s\n", SDL_GetError());
      return 1;
   }
   SDL_UpdateRects(screen, 1, &location1);
location1.x =1090;

for (j=0; j<=598; j++)
{
location1.y = j;
SDL_BlitSurface(image1, NULL, screen, &location1);
   SDL_UpdateRects(screen, 1, &location1);

} 
srand ( time(NULL)*5 );
for(tes=0; tes<=3; tes++) 
{

location1.x = 1;
if(itter == 1)
{
itter=0;

	printf("%d\n",location1.y);
location1.y=rand() % 580  + 1;
}
if (tes==5 )
{
location1.y-=15;
}
for (j=0; j<=1087; j++)
{
store=location1.y;

location1.y=mybuf[j+1]; 
location1.x +=1;
SDL_BlitSurface(image6, NULL, screen, &location1);
   SDL_UpdateRects(screen, 1, &location1);
location1.y=store;
mybuf[j]=store;

location1.y=inb(BASEPORT);

change=rand() % 580  + 1;
if( location1.x> 500) 
{location1.y=201;}
if( location1.x> 600) 
{location1.y=300;}

mybuf[j]=location1.y;
SDL_BlitSurface(image1, NULL, screen, &location1);
   SDL_UpdateRects(screen, 1, &location1);
SDL_Delay(1);
} 
 SDL_Delay(delay * 2);
}

   SDL_Delay(delay * 200);
   SDL_Quit();
   return 0;
}

```
The problem is that the line 
change=rand() % 580  + 1;
has to be there even though it is not used for anything.
If it's there then the program runs as expected but if it isn't then the the display comes up for a very small fraction of a second.
I set it up to do some variable prints and when it runs I get:
> 
SDL initialized.
Video mode set.
image1 loaded.
image2 loaded.
image6 loaded.
598

But if the change ... line is commented out I get:
> 
SDL initialized.
Video mode set.
image1 loaded.

As I said I am new to this and the code is cobbled together vrom various google searches and I am still trying to understand most of it.
Can someone please have a look at the code and explain why I have this problem please?

---

### Post by trent.josephsen on 2013-01-13
C, C++: pick one. If C++, you should be using <cstdlib>, <ctime>, etc., not <stdlib.h> and <time.h>, and should you persist in using C-style I/O, that would be <cstdio>.

I don't know enough C++ to offer more advice on your actual problem, but you will get better and faster answers if you format your code readably. Use `indent` or something at least, your left margin is all ragged and it's really hard to tell where blocks are supposed to begin and end.

---

### Post by dwhitney67 on 2013-01-13
> **linuxonbute said:**
> 
Can someone please have a look at the code and explain why I have this problem please?

I second the previous post; format your code so that it is easier to read.  Also, flip to a chapter (or section) of your programming tutorial that discusses functions.  That way you can modularize your application to make it easier to troubleshoot issues.

As for the first thing that stuck out in your code was the following:
```

...
   location2.w = image2->w;
   location2.h = image2->h;

   image2 = SDL_LoadBMP("image5.bmp");
...

```
I suppose the computer "gods" allowed the assignments above to succeed.  On a normal day, accessing a pointer (ie image2) that has yet to be initialized should have generated a seg-fault.

---

### Post by linuxonbute on 2013-01-14
Thanks guys,
@trent
 Didn't realize this. I will update the includes and see if that makes a difference.
As I said it was stuff from different google searches. The code was in a file I had created with gedit and it was reasonably formatted there. I just selected it all and did a copy/paste so I guess there was somthing hidden in it which created the problem.

@dwhintey67
Well I do tend to rush into things and have barely looked at my book. About 30 years ago I had an 8 bit z80 computer and did a bit of programming in Mix C and later I had Borland Turbo C  so to say I am a bit rusty is an understatement. Since then I have really only done some php coding and then only at a hobby level. I will look at the pointer assignments too.
[edit]
Moving the pointer assignment down so it was after loading the image cleared up the problem with the unused integer so that resolved it. 
[/edit]
Thanks again guys.

---

