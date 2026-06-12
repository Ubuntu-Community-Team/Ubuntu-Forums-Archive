---
title: "Need help with a short &amp; simple C function"
date: 2009-01-16
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-16
Because I don't like complicated objects and stuff when it can be done with just one function,
I tried to convert this C++ thing into one neat C function: [http://lazyfoo.net/SDL_tutorials/lesson14/index.php]](http://lazyfoo.net/SDL_tutorials/lesson14/index.php])

And so I got this function:
```

void tick( int framesPerSecond )
{
    static int startTicks = -1;
    
    // when this is called first time,
    // save the current time for future use
    if ( startTicks == -1 )
    {
        startTicks = SDL_GetTicks();
    }
    // when this is called the second time,
    // calculate time elapsed and fps, and sleep the spare time
    else
    {
        int time_passed = ( SDL_GetTicks() - startTicks );
        SDL_Delay( (1000/framesPerSecond) - time_passed );
        // reset startTicks to say it's first time again
        startTicks = -1;
    }
    
    // not needed but I just like to type it
    return;
}

```
I use that function like this in my main loop:
```

while ( ! done )
{
    tick(30);

    redraw_screen();
    update_stuff();
    blahblahblah

    tick(30);
}

```

The program should stay at 30 fps, I tested it, and it seems to be working correctly.

I'd like to do this without SDL functions, with just standard C libraries, so I wouldn't need another unnecessary extra-dependency.

How would it look like when SDL_GetTicks() and SDL_Delay() are replaced with usleep and some other std stuff?

---

### Post by hod139 on 2009-01-16
[http://ubuntuforums.org/showthread.php?t=296142](http://ubuntuforums.org/showthread.php?t=296142)

---

### Post by crazyfuturamanoob on 2009-01-17
edit: posted into wrong thread

---

