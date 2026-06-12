---
title: "Sorry, I don't know what should I put as title"
date: 2009-02-27
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-02-27
I'm making a simple game in C. It's nearly finished. But I can't get stable framerate. It's jumping all around.

When processor works harder (higher MHz), framerate increases radically. What's up with this code?

```

#define FPS 30

// update and draw everything
void world_step( world_t *w, SDL_Surface *target )
{
    double sec;
    clock_t kello = clock();
    
    
    world_update( w );
    world_draw( w, target );
    
    
    kello = clock() - kello;
    sec = (double)kello / (double)CLOCKS_PER_SEC;
    sec = sec * 1000;
    static const int max_sleep = 1000/FPS;
    
    if ( sec <= max_sleep )
        usleep( sec * 1000 );
}

```

I can't find any bugs from above. It seems to work as it should. Why does the framerate increase when I put some load on processor, like opening a media player?

---

### Post by cb951303 on 2009-02-27
here are the best articles you can find on the issue. they helped me a lot.

[http://dewitters.koonsolo.com/gameloop.html](http://dewitters.koonsolo.com/gameloop.html) (4th one is a good method)
[http://gafferongames.com/game-physics/fix-your-timestep/](http://gafferongames.com/game-physics/fix-your-timestep/)

:popcorn:

---

### Post by jimi_hendrix on 2009-02-27
curious: what type of game?

---

### Post by crazyfuturamanoob on 2009-02-27
> **jimi_hendrix said:**
> curious: what type of game?

Player shoots birds off the sky in real time.
Screenshot of what's finished so far:

[[IMG]http://img15.imageshack.us/img15/4069/birdhunter.th.png[/IMG]](http://img12.imageshack.us/img12/4069/birdhunter.png)

All artwork and 99% coding done by me. 


> **cb951303 said:**
> here are the best articles you can find on the issue. they helped me a lot.

[http://dewitters.koonsolo.com/gameloop.html](http://dewitters.koonsolo.com/gameloop.html) (4th one is a good method)
[http://gafferongames.com/game-physics/fix-your-timestep/](http://gafferongames.com/game-physics/fix-your-timestep/)

:popcorn:

But GetTickCount() is only in windows.h! :O

---

### Post by tneva82 on 2009-02-27
> **crazyfuturamanoob said:**
> But GetTickCount() is only in windows.h! :O

Not sure what GetTickCount does but maybe SDL's GetTicks does same thing? Atleast function sounds similar ;-)

Of course there might be OS specific solution but SDL is cross-platform so porting game to others is easier that way.

---

### Post by cb951303 on 2009-02-27
> **crazyfuturamanoob said:**
> Player shoots birds off the sky in real time.
Screenshot of what's finished so far:

[[IMG]http://img15.imageshack.us/img15/4069/birdhunter.th.png[/IMG]](http://img12.imageshack.us/img12/4069/birdhunter.png)

All artwork and 99% coding done by me. 


artwork looks kinda cool :D

> 
But GetTickCount() is only in windows.h! :O
as already stated SDL_GetTicks() would do the job. Other libraries have differently named functions. I'm almost positive that libc has one too :popcorn:

---

### Post by crazyfuturamanoob on 2009-02-27
Ok, I managed to make steady framerate. Great, processor speed doesn't affect it anymore. :) Thanks.

---

### Post by cb951303 on 2009-02-28
Glad you worked it out. Which method did you use?

Also when the game is coming out :)?

---

### Post by crazyfuturamanoob on 2009-02-28
Here, It's almost 1:1 copy of the one in the article you gave me:
```


// update and draw the world, and also keep framerate
void world_step( world_t *w, SDL_Surface *target )
{
    int skip_ticks = 1000 / frames_per_second;
    static int next_game_tick;
    static int sleep_time = 0;
    
    static int firstTime = 1;
    if ( firstTime )
    {
        next_game_tick = SDL_GetTicks();
        firstTime = 0;
    }
    
    
    world_update( w );
    world_draw( w, target );
    
    
    next_game_tick += skip_ticks;
    sleep_time = next_game_tick - SDL_GetTicks();
    
    if ( sleep_time >= 0 )
        SDL_Delay( sleep_time );
    else;
        /// ****, we are running behind!
}

```

It's the second method. No interpolation used (4th), because all today's hardware can handle that for sure without laaging, and interpolation would need much bigger changes.

And the game is finished next week for sure (probably even tomorrow if I don't encounter huge problems/bugs). It's a game everyone can make in a matter of days, so don't expect anything big.

---

### Post by crazyfuturamanoob on 2009-03-01
The game is complete. It still needs bugfixes, but I'm lazy and I'll leave 0.9 the final version.

It's boring, it has some seriously annoying bugs, nothing special, so I'm not making a new thread or anything.


Aim with mouse, shoot with any key or mouse button, and the more kills you make with one shot, 

the more score you get ( score += killcount*killcount ).


If you are interested in about it, or just curious, get it here: [[COLOR="RoyalBlue"]_Download birdhunterV9.tar.gz_[/COLOR]](http://host-a.net/crazyfuturamafreak/birdhunterV9.tar.gz)

Now I'm asking, how is my coding style? Is that the "real" way to make games?


How was the original Quake done? (it was coded in pure C)

Does it have a HUGE data structure which contains all game information?


And the bugs/problems I know are:
[list]
[*]Flickering animation


[*]Sometimes birds go temporarily invisible


[*]Sound plays one second too late


[*]Sometimes when shooting a bird, all birds disappear 
(linked list head gets terminated)
[/list]

And what now? Another game? I can't make my mind. Everything is done already.


**Edit: I just decided to do it. Sprite flickering fixed. PM me if you absolutely want the final version.**

---

### Post by jimi_hendrix on 2009-03-01
> **crazyfuturamanoob said:**
> 
And what now? Another game? I can't make my mind. Everything is done already.

exaggerate on this please

---

### Post by crazyfuturamanoob on 2009-03-02
> **jimi_hendrix said:**
> exaggerate on this please

Let me rephrase: everything simple enough I could do is already done.

---

### Post by Dougie187 on 2009-03-02
I think he wants ideas for games. Or maybe an idea on what he should work on next.

---

### Post by jimi_hendrix on 2009-03-02
ok then...i am learning orge3d and am planning on making a very simple space flight game...if you want to join in that would be great but i am at the "learn the API and how to use wings3d" stage

---

