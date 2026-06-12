---
title: "help on gcc: difficulty on finding alternate for delay() of TurboC"
date: 2007-09-06
forum: Programming Talk
---

### Post by mitchi on 2007-09-06
i am trying write a simple timer program , wherein as I start the program, from 00:00:00 it would start to count/tick until 23:59:59, then resets back to 00:00:00. I've done this with TurboC when I was still on Windows/DOS, but with gcc, I cannot find any function related to delay(), which delays the count/tick display of the number.

Can anyone help me on this one. As I've trying to figure this out for a week now.

Thanks!

---

### Post by gnusci on 2007-09-07
I think this code can help you:

[PHP]
/* timer.c */
#include <stdio.h>
#include <time.h>

void delay_sec( int seconds ){
    clock_t endwait;
    endwait = clock () + seconds * CLOCKS_PER_SEC;
    while (clock() < endwait) {}
}

int main (void){
    time_t rawtime, ini_time, now;
    struct tm *ptm;

    time ( &ini_time );
    for(;;){
        time ( &rawtime );
        //ptm = gmtime ( &rawtime );
        //printf ("%2d:%02d:%02d\n", ptm_2->tm_hour, ptm_2->tm_min, ptm_2->tm_sec);
        now = rawtime - ini_time;
        ptm = gmtime ( &now );
        printf ("%2d:%02d:%02d\n", ptm->tm_hour, ptm->tm_min, ptm->tm_sec);
        delay_sec(1);
    }
    return 0;
}
[/PHP]

compile it with:

**$ gcc timer.c -o timer**

I think you can take the main idea from this program...

This page it is very useful:

