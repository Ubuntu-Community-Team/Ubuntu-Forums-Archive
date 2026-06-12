---
title: "[C] What would be the best way to find the elapsed time in milliseconds?"
date: 2008-07-10
forum: Programming Talk
---

### Post by Yes on 2008-07-10
I have a method that's called in a while loop, and it gets user input.  There's other things moving around the screen which are also called from the while loop, so there's a tenth of a second timeout on the input, if there's no input after that long it continues through the while loop.  That way everything keeps moving.

The problem is when there is user input, it speeds everything else up because it's not waiting a tenth of a second every time it goes through the loop.  I need a way to figure out long it took, in milliseconds, to get the input, find the difference of that and a tenth of a second, and then wait the difference.  How should I do this, as I can't seem to find any way to get the time in milliseconds.

Thanks!

---

### Post by supirman on 2008-07-10
see "man gettimeofday"

You can do something similar to the following.  This hasn't been compiled, but it should be close enough to give you the idea.

```

#include <sys/time.h>
#include <time.h>

struct timeval start, end;
int msec;

gettimeofday(&start, NULL);
yourUserInputFunction();
gettimeofday(&end, NULL);
// disregarding tv_sec since you said it's bouned at .1s anyway.
msec = 1000*(end.tv_usec-start.tv_usec); 


```

---

### Post by odyniec on 2008-07-11
> **supirman said:**
> ```

// disregarding tv_sec since you said it's bouned at .1s anyway.
msec = 1000*(end.tv_usec-start.tv_usec);
```
You still need to take tv_sec into account in case the number of seconds changes while the measurement is taking place -- otherwise you might get a negative number of milliseconds. Additionally, to convert microseconds to milliseconds, you should divide by 1000 rather than multiply. So that line should read:
```
msec = ((end.tv_sec * 1000000 + end.tv_usec) - 
  (start.tv_sec * 1000000 + start.tv_usec)) / 1000;
```

---

### Post by gnusci on 2008-07-11
Here some hints

[PHP]
#include <time.h>

clock_t start, stop;

void main(void){
  start = clock();
  // do whatever you want here
  stop = clock();
  clock_t mseconds = ( stop - start)*1E3 / (CLOCKS_PER_SEC) ;
  return 0;
}


[/PHP]

---

### Post by Yes on 2008-07-11
Ugh, I have a new problem now - after the user presses something, I need to be able to get input again while I'm waiting for the rest of the tenth of a second to finish.  Is this the type of situation you would use threads in?  So the user's person would be one thread, and the other person would be another, and then their movements aren't dependant on the other one finishing their stuff?  Or am I missing the point of threads?

---

### Post by dwhitney67 on 2008-07-12
> **Yes said:**
> I have a method that's called in a while loop, and it gets user input.  There's other things moving around the screen which are also called from the while loop, so there's a tenth of a second timeout on the input, if there's no input after that long it continues through the while loop.  That way everything keeps moving.

The problem is when there is user input, it speeds everything else up because it's not waiting a tenth of a second every time it goes through the loop.  I need a way to figure out long it took, in milliseconds, to get the input, find the difference of that and a tenth of a second, and then wait the difference.  How should I do this, as I can't seem to find any way to get the time in milliseconds.

Thanks!
Can you please re-write this OP?  Here are my questions, that perhaps you can clarify:

1.  "...things moving around the screen..." - What things?  Are you using ncurses?

2.  You indicate that you want to wait a tenth of a second for input, and yet you need to get time in milliseconds.  What is the correct time unit that you desire?

3.  Is this a multi-threaded application?  Your final post indicates that it is, yet the OP does not.  Which is it?

4.  Lastly, what type of input are you attempting to acquire?  Is it a character, a string, a number?  Have you managed to set up non-blocking I/O?  Will the user have to press "enter" to finish their input?

Trying reading the man-page for select().  I think this might be helpful to you with regards to knowing when to gather user input; it also provides a timer for the delay.  However without knowing more about your application, it will be difficult to assess whether select() is really needed.

---

### Post by gnusci on 2008-07-12
> **Yes said:**
> Ugh, I have a new problem now - after the user presses something, I need to be able to get input again while I'm waiting for the rest of the tenth of a second to finish.  Is this the type of situation you would use threads in?  So the user's person would be one thread, and the other person would be another, and then their movements aren't dependant on the other one finishing their stuff?  Or am I missing the point of threads?

Use threads for multiuser programming

[http://www.nicemice.net/amc/os-prelim/summaries/intro-threads.var](http://www.nicemice.net/amc/os-prelim/summaries/intro-threads.var)

---

### Post by Yes on 2008-07-12
Ok - 

I'm using ncurses.  The user has a piece that they move around the screen with the arrow keys, and there's other computer controlled pieces also moving.  Using the halfdelay method in ncurses, I set it so that user input times out after a tenth of a second.  That way if the user doesn't want to move, the computer controlled pieces will continue to move.  The problem is when there is user input, since everything isn't waiting a tenth of a second anymore to keep moving things speed up around the screen considerably.  I needed a way to wait for the remainder of the tenth of a second, which is why I needed to be able to figure out, in milliseconds, how long it took to get the input.  But then while I'm waiting, I can't have the program just stop - I need to still be able to get user input, so they're not limited to only moving once every tenth of second.

In my last post, I asked if this was the type of program where using threads would be helpful - as of right now, it's not multithreaded.

I'll look into select() now, thanks.

---

### Post by dwhitney67 on 2008-07-12
I recently helped another forum member with a simple ncurses-driven game, and it employed the use of select().  Maybe you can take a look at it to see if it will help you (see post #9 at): [http://ubuntuforums.org/showthread.php?t=844566](http://ubuntuforums.org/showthread.php?t=844566)

---

