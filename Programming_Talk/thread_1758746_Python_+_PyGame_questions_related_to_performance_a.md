---
title: "Python + PyGame questions related to performance and optimization"
date: 2011-05-15
forum: Programming Talk
---

### Post by slooksterpsv on 2011-05-15
It's me! =P

Anyways, I know how to program standard applications where performance really doesn't matter, as in computers are fast enough now a flick her or there won't matter.

Now with gaming, it's different cause you want to squeeze out all you can. Ok so in Pygame and Python, my sprites seem jittery, and even when trying to do a faux parallax (just a simple moving background) it seems jittery too. I don't know if its because I have it 800x600 (maybe I should try a smaller size) or if its that I'm not optimizing my code.

Now I've posted my source code, it's just one file, if you see something that's like what? Why are you doing that? I'll explain, the code is continually morphing.

Actually I'll zip up everything and post it then you can let me know.

Now for questions:
1. Is it better to group a bunch of sprites and do the pygame.sprite.RenderPlain(sprite_group) - rather than have the sprites handle their drawing individually? I heard this is better so it can make one single sprite image and just blit it to the board. 

2. If so would I just need to make a class where I can define my sprite, what it does (enemies, player, collectables) and do 3 groups or 1 group?

3. Should the background be a sprite? Or should I just blit it as an image? What about in parallax?

I'm trying to stick with this project and make it happen, I've been playing around with the code for 2 days, I made the code so yeah, it may not be optimized, clean or anything like that.

Links to tutorials would be appreciated as well as answers to the questions. (Yes I've google tutorials and some I've been through a few times (same ones), but it gets old going through the same ones.)

Ok I'm done blabbing

---

### Post by cgroza on 2011-05-15
If you really need performance, you will use SDL or OpenGL on C++ or Java. I can't think of some medium to large game coded in python.

---

### Post by ssam on 2011-05-15
you need to profile the code. often a lot of time is spent in a small bit of code. sometimes its not the bit you expect.

---

### Post by slooksterpsv on 2011-05-15
> **ssam said:**
> you need to profile the code. often a lot of time is spent in a small bit of code. sometimes its not the bit you expect.

Thank you! That's what I needed, now I can see what functions are being called the most and how I can optimize it (see below) this is from my python breakout game I'm working on.

[php]
         161812 function calls in 3.260 CPU seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        6    0.000    0.000    0.000    0.000 :0(append)
    22092    0.620    0.000    0.620    0.000 :0(blit)
        1    0.000    0.000    0.000    0.000 :0(exit)
      568    0.280    0.000    0.280    0.000 :0(fill)
      568    1.260    0.002    1.260    0.002 :0(flip)
      569    0.000    0.000    0.000    0.000 :0(get)
      568    0.000    0.000    0.000    0.000 :0(get_pressed)
       44    0.000    0.000    0.000    0.000 :0(hasattr)
      438    0.000    0.000    0.000    0.000 :0(isinstance)
      900    0.000    0.000    0.000    0.000 :0(iter)
     4950    0.010    0.000    0.010    0.000 :0(keys)
       12    0.000    0.000    0.000    0.000 :0(remove)
        1    0.010    0.010    0.010    0.010 :0(setprofile)
      569    0.110    0.000    0.110    0.000 :0(tick)
        1    0.000    0.000    3.250    3.250 <string>:1(<module>)
      568    0.000    0.000    0.000    0.000 main.py:108(CheckBallCollisions)
      568    0.000    0.000    0.000    0.000 main.py:114(MoveBall)
      568    0.280    0.000    0.510    0.001 main.py:142(CheckBlockCollisions)
       12    0.000    0.000    0.000    0.000 main.py:191(HandleBlockCollision)
    94767    0.250    0.000    0.250    0.000 main.py:197(CheckPointInRect)
      332    0.050    0.000    0.120    0.000 main.py:202(CheckMissileCollisions)
      338    0.000    0.000    0.120    0.000 main.py:210(ShootMissile)
        1    0.060    0.060    3.250    3.250 main.py:235(update)
        4    0.000    0.000    0.000    0.000 main.py:34(missile)
      315    0.000    0.000    0.000    0.000 main.py:36(update)
      568    0.010    0.000    0.010    0.000 main.py:48(update)
      568    0.000    0.000    0.000    0.000 main.py:60(update)
    20641    0.030    0.000    0.030    0.000 main.py:70(update)
        1    0.000    0.000    3.260    3.260 profile:0(game.update())
        0    0.000             0.000          profile:0(profiler)
      432    0.000    0.000    0.000    0.000 sprite.py:146(add_internal)
        6    0.000    0.000    0.000    0.000 sprite.py:149(remove_internal)
       18    0.000    0.000    0.000    0.000 sprite.py:267(__init__)
     4950    0.050    0.000    0.060    0.000 sprite.py:271(sprites)
      432    0.000    0.000    0.000    0.000 sprite.py:281(add_internal)
        6    0.000    0.000    0.000    0.000 sprite.py:284(remove_internal)
      438    0.000    0.000    0.000    0.000 sprite.py:290(has_internal)
      900    0.040    0.000    0.050    0.000 sprite.py:301(__iter__)
       18    0.000    0.000    0.000    0.000 sprite.py:307(add)
        6    0.000    0.000    0.000    0.000 sprite.py:339(remove)
     2025    0.090    0.000    0.160    0.000 sprite.py:393(update)
     2025    0.110    0.000    0.750    0.000 sprite.py:401(draw)
       18    0.000    0.000    0.000    0.000 sprite.py:477(__init__)

