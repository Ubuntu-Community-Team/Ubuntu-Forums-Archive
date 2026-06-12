---
title: "making a thread wait on windows - how?"
date: 2007-11-14
forum: Programming Talk
---

### Post by c174 on 2007-11-14
This post is about using threads under windows xp.

I'm writing a piece of simulation software in C++ which needs to plot graphics along the course of execution. I have written a small plotting facility based on freeglut. The plotting utility is started in its own thread by using "_beginthread". This thread never returns because "glutMain()" never returns.

The simulation thread can then send a plotting command by pushing arguments on a list. Nothing is processed until I put a call which I have named "drawnow()". This function looks like this

```
bool dispatch;

void drawnow() {
    dispatch = true;
    while( dispatch ) Sleep( 0 );
}
```

The glut idle function will then process the plotting commands in the following way

```
void myGlutIdle() {
    if( !dispatch ) Sleep( 1 );

    while( !command_list.is_empty() ) {
        // process next command...
    }
    dispatch = false;
}
```

My question is now:

The strategy above using the global variable "dispatch" works fine on a specific laptop computer with windows xp on it. But running the program on a desktop computer (again win xp) is terrible -- it is sloooow. I think the problem is related to punching in and out of Sleep().

I realize that there most be some functions available for "pausing" the main simulation thread, while the graphic commands are being processed. Is this a "wait"-problem or a "synchronization"-problem?

I don't know a lot about thread (it was a big thing getting _beginthread to work :) ), so if you can help me I would be very happy

---

### Post by aks44 on 2007-11-14
Instead of polling the "dispatch" variable, you should wait on an event. See CreateEvent and related APIs (you probably want an auto-reset event BTW).

Also, be sure to synchronize access to your command_list with a mutex (CreateMutex et al).

---

### Post by c174 on 2007-11-14
Ah, "CreateEvent" sounds good. You are right about ensuring safe access to command_list - that is one reason why I want to block the main thread completly :)

I will look for CreateEvent and CreateMutex on MSDN. Thank you!

---

### Post by j_g on 2007-11-14
aks44's advice is spot on. Hey, another programmer here who knows how to answer Win32 questions! (And wow, no one suggesting that the solution to the OP's problem is to dump his code, and use Python!)

I'll just add that, since it appears that what you need to do is serialize access to a shared list between threads, an even easier thing to do may be to surround any list manipulation code with a call to EnterCriticalSection(), and LeaveCriticalSection() when you're done. Then you wouldn't need any mutex (nor events) at all. (A critical section is essentially a simple mutex that works only between threads in the same process. It doesn't work between two different processes, like full mutexes do). It's more efficient than a mutex too.

---

### Post by aks44 on 2007-11-14
> **j_g said:**
> Hey, another programmer here who knows how to answer Win32 questions!

That's how I make my living, so... ;)


> **j_g said:**
> an even easier thing to do may be to surround any list manipulation code with a call to EnterCriticalSection(), and LeaveCriticalSection() when you're done. Then you wouldn't need any mutex (nor events) at all.

Good point. I tend to consider Win32's CriticalSections for what they really are: mutexes in disguise. But you're right, CriticalSections are preferable over mutexes if you don't need to cross process boundaries, since they are more efficient.


However I still think that to achieve what the OP wants, events are needed as a synchronizer between drawnow() and myGlutIdle(). From the top of my head (the boiler-plate code and error checks are missing, but you get the picture):


```
void drawnow()
{
  ResetEvent(drawFinishedEvent);
  SetEvent(processListEvent);
  WaitForSingleObject(drawFinishedEvent, INFINITE);
}

void myGlutIdle()
{
  if (WaitForSingleObject(processListEvent, 0) == WAIT_0)
  {
    // process messages (while loop, protected by adequate locks)
    SetEvent(drawFinishedEvent);
  };
}
```

---

### Post by c174 on 2007-11-14
Thanks for the code example. It is useful for a newbee. 

But is there not a "ResetEvent(processListEvent);" missing just before "SetEvent(drawFinishedEvent);"?

If I get it right it is necessary to have two event objects - one for "pausing" the drawnow() function and another one for "pausing" the myGlutIdle() function? (this is of course no problem, just a question to get some understanding. There is no negated version of WaitForSingleObject() ? or negated version on an event...? )

