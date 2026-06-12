---
title: "Segmentation fault (Core Dumped) SDL"
date: 2014-01-29
forum: Programming Talk
---

### Post by Ben_Miled_Walid on 2014-01-29
HI all. I'm new in coding so i was trying to show an picture with SDL 1.2 in ubuntu
so this is my code

```
#include<stdio.h>
#include<SDL/SDL.h>
#include<stdlib.h>
void pause()
{
    int continuer=1;
    SDL_Event event;

    while (continuer)
    {
        SDL_WaitEvent(&event);
        switch(event.type)
       {            case SDL_QUIT:
                continuer=0;
        }
    }
}

int main()
{
SDL_Surface *ecran=NULL , *image=NULL;
SDL_Init(SDL_INIT_VIDEO);
SDL_Rect pos;
pos.x=0;
pos.y=0;
ecran=SDL_SetVideoMode(850,600,32,SDL_HWSURFACE);
image=SDL_LoadBMP("chat.bmp");
SDL_BlitSurface(image,NULL,ecran,&pos);
SDL_Flip(ecran);
pause();
SDL_Quit();
SDL_FreeSurface(image);
return EXIT_SUCCESS;
}
```


and this is my terminal

walid@walid-SATELLITE-P870:~/Bureau$ gcc image.c -o prog -lSDL
walid@walid-SATELLITE-P870:~/Bureau$ ./pro
bash: ./pro: No such file or directory
walid@walid-SATELLITE-P870:~/Bureau$ ./prog
Segmentation fault (core dumped)
walid@walid-SATELLITE-P870:~/Bureau$ gdb prog
GNU gdb (GDB) 7.6.1-ubuntu
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/walid/Bureau/prog...(no debugging symbols found)...done.
(gdb) run
Starting program: /home/walid/Bureau/prog 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
SDL_Flip (screen=0x0) at ./src/video/SDL_video.c:1096
1096    ./src/video/SDL_video.c: No such file or directory.
(gdb) quit

can you please help me ( it works on other computers )
Thank you

---

### Post by spjackson on 2014-01-29
My first guess is that either ecran or more likely image is a null pointer (e.g. it can't find chat.bmp or there isn't support for .bmp files). You could also try building your program for debug (with -g) and trying "bt" for backtrace after the SIGSEGV has occurred.

---

### Post by ofnuts on 2014-01-30
A possibility is that you are asking for a video mode that is not supported on that specific computer so that the "ecran" variable is not set (your code is not checking for the NULL that 
SDL_SetVideoMode returns when it cannot set the request mode).

---