[http://www.cplusplus.com/](http://www.cplusplus.com/)

---

### Post by mitchi on 2007-09-08
the program works, thanks. but how about changing the ticker input to milliseconds? is that possible with this function? because with the delay() function, the default input is in milliseconds, so if I'd input 1000, the ticker would count 1 second. 

Thanks.

---

### Post by scourge on 2007-09-08
> I think this code can help you

I don't think it's a good idea to use such a loop for sleeping, it just wastes the cpu time that could be needed by some other thread or process.

> **mitchi said:**
> the program works, thanks. but how about changing the ticker input to milliseconds? is that possible with this function? because with the delay() function, the default input is in milliseconds, so if I'd input 1000, the ticker would count 1 second. 

Thanks.

You can use nanosleep to do that: [http://www.gnu.org/software/libc/manual/html_node/Sleeping.html](http://www.gnu.org/software/libc/manual/html_node/Sleeping.html)

---

### Post by mitchi on 2007-09-08
> #include<stdio.h>
#include<unistd.h>
main()
{
int x;
for(x=0;x<10;x++)
{
printf("*");
sleep(1);
}
}

i was hoping that this program would display 10 '*' characters, with 1 second interval before displaying  the next character. What happened was,  10 seconds was consumed before displaying the whole bunch of '*'. Please help me on this as I would want to create a simple time ticker program, just like a stopwatch program, where i would execute it in the command-line.

I've done this easily with TurboC, using the delay() function, but since I want to master C on Linux Programming, I'm having difficulties on this simple program.

Please help me.

Thanks.

---

### Post by gnusci on 2007-09-08
> **scourge said:**
> I don't think it's a good idea to use such a loop for sleeping, it just wastes the cpu time that could be needed by some other thread or process.

You can use nanosleep to do that: [http://www.gnu.org/software/libc/manual/html_node/Sleeping.html](http://www.gnu.org/software/libc/manual/html_node/Sleeping.html)

You are completely correct, I did know the performance of the above code an is completely a waste of cpu, I just wanted to show him some ideas, but anyway here there is a better code using [COLOR="Red"]usleep[/COLOR]. 

[PHP]
/* udelay.c: micro-seconds delay */

#include <stdio.h>
#include <unistd.h>
#include <time.h>

// microseconds delay
void udelay( int useconds ){
    usleep(useconds);
}

int main (){
    int steps;
    time_t rawtime, ini_time, now;
    struct tm *ptm;

    time ( &ini_time );
    printf ("Timer...\n");
    for (steps=0; steps<10; steps++)
    {
        // million of microseconds delay = one second
        udelay(1000000);

        time ( &rawtime );
        now = rawtime - ini_time;
        ptm = gmtime ( &now );

        printf ("countdown: %d\n",steps);
        printf ("%2d:%02d:%02d\n", ptm->tm_hour, ptm->tm_min, ptm->tm_sec);

    }
    printf ("!!!BOOM!!!\n");
    return 0;
}

[/PHP]

The program does no use cpu during the sleeping time, that save cpu. You can find more information in:

[http://linux.die.net/man/3/usleep](http://linux.die.net/man/3/usleep)

---

### Post by Fixman on 2007-09-08
> **mitchi said:**
> i was hoping that this program would display 10 '*' characters, with 1 second interval before displaying  the next character. What happened was,  10 seconds was consumed before displaying the whole bunch of '*'. Please help me on this as I would want to create a simple time ticker program, just like a stopwatch program, where i would execute it in the command-line.

I've done this easily with TurboC, using the delay() function, but since I want to master C on Linux Programming, I'm having difficulties on this simple program.

Please help me.

Thanks.

sleep is just as delay, so if you want to use a 1 second interval, you should write

```

//...
printf ("*") ;
sleep (1000) ;
//...

```

---

### Post by DMills on 2007-09-08
Sleep takes an argument in seconds, not milliseconds, so sleep (1) will sleep for (at least) a second.

Select with no file descriptors and a timeout is a good way to get sub second delays. 

Regards, Dan.

---

### Post by winch on 2007-09-08
> **mitchi said:**
> i was hoping that this program would display 10 '*' characters, with 1 second interval before displaying  the next character. What happened was,  10 seconds was consumed before displaying the whole bunch of '*'. Please help me on this as I would want to create a simple time ticker program, just like a stopwatch program, where i would execute it in the command-line.

Use [fflush]("http://www.cplusplus.com/reference/clibrary/cstdio/fflush.html") to flush the buffer to make sure printf output makes it to the screen

```

#include <stdio.h>
#include <unistd.h>

int main()
{
    int x;
    for(x=0;x<10;x++)
    {
        printf("*");
        fflush(stdout);
        sleep(1);
    }
    return 0;
}

```

---

### Post by scourge on 2007-09-08
> **Fixman said:**
> sleep is just as delay

The sleep() function in unistd definitely takes seconds, not milliseconds, as its argument.


[quote=winch]Use fflush to flush the buffer to make sure printf output makes it to the screen[/quote]

Yeah, or turn off output buffering completely:
```
setbuf(stdout, NULL);
```

---

### Post by gnusci on 2007-09-08
Exactly, sometimes the standard output is buffered and you must force it to print it out with [COLOR="Red"]fflush[/COLOR]. Give a look to:

[http://www.opengroup.org/onlinepubs/000095399/functions/fflush.html](http://www.opengroup.org/onlinepubs/000095399/functions/fflush.html)

Here I am adding the last code again but with a fancy text mode progress bar, maybe you will like it... ;)

[PHP]
/* udelay.c: micro-seconds delay */

#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<time.h>


void udelay( int useconds ){
    //sleep micro-seconds
    usleep(useconds);
}

// 10 steps progress bar with 20 columns
void progressbar(int pc){
    // 20 column progress bar
    int tmp, cols = 20;

    printf("\e[K  %3d%% [", pc);

    for(tmp=cols*pc/10;tmp;tmp--)
        printf("#");
    for(tmp=cols-(cols*pc/10);tmp;tmp--)
        printf("-");

    printf("]\r");
    fflush(stdout);
}

int main (){
    int steps;
    time_t rawtime, ini_time, now;
    struct tm *ptm;

    time ( &ini_time );
    printf ("Progress Bar...\n");

    for(steps=0; steps<10; steps++){
        progressbar(steps+1);

        udelay(1000000);

        time ( &rawtime );
        now = rawtime - ini_time;
        ptm = gmtime ( &now );
        //printf ("%2d:%02d:%02d\n", ptm->tm_hour, ptm->tm_min, ptm->tm_sec);
    }
    printf("\n");
    printf ("!!!BOOM!!!\n");
    return 0;
}

[/PHP]

---

### Post by dwhitney67 on 2007-09-08
Here's a timer app I wrote many moons ago in C++.  This timer utility allows for one to choose between a one-shot, repeating, or continuous timer.  It also allows for one to choose if the timer will block (the caller) or not.  Best of all, it allows one to specify a callback routine that will get executed when the timer expires.

Sorry that it lacks comments.  I threw it together real quick and never found a use for it.  Here's the code:

[PHP]#include <iostream>
#include <sys/types.h>
#include <sys/select.h>

using namespace std;


template< class T >
class Timer
{
  public:
    enum TimerType
    {
      ONE_SHOT, REPEATING, CONTINUOUS
    };

    enum TimerRunType
    {
      BLOCKING, NON_BLOCKING
    };

    Timer( int seconds, TimerType timerType = ONE_SHOT, int repeats = 1 )
    {
      setupTimer( seconds, 0, timerType, repeats );
    }

    Timer( int seconds, int microseconds = 0, TimerType timerType = ONE_SHOT, int repeats = 1 )
    {
      setupTimer( seconds, microseconds, timerType, repeats );
    }

    inline void start( TimerRunType runType = BLOCKING )
    {
      pid_t childPid = 0;

      if ( runType == NON_BLOCKING )
      {
        childPid = fork();
      }

      if ( childPid == -1 )
      {
        cerr << "failed to start timer process" << endl;
      }
      else if ( childPid == 0 )
      {
        switch ( type )
        {
          case ONE_SHOT:
              struct timeval tv;
              tv.tv_sec  = seconds;
              tv.tv_usec = microseconds;
              select( 0, 0, 0, 0, &tv );
              functor();
              break;

          case REPEATING:
          case CONTINUOUS:
              int r = repeats;
              while ( ( r-- > 0 ) || ( type == CONTINUOUS ) )
              {
                struct timeval tv;
                tv.tv_sec  = seconds;
                tv.tv_usec = microseconds;
                select( 0, 0, 0, 0, &tv );
                functor();
              }
              break;
        }

        if ( runType == NON_BLOCKING )
        {
          exit( childPid );
        }
      }
      else
      {
        // in parent context... just return
      }
    }

  private:
    void setupTimer( int seconds, int microseconds, TimerType timerType, int repeats )
    {
      this->seconds      = seconds;
      this->microseconds = microseconds;
      this->type         = timerType;
      this->repeats      = repeats;
    }

    int       seconds;
    int       microseconds;
    TimerType type;
    int       repeats;

    T functor;
};


class WaitTimer
{
  private:
    class CallbackForTimer
    {
      public:
        CallbackForTimer() {}
        void operator()() { cout << "waiting..." << endl; }
    };

    typedef Timer< CallbackForTimer > WaitTimerDef;

  public:
    WaitTimer( int seconds, int milliseconds = 0 )
        : internalTimer( seconds, milliseconds, WaitTimerDef::REPEATING, 1 )
    {
    }

    void start()
    {
      internalTimer.start( WaitTimerDef::BLOCKING );
    }

  private:
    WaitTimerDef internalTimer;
};


class CallbackOne
{
  public:
    CallbackOne() {}

    void operator()()
    {
      cout << "CallbackOne operator() has been called" << endl;
    }
};


class CallbackTwo
{
  public:
    CallbackTwo() {}

    void operator()()
    {
      cout << "CallbackTwo operator() has been called" << endl;
    }
};


int main(int argc, char** argv)
{
  int seconds      = 1;
  int microseconds = 0;

  typedef Timer< CallbackOne > CallbackOneTimer;
  typedef Timer< CallbackTwo > CallbackTwoTimer;

  CallbackOneTimer timerOne( seconds, microseconds, CallbackOneTimer::REPEATING, 6 );
  CallbackTwoTimer timerTwo( seconds, 500         , CallbackTwoTimer::REPEATING, 6 );

  timerOne.start( CallbackOneTimer::NON_BLOCKING );
  timerTwo.start( CallbackTwoTimer::NON_BLOCKING );

  WaitTimer wt( 3 );

  int iterations = 5;
  while ( iterations-- )
  {
    wt.start();
  }
}[/PHP]

---

### Post by pmasiar on 2007-09-08
dwhitney67: nice color highlighting, which tool did you used?

[php]
# let's try Python formatted with PHP colors
def fn1():
   print 'it works!'
[/php]

---

### Post by dwhitney67 on 2007-09-09
Nothing special.  Just opted to post my code using the PHP format in lieu of the Code format.  With lengthy posts, PHP provides the scroll bar; Code format does not.

---

### Post by mitchi on 2007-09-11
thanks everyone, but i dont understand these codes?

> 
void progressbar(int pc){
    // 20 column progress bar
    int tmp, cols = 20;

    **printf("\e[K  %3d%% [", pc);**

    for(tmp=cols*pc/10;tmp;tmp--)
        printf("#");
    for(tmp=cols-(cols*pc/10);tmp;tmp--)
        printf("-");

    [B]printf("]\r");
    fflush(stdout);[/B]
}

can someone tell me the use of these codes?

thanks for the code gnusci. the progressbar is really great, but i need to understand it line by line, i haven't seen or used this codes before. sorry for the trouble.

---

### Post by gnusci on 2007-09-12
I think you can find the meaning out by yourself very easy and you will have a lot of fun... here some links:

[http://en.wikipedia.org/wiki/Printf](http://en.wikipedia.org/wiki/Printf)
[http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)
[http://www.opengroup.org/onlinepubs/000095399/functions/printf.html](http://www.opengroup.org/onlinepubs/000095399/functions/printf.html)
[http://www.ss64.com/bash/printf.html](http://www.ss64.com/bash/printf.html)
[http://www.cppreference.com/escape_sequences.html](http://www.cppreference.com/escape_sequences.html)
[http://www.codecodex.com/wiki/index.php?title=Escape_sequences_and_escape_characters](http://www.codecodex.com/wiki/index.php?title=Escape_sequences_and_escape_characters)
[http://en.wikipedia.org/wiki/C_syntax](http://en.wikipedia.org/wiki/C_syntax)

If after you check those pages you have some questions just let us know...

---