Yep, a side effect of drawnow() is to synchronize the main thread and the graphics thread. It is nice to know that calling "drawnow" will flush all graphic commands at the given position in the code. For example this can be useful for debugging. On the other hand I suppose it might reduce performance a little bit.

---

### Post by c174 on 2007-11-14
OOPS: There's a mistake in my first post. The code sample for myGlutIdle should be

```
void myGlutIdle() {
    if( !dispatch ) {
        Sleep( 1 );
        return;
    }

    while( !command_list.is_empty() ) {
        // process next command...
    }
    dispatch = false;
}
```

The idea is of course to only process the command_list when "dispatch" is TRUE :) But I think you were able to see that ;)

---

### Post by aks44 on 2007-11-14
> **c174 said:**
> But is there not a "ResetEvent(processListEvent);" missing just before "SetEvent(drawFinishedEvent);"?
Well, theoretically ResetEvent(drawFinishedEvent) is not needed if you use auto-reset events (ie. it will be automatically reset as soon as WaitForSingleObject detects it is signalled). But I guess that my usual paranoia dictated me to put that ResetEvent there just in case... :-\"


> **c174 said:**
> If I get it right it is necessary to have two event objects - one for "pausing" the drawnow() function and another one for "pausing" the myGlutIdle() function?
You could probably do it another way, but that's the first thing that popped into my mind. :)


> **c174 said:**
> There is no negated version of WaitForSingleObject() ? or negated version on an event...?
The closest thing to a "negated event"  would be WaitForSingleObject failing due a time out :

```
if (WaitForSingleObject(eventHandle, 0 /* immediate */) == WAIT_TIMEOUT)
{
  // event is not signaled
}
```

---

### Post by j_g on 2007-11-14
Yeah, I just suggested EnterCriticalSection()/LeaveCriticalSection() because it _may_ be relevant to what he's trying to do. I may be thick, but I just couldn't figure out exactly what the OP was trying to do based upon his code snippets. In particular, I'm not sure if what he's trying to do is prevent one thread from modifying the list while another thread is doing the same. If that's all he's concerned about, EnterCriticalSection is the way to go. On the other hand, does he also need a thread to be able to "notify" another thread when a change has been made to the list? If he needs to do that _also_, then (as you noted) an event is the way to go, because a Critical Section doesn't implement any sort of notification feature.

---

### Post by c174 on 2007-11-15
To be more precise about what I want to do: The main simulation thread might look something like this:

```
#include "my_variables.h"

int main() {
    // read problem definition from a file
    read_problem();

    // plot initial configuration
    plotting::figure(1);
    plotting::plot( x, y );
    plotting::drawnow();

    // wait for user input
    getchar();

    // perform simulation
    while( t < t_end ) {
        time_integrate( t, t + t_delta );

        plotting::plot( x, y );
        plotting::drawnow();

        t += t_delta;
    }
    return 0;
}
```

The graphic commands are put in namespace "plotting".

About the command list: The main thread will only push arguments onto the list. The graphics thread will only pop arguments from the list. The command "drawnow" should enable/disable the execution of the threads in a exclusive manner. Until "drawnow" is called let the graphics thread sleep. Once "drawnow" is called, block the main thread, and let the graphics thread run until all item in the command list have been processed. 

At this point, the graphics thread has nothing more to do and should therefore sleep. The main thread is then reactivated to continue the simulation. New graphic commands are pushed on the list. The scenario starts over when "drawnow" is called again.

Hope I'm more clear now :) Anyhow I think the events is what I need.

Thanks for very good answers to my post!! Really makes my want to change the current design into "the right way". Thanks

---

### Post by j_g on 2007-11-15
Well, I don't know about aks44, but I'm really confused by these code snippets. You've got this labeled main() so I have to assume it's the entry point for your (console mode) program. A console mode Win32 program doing graphics???

I have to take a wild guess at this. Is your main thread not handling the UI? In fact, it's this secondary thread that handles the UI (via GLUT?), and updating of the graphical display? That's really unusual. How come you didn't write a Win32 windowed app instead? You've got a console window hanging around that you don't even need. Is this how GLUT works?? It requires a console mode Win32 app??? How bizarre.

