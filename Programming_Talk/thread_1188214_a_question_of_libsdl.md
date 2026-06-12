---
title: "a question of libsdl"
date: 2009-06-15
forum: Programming Talk
---

### Post by CStick on 2009-06-15
my program generated a surface in a thread , then blit surface to the display surface.
but the program getting crash when calling SDL_BlitSurface
 i don't know why .

```
#include <SDL.h>
#include <SDL_ttf.h>
#include <SDL_thread.h>
SDL_Surface* disp;
TTF_Font* font;
SDL_Thread* thread;
SDL_Surface* text;
int proc( void * parm)
{
    SDL_Color color = {255,255,255};
    text = TTF_RenderText_Solid( font , "abcdefg" , color );
    while(1);    
}
int main()
{
    SDL_Init(SDL_INIT_VIDEO);
    TTF_Init();
    disp = SDL_SetVideoMode(800,600,32,SDL_SWSURFACE);
    font = TTF_OpenFont("font.ttf",15);
    thread = SDL_CreateThread(proc ,NULL );
    while(1)
    {
        if(text)
        {
            SDL_BlitSurface( text , NULL , disp , NULL );
            text = NULL;
        }
    }
    return 0;
}
```

---

### Post by Zugzwang on 2009-06-15
You do not initialize "text" with anything. Probably you should try:
```

SDL_Surface* text = 0;

```

Note that using "valgrind", you would have found this problem yourself!

---

### Post by bhagabhi on 2009-06-15
> You do not initialize "text" with anything.

He does, in the other thread.
I wonder though, if you are allowed to play around with Surfaces like that, or you are forced to create surfaces and do blitting only in the main thread. In that case, make the thread send a signal to the main thread, and do the blitting there.

---

### Post by Zugzwang on 2009-06-15
> **bhagabhi said:**
> He does, in the other thread.

Yes, but it's a typical race-condition: In many cases, the main thread will proceed past the "if(text) {" check before text has been assigned a value in the other thread. In fact, this is not unlikely as "TTF_RenderText_Solid" will take a couple of clock cycles.

---

### Post by MadCow108 on 2009-06-15
> **bhagabhi said:**
> He does, in the other thread.
I wonder though, if you are allowed to play around with Surfaces like that, or you are forced to create surfaces and do blitting only in the main thread. In that case, make the thread send a signal to the main thread, and do the blitting there.

but there's no guarantee that the thread initialises *text* before the main thread tries to access it.

---

### Post by bhagabhi on 2009-06-15
Ah, you are both right.

---

### Post by CStick on 2009-06-15
> **Zugzwang said:**
> Yes, but it's a typical race-condition: In many cases, the main thread will proceed past the "if(text) {" check before text has been assigned a value in the other thread. In fact, this is not unlikely as "TTF_RenderText_Solid" will take a couple of clock cycles.

ah, that is why the program crashed.
i tried to solve this problem using a SDL_mutex , and the program works well now.  :p

---

