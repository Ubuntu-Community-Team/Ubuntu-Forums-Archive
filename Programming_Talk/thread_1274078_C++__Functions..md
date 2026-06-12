---
title: "C++ : Functions."
date: 2009-09-24
forum: Programming Talk
---

### Post by ashmew2 on 2009-09-24
Hi , I was wondering if it was possible to run more than one function at a time in C++. 
Like you have a block falling function and another character movement function.
So , how do you execute them both in memory at the same time , so that blocks are falling and the character is moving..

Thanks.

---

### Post by pmlxuser on 2009-09-24
I think that is not possible C++ execute command in sequence so still one command has to be executed before the next one. so far thats my experience. i might be wrong

---

### Post by ashmew2 on 2009-09-24
I feared the same :(

Isnt there some sort of suspend to the background ? Like this loop keeps running in the background and you can carry on with your program..?

---

### Post by hessiess on 2009-09-24
Look into threading and concurrency, thogh theare is no standardised way of doing it in C++.

---

### Post by ashmew2 on 2009-09-24
Thanks hessiess , could you point me in the direction as to where to start, ? Ive heard those terms for the first time and google isnt returning much help :(

---

### Post by CptPicard on 2009-09-24
[http://www.google.fi/search?q=threads+c%2B%2B](http://www.google.fi/search?q=threads+c%2B%2B)

Looks fine to me...

Threads are what you're looking for, however, threading complicates matters a lot. The example you are giving in particular would be done just fine sequentially; the user won't be able to tell the difference. In particular on a single-core machine, threads run, in reality, "one at a time" anyway... just interleaved so that it appears they run at the same time.

---

### Post by ashmew2 on 2009-09-24
Thanks CptPicard. I was actually looking for something which "weaves" together things and presents them to the user. I'll look into it and report back. Thanks for all the replies guys!

---

### Post by dwhitney67 on 2009-09-24
> **ashmew2 said:**
> Thanks CptPicard. I was actually looking for something which "weaves" together things and presents them to the user. I'll look into it and report back. Thanks for all the replies guys!

Google on pthread or on Boost Threads.

---

### Post by Simian Man on 2009-09-24
> **ashmew2 said:**
> Hi , I was wondering if it was possible to run more than one function at a time in C++. 
Like you have a block falling function and another character movement function.
So , how do you execute them both in memory at the same time , so that blocks are falling and the character is moving..

Thanks.

Threads are one way to do this, but since you sound like a novice game programmer, I will suggest an alternative, far simpler way to achieve this.  Instead of having both functions run at the same time, have each run one after the other frequently and do their job in pieces.  Here is some psuedocode to illustrate this:

```
void update_blocks(float delta_time) {
  /* delta time is the number of seconds passed since the last time this function was ran */
  
  /* say we want the blocks to drop every 2 seconds */
  /* for real code these should be in a class or struct :) */
  static const float time_to_drop = 2.0;
  static float time_so_far = 0.0;

  /* increment timer and check if it went off */
  time_so_far += delta_time;
  if(time_so_far >= time_to_drop) {
    /* do whatever you need to drop the block */

    /* reset timer */
    time_so_far = 0.0;
  }
}


void update_character(float delta_time) {
  /* these variable store the position and speed of the character
     again they should be in a struct or class */
  static float x, y, dx, dy;

  /* you should set the position and speed based off of the situation
     and/or the keyboard input.  for example you can set dx to something
     positive when the player pushes the right arrow key */

  /* update position based on speed and elapsed time */
  x += dx * delta_time;
  y += dy * delta_time;

  /* you can also add an acceleration vector to make your characters
     for example fall with acceleration due to gravity */

  /* you can also use the delta_time to work your way through
     a sprite animation for example */
}


int main( ) {

  float time_prev = 0, time_now = 0;

  while(game_is_playing) {
    time_prev = time_now;
    time_now = get_current_time( );

    /* handle player input */

    /* update all stuff that must be updated */
    update_blocks(time_now - time_prev);
    update_character(time_now - time_prev);
    /* ... */

    /* draw stuff */
  }
}
```

This is, I think, the simplest way to achieve an interactive game.  Threading is nice, but it is very difficult and, if you're not careful, you can introduce very subtle bugs into your code.

Another benefit of this method, is that you get the "pause" functionality for free by passing 0.0 to your update functions.

Hope the code dump made sense :).

---

### Post by napsy on 2009-09-24
Just avoid using threads as much as possible. If you think you can solve a problem without using a thread, then do so.

---

### Post by TheBuzzSaw on 2009-09-24
Yes, you can achieve pseudo simultaneous execution just by running both adjacently. Computers operate much faster than humans can perceive. :)

---

### Post by dribeas on 2009-09-24
Threads are not easy, but they are a tool you will need to know in the future. Hardware is getting more cpu cores and to take full advantage of current hardware you cannot just develop single threaded code.

As hessiess points out, there is no standard way of doing it in C++ (yet), but the upcoming C++ standard will have thread support in a manner similar to boost::thread from the user point of view, so I would start there. Depending on what your functions work is, you will need to provide inter-thread communication in a thread safe manner. 

If you are developing an application using some high level framework (as QT) you might want to take a look into the thread facilities that are present in the framework. QT has simple interthread communication mechanisms through the use of signals and slots when the emitter and receiver objects belong to different threads.

Anyway, I would go with boost::thread library as it close to what will be standard in all systems in a couple of years.

---

### Post by VertexPusher on 2009-09-25
libcommoncpp is another library providing thread classes. It is more lightweight than libboost-thread.

No matter which one you use, both make multithreading in C++ almost as easy as in Java.

---

### Post by zinouch on 2009-09-25
i think that you have to do what napsy was say, i remember that i use thread only in JAVA when i need multiple inheritance ^^.

you can tell we where do you need threads, may be we can help you ..

---

### Post by CptPicard on 2009-09-25
> **zinouch said:**
> i remember that i use thread only in JAVA when i need multiple inheritance.


Could you please elaborate on this? A completely new approach to me... :confused:

---

### Post by ashmew2 on 2009-09-25
Wow..There is so much to learn. Im actually using an ancient Borland Turbo C Compiler 3.0 As they are following the same in school. They follow DOS around , and i failed the computer exam because i wrote ls everywhere instead of dir.(lol)
Its actually a snake game using graphics.h which is a dos library file. I have to follow Windows and DOS programming until i can finally get out of school :(. If someone's interested in seeing the source code , ill be more than glad to attach it in the next post. Also , the thing with threading is that the teachers at my school(im pretty sure) havent heard about it. So even if i put in hours of effort into it , they'll simply shun me with the "You copied it from the internet" crap.

Thanks for the replies. Ill surely surely look into threading and concurrent programming once im done with the issue at hand.

---

### Post by Simian Man on 2009-09-25
> **ashmew2 said:**
> Wow..There is so much to learn. Im actually using an ancient Borland Turbo C Compiler 3.0 As they are following the same in school. They follow DOS around , and i failed the computer exam because i wrote ls everywhere instead of dir.(lol)

Wow I feel sorry for you having to use such old tools.  Good luck with your project!

---

### Post by ashmew2 on 2009-09-26
> **Simian Man said:**
> Wow I feel sorry for you having to use such old tools.  Good luck with your project!

Lol. I actually feel sort of sorry for myself.But its no point whining when you cant change the system (for now) so its something ill have to live with hehe ;)

---

### Post by ashmew2 on 2009-09-26
Well im actually trying to write a snake game. But at one point into writing the code , i just dont know how to proceed any further. I am unable to turn the snake properly according to the user pressing the keys.

---

### Post by phrostbyte on 2009-09-26
> **ashmew2 said:**
> Well im actually trying to write a snake game. But at one point into writing the code , i just dont know how to proceed any further. I am unable to turn the snake properly according to the user pressing the keys.

What library are you using for grabbing keyboard events? Do you have documentation for this "graphics.h"

If it is DOS you probably must poll the keyboard in a loop.

like 

```

while (1)
{
   if (key_press('w'))
   { 
     // do something
   }
}

```

Or it might support async events which is a more modern way of doing it.

---

### Post by ashmew2 on 2009-09-27
Thanks for the reply phrostbyte. I'm using the kbhit() function which is defined in the conio.h (Borland's file) for grabbing keyboard events. I can use the if(kbhit()) ,  but thats not the problem , the thing is i can use infinite loops and key press events for making the snake's head and continuing it. I just cant figure out a proper way (without glitches) to erase it's tail.

Like if S is pressed , the snake starts going downwards , but how do i erase its tail which could be anywhere.

I've put around 15 hours into figuring out the erasing tail part and im just going nuts..but i just cant seem to figure it out :(( , Please i need help .

---

### Post by ashmew2 on 2009-09-29
Thanks to CptPicard on IRC for suggesting linked lists for making the snake. Thanks CptPicard , i actually now have hope that i will finish this project :D

---