Can't you just make a Win32 windowed app as so?:

```
int WINAPI WinMain(HINSTANCE hinstExe, HINSTANCE hinstPrev, LPSTR lpszCmdLine, int nCmdShow)
{
   // read problem definition from a file
    read_problem();

    // plot initial configuration
    plotting::figure(1);
    plotting::plot( x, y );

    // Initialize/present your GLUT interface, and call a
    // function that draws your graph
    plotting::draw_my_graph();

    // run GLUT's "message loop" right here. This is the UI
    // thread. When it's time to update the graph, call do_graph().

   return(0);
}

void do_graph(void)
{
   time_integrate( t, t + t_delta );

   plotting::plot( x, y );
   plotting::drawnow();
   plotting::draw_my_graph();

   t += t_delta;
}
```

Do you even need a secondary thread?

---

### Post by c174 on 2007-11-18
> **j_g said:**
> Well, I don't know about aks44, but I'm really confused by these code snippets. You've got this labeled main() so I have to assume it's the entry point for your (console mode) program.

Yes, main() is the entry point for the console program.

> **j_g said:**
> A console mode Win32 program doing graphics???

It might sound bizarre, but it is actually something that can be very useful. The console program is a "simulation program", e.g. some mathematical model of physics. These types of programs rarely have a graphical interface - and if they have, it is added as a last step, once the simulation program has been fully accepted with respect to which INPUT and OUTPUT is available for the user.

Therefore these programs often read a problem definition file and then writes the results into an output file. The data is then postprocessed by some other program. For example Matlab (if one has a license) or GnuPlot.

However, it is VERY useful to be able to plot data on the fly as the simulation is carried out (e.g. debugging/find out why or when a simulation blows up). Note that the plotting commands come from the simulation program- not through callbacks from the window environment.

> **j_g said:**
> I have to take a wild guess at this. Is your main thread not handling the UI?

No :) The main thread does the computations.

> **j_g said:**
> In fact, it's this secondary thread that handles the UI (via GLUT?), and updating of the graphical display?

The second thread fires up GLUT by calling glutMainLoop(). This function never returns, but it brings at least 1 window to life. This window recieves user events, such as rescaling of the window. Callback functions are assigned in order to redraw the contents of the window, handle mouse events for zooming in or out, etc.

> **j_g said:**
> That's really unusual. How come you didn't write a Win32 windowed app instead?

I don't know the Win32 API and I also want my program to run on both Windows and Linux. Only a few platform dependent functions are needed for the threads and sleep function, since GLUT is already cross-platform. Maybe I could even get around these platform issues by using Boost-threads(?) At the moment I'm not into the Boost library, so it'll have to wait.

> **j_g said:**
> You've got a console window hanging around that you don't even need. Is this how GLUT works?? It requires console mode Win32 app??? How bizarre.

Well, the console window is nice to have. It gives a simple place to print out different values from the simulation. Also simple user interaction becomes available. I don't think GLUT requires a console mode. But so far I only write console programs :)

> **j_g said:**
> Can't you just make a Win32 windowed app as so?:

```
int WINAPI WinMain(HINSTANCE hinstExe, HINSTANCE hinstPrev, LPSTR lpszCmdLine, int nCmdShow)
{
   // read problem definition from a file
    read_problem();

    // plot initial configuration
    plotting::figure(1);
    plotting::plot( x, y );

    // Initialize/present your GLUT interface, and call a
    // function that draws your graph
    plotting::draw_my_graph();

    // run GLUT's "message loop" right here. This is the UI
    // thread. When it's time to update the graph, call do_graph().

   return(0);
}

void do_graph(void)
{
   time_integrate( t, t + t_delta );

   plotting::plot( x, y );
   plotting::drawnow();
   plotting::draw_my_graph();

   t += t_delta;
}
```

Do you even need a secondary thread?

I'm not sure how this would work. If "do_graph" is supposed to trigger the simulation it is not a good idea. The simulation might take hours, so the window would be irresponsive for a long time during a single redraw request. I have to say though, that I'm not sure I understood your design correctly, so maybe it actually would work fine (but not platform independently).

---