[/php]

---

### Post by unknownPoster on 2011-05-15
> **cgroza said:**
> If you really need performance, you will use SDL or OpenGL on C++ or Java. I can't think of some medium to large game coded in python.

EVE: Online is a fairly popular MMO coded primarily in Python.

Back on topic, based on the following line: 

```
[COLOR=#000000][COLOR=#0000BB]94767    0.250    0.000    0.250    0.000 main[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]py[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]197[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]CheckPointInRect[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700]
[COLOR=Black]
[/COLOR][COLOR=Black]You can see that CheckPointInRect is called almost 95000 times. I would suggest checking if you really need to call it so many times. Perhaps calling the function every other tick will offer better performance. There are also other possibilities.[/COLOR]
[/COLOR][/COLOR]

---

### Post by slooksterpsv on 2011-05-15
> **unknownPoster said:**
> EVE: Online is a fairly popular MMO coded primarily in Python.

Back on topic, based on the following line: 

```
[COLOR=#000000][COLOR=#0000BB]94767    0.250    0.000    0.250    0.000 main[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]py[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]197[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]CheckPointInRect[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700]
[COLOR=Black]
[/COLOR][COLOR=Black]You can see that CheckPointInRect is called almost 95000 times. I would suggest checking if you really need to call it so many times. Perhaps calling the function every other tick will offer better performance. There are also other possibilities.[/COLOR]
[/COLOR][/COLOR]

Yeah I fixed that now, I made it call if the ball is between 0 and (21 * NUM_ROWS)

---

### Post by simeon87 on 2011-05-16
You should also realize that every function call in Python is more costly than in a language such as Java because it has to lookup where the function is located each time. Python is a dynamic language so the function may have changed etc.

Any function that is called more than necessary should be refactored when speed is critical. Try to cache values and reuse them later.

---

### Post by ssam on 2011-05-17
you should be able to ask the profiler to sort by cumulative time, or number of calls. and keep working through. do you have some measure like frames per second, that you can keep track of to see you progress?

you could also post some of the often called functions here, maybe someone can suggest a speed up for them.

---

### Post by slooksterpsv on 2011-05-17
> **ssam said:**
> you should be able to ask the profiler to sort by cumulative time, or number of calls. and keep working through. do you have some measure like frames per second, that you can keep track of to see you progress?

you could also post some of the often called functions here, maybe someone can suggest a speed up for them.

Hahaha I posted the whole zip of source and images above.

Ok so yeah profiler is really easy to run:
```

import profiler
...code...
game = Game()
profile(game.run())

```

It gives results like above.

It's a complete WIP, but I used a C++ tutorial that shows how to make it to make it, and then converted the C++ to python. I know probably not fully correct, but hey it worked to a degree.

---

