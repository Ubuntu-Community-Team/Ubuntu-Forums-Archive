---
title: "Setting fixed fps in opengl"
date: 2009-02-23
forum: Programming Talk
---

### Post by Bölvaður on 2009-02-23
Im wondering if it would be better to use glutGet(GLUT_ELAPSED_TIME) or some more basic time counter for setting fixed frames/second.

I have no experience with game development but Im currently making a simple 3d game which will be my first step towards making a small linux game sometime in the future.

How I would do things is if I'd want 100 frames per second:

```
create timer

loop begins

   execute calculations
   draw objects
   wait until timer gets to 0.1 seconds
   set timer to 0

end loop
```

I have been looking at tutorials but I only find them for windows (#include windows.h)

---

### Post by Zugzwang on 2009-02-23
This is normally a bad idea. Rather try to take the current time before the computation of each frame. Then perform movements and stuff relative to the difference between the last frame's time and the current frame's time. Here comes a pseudo-code example:

```

current_time = time()
do:
   last_time = current_time
   current_time = time()
   timeDiff = current_time - last_time

   object_x_pos += SPEED * timeDiff

   draw_object()
until end_of_program

```

This way, your program will run smooth under all refresh rates and will not slow down when the user's gfx card can only do 50 fps, for example.

---

### Post by Ferrat on 2009-02-23
Well I would do it with a while loop running the game then a while loop outside for rendering 



```


#define FPS_WANTED 100

int NewTime, LastTime


while GameRunning == true
   
{
     while (NewTime < LastTime + (1000/FPS_WANTED))
        {
         NewTime = getTime in milliseconds or something
         Do all the other stuff with no max speed
         }
     
     DoRenderFuction()
     lastTime = getTime 
}
   
```

if I haven't missed something then you should only reach the render function once every 1/100 of a second = 100FPS (max)

if you're doing it in C++ then you might need to add a if function checking seconds and adding 1000 to NewTime if needed since the sys/time.h loops the "under 1sec" measure, might want to devide it as well since it's goes +1 every 1/1 000 000 sec = milliseconds (easier to work with)

EDIT: 
Post above might be better, but then again you can just turn my example around and put the render in the second loop and switch it around a bit.

---

### Post by Bölvaður on 2009-02-23
_Thank you Zugzwang, thank you very much _:KS
I actually had in mind doing another loop which would make sure I could draw fewer frames than... 100fps for an instance. But it would take few more calculations per frame :(
but man your way is so much better and cleaner code :)

I forgot to say I am most comfortable with **C++**, but assumed naming GLUT and #include was clear enough indication of C/C++.


But my real struggle would be deciding weather to use &#8594; <time.h>
or that is included into the &#8594; <GL/glut.h>

I have used the glut library in the past for calculating fps but somehow I would assume it takes more calculation time than if I'd rely on <time.h>

any inputs?

---

### Post by Ferrat on 2009-02-23
Not sure about the performance, if your app is very heavy then might be worth making two functions with the same name (should be fairly easy and fast), one using time.h and one gluts way,comment one out then later on when you are tweaking in the end you can benchmark the two and pick the one working best with your code? :)

---

### Post by cb951303 on 2009-02-23
Fixed FPS is not a good idea: [http://dewitters.koonsolo.com/gameloop.html](http://dewitters.koonsolo.com/gameloop.html)
This is the best article I've ever read on this issue. It investigates  different implementations of time management in game loops. 4th one is the way to go.

Also, this one is a good read too: [http://gafferongames.com/game-physics/fix-your-timestep/](http://gafferongames.com/game-physics/fix-your-timestep/)

:popcorn:

---

