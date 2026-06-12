---
title: "C++, move counter to begining of program like in Assembly"
date: 2011-07-02
forum: Programming Talk
---

### Post by scu-ba-de-buntu on 2011-07-02
Hey, I am writing an open-source game that is to be true to 16bit genesis type games. I am writing it in C++. Is there a (Must be SAFE) way to move the counter to the beginning of the binary to effectively "Reset" the game? You can do this in assembly but its not the language I'm working in.

thanks

---

### Post by unknownPoster on 2011-07-02
Games are event driven. When the user "resets" the game, just restart the game loop. 

It seems as if you're over-complicating this.

---

### Post by scu-ba-de-buntu on 2011-07-02
still, it is what I would like to do

---

### Post by ve4cib on 2011-07-03
The only way I can think of to do this in a "pure" way would be to use inline assembly:

```

asm volatile("<appropriate assembly load/store instructions here">::);

```

It's hacky, and not particularly safe (especially if you're not 100% sure what you're doing and why).  But it's the only way I know of to manipulate the CPU registers in C or C++.  The obvious downside is that it locks you into one architecture.  To allow the program to be compiled for i386, arm, PowerPC, Atmel, etc... you'd need a lot of #ifdef directives and the appropriate assembler code for each architecture.

A much, much better way would be to do what UnknownPoster suggested: simply reset the program's main loop.  Unlike an old 16-bit console, modern computers have an OS that handles things for you.  We don't need a hardware-driven interrupt that resets the CPU's program counter.  You're making things needlessly complex, for no real gain as far as I can tell.

As a middle-ground approach, you could have two threads/processes.  One is the main game loop, and the other simply waits for your "reset" event to fire.  If that ever fires then you kill the game thread/process, and start a new one.  The visible result will be the same as resetting the program counter, but you let the OS deal with the concurrency, resource management, and hardware registers.

---

### Post by unknownPoster on 2011-07-03
Assuming you are using the OOP features of C++, you could also design your code such that the current running instance of your game is deleted and new instance is created when the reset interrupt is sent.

---

### Post by ve4cib on 2011-07-03
> **unknownPoster said:**
> Assuming you are using the OOP features of C++, you could also design your code such that the current running instance of your game is deleted and new instance is created when the reset interrupt is sent.

Wouldn't that still necessitate two threads/processes though?  One to run the game (the running instance), and another to listen for interrupts and delete the running instance when necessary (either a thread running within that same instance, or a separate entity)?

---

### Post by unknownPoster on 2011-07-03
> **ve4cib said:**
> Wouldn't that still necessitate two threads/processes though?  One to run the game (the running instance), and another to listen for interrupts and delete the running instance when necessary (either a thread running within that same instance, or a separate entity)?

Not necessarily, but again it depends on how the OP has his classes set up. Just a quick example:

Assume you have 3 states: "running", "quit", "restart".

Some "Manager" class waits for the states to change and then takes appropriate action.

I can provide a working example, but I'd rather not pollute the thread.

---

### Post by ve4cib on 2011-07-03
> **unknownPoster said:**
> Not necessarily, but again it depends on how the OP has his classes set up. Just a quick example:

Assume you have 3 states: "running", "quit", "restart".

Some "Manager" class waits for the states to change and then takes appropriate action.

I can provide a working example, but I'd rather not pollute the thread.

But even then you still need some way of flipping between the "Manager" class and the game instance.  Either two threads/processes (like I described above), or your game would need to constantly poll the input to see if the reset message has been sent.

Your post simply further reinforces the idea that at least two concurrent lines of execution are necessary as far as I can tell.  Here's how I'm understanding the multi-thread approach (using some pseudo-code):

**Manager class (main)**
```

for(;;)
{
    state = checkState();

    switch(state)
    {
    case RESET:
       delete gameInstance;
    case START:
       gameInstance = new GameInstance();
       break;
    case CONTINUE_GAME:
       break;
    ...
    }

    sleep(100);
}

```

**GameInstance**
```

class GameInstance
{
    private Thread gameThread;

    public GameInstance()
    {
        this.gameThread = new Thread(runGame);
        this.gameThread.start();
    }

    public ~GameInstance()
    {
        this.gameThread.stop();
        delete this.gameThread;
    }

    private void runGame()
    {
        // play the actual game, remembering to call sleep
        // every once in a while when it's convenient
        ...
    }
}

```

The Manager class contains main, and simply loops, checking the state.  If the reset command comes in we delete the current instance and create a new one.

Creating a new instance spawns a new thread in which the game runs.  (This could also be a new process, at which point we don't need to worry about sleeping as much, since the OS will take care of switching between processes.)  The game thread is completely self-contained and isolated from the Manager.  The only interaction between the two is when the Manager creates or destroys the GameInstance, according to the program's state.

If you (or anybody else) can show how you can run the game in one class, and listen for the reset command in another, without using concurrency (and without polluting the game class's code with constant polling) I'd be very interested to see how you'd pull that off.

---

### Post by unknownPoster on 2011-07-03
By nature, games must constantly poll for user input, so adding that functionality is not "polution" as you call it.

Yes, the manager method I described is "multi-threaded" but the programmer doesn't have to explicitly concerned with threads.

---

### Post by Arndt on 2011-07-03
> **scu-ba-de-buntu said:**
> Hey, I am writing an open-source game that is to be true to 16bit genesis type games. I am writing it in C++. Is there a (Must be SAFE) way to move the counter to the beginning of the binary to effectively "Reset" the game? You can do this in assembly but its not the language I'm working in.

thanks

One thing you can do which may have the effect you want is to "exec" the same program, with the same arguments: something similar to

```
execv("progname", argv);
```

---

### Post by ve4cib on 2011-07-03
> **unknownPoster said:**
> By nature, games must constantly poll for user input, so adding that functionality is not "polution" as you call it.

I think we're using the term "polluting" in slightly different ways here.  Obviously you need to check the inputs somehow.  The pollution comes from how and where you're doing that polling.  And trying to do it without concurrency will pollute your code and make it much harder to maintain.

If you were to try write a game with a single thread then you would have to insert your polling code into almost every function -- including ones that have nothing to do with I/O.  Imagine you have a lengthy level loading & rendering routine.  It might take several seconds to execute.  And without concurrency you would need to poll the input *inside* your level-rendering function.  That's messy, and polluting your rendering code with polling that should be implemented elsewhere.

Having a dedicated thread that sits there polling the inputs, acting as necessary if anything was input, and then going to sleep, while keeping your rendering code in a separate thread is the proper way of doing it.  You're not spamming the rest of your code with polling; you're keeping everything nice and self-contained, which leads to cleaner and more maintainable code.

---

### Post by CptPicard on 2011-07-03
Games have been written in a single-threaded fashion for ages (multithreading is a relatively new phenomenon in general) without user input polling code being inserted "everywhere".

A simple single-threaded game main loop

1. Reads user input
2. Decides how the game world reacts to the input
3. Renders the game's visuals.

Your multi-second loading screen is quite a special case, and there are ways to deal with that without having to actually start using threads simply to read user input...

An important point to consider as a downside of using threading is synchronization of user input to whatever is happening in the game world. In a single-threaded game loop, the "cause and effect" of user input is very straightforward. In a multithreaded one, I can foresee issues; in any case, you'll end up with some kind of a queue that the user actions are "effected from" in the game thread, which does not differ all that much from responsive-enough polling so that you're not seeing some really weird delays in gameplay.

---

### Post by ve4cib on 2011-07-03
> **CptPicard said:**
> Games have been written in a single-threaded fashion for ages (multithreading is a relatively new phenomenon in general) without user input polling code being inserted "everywhere".

A simple single-threaded game main loop

1. Reads user input
2. Decides how the game world reacts to the input
3. Renders the game's visuals.

Your multi-second loading screen is quite a special case, and there are ways to deal with that without having to actually start using threads simply to read user input...

An important point to consider as a downside of using threading is synchronization of user input to whatever is happening in the game world. In a single-threaded game loop, the "cause and effect" of user input is very straightforward. In a multithreaded one, I can foresee issues; in any case, you'll end up with some kind of a queue that the user actions are "effected from" in the game thread, which does not differ all that much from responsive-enough polling so that you're not seeing some really weird delays in gameplay.

You make a good point.  I hadn't thought of it like that before.

I work with realtime systems and robotics, where asynchronous inputs from sensors always tend to be shunted to their own threads.  Controlling the motors in a walking motion takes several seconds, but you need to constantly check the sensors to make sure you haven't fallen over, walked into anything, and the like.  Doing that in a single thread is impossible without making the code horribly messy.

I hadn't even considered the fact that rendering a single frame in a game could be done quickly enough that you could be polling the input between frames.  Thanks for pointing that out.  :)

---

### Post by psusi on 2011-07-03
What does the location of a variable have to do with performing a game "reset"?

---

### Post by ve4cib on 2011-07-03
> **psusi said:**
> What does the location of a variable have to do with performing a game "reset"?

I think what the OP means is resetting the Program Counter (a register on the CPU).  The Program Counter basically points to the instruction currently being executed (or the next one to execute, depending on the architecture).  By resetting the Program Counter to point back to the first instruction of a program you can start executing it all over again, without having to reload it into memory.

It's not something most programmers ever have to worry about; the OS deals with manipulating the CPU registers.  The only time most programmers ever need to deal with it is when they're working with embedded systems when there is no OS, or when they're writing/maintaining an OS.

---

### Post by nvteighen on 2011-07-04
IMO, the best approach is the usual one for this cases in C++ and OOP languages:

0. Encapsulate the game in a class (it doesn't need to be a formal singleton, but the idea is that there should be just one instance of this game class).
1. The game class constructor should state the game's inital state, though I'd create some auxiliary method that could be called by the constructor and the reset method (see 3).
2. Use a game loop to control input/output. The game class should be instantiated inside this loop.
3. Resetting can be achieved in two possible ways: either by discarding the game object and constructing a new one (but this may leak memory if you do it wrongly) or by creating a reset method that effectively resets the game's state.

---

### Post by CptPicard on 2011-07-04
> **ve4cib said:**
> 
I work with realtime systems and robotics, where asynchronous inputs from sensors always tend to be shunted to their own threads.  


That's cool... and interesting. But does that not lead to information just sitting in some queue and being late to the party when it needs to be reacted to? (My own experience with issues in asynchronous messaging comes from experiments in agent-based computation...)

> 
I hadn't even considered the fact that rendering a single frame in a game could be done quickly enough that you could be polling the input between frames. 

Well both polling and rendering has to be fast enough, because it's a simulation of immediate effect of input on a seemingly real-time world, repeating itself in cycles. Let's say if you only manage to produce 1 FPS of output, I'm not sure you'd really need more resolution in user input either, and if you did have lots of input data from the user during that second, how would you effect that higher resolution onto the game world that you're choking to render even at 1 FPS? :)

And, of course, it's not really any kind of busy-loop polling or anything. In old-school game programming you would just register hardware interrupt handlers for, say, the keyboard, and when that handler would run, it would set some flag in some global input table that you'd process once per iteration of your game loop. Not threading, but just normal async (single-threaded) I/O, which is very light processing-wise.

---

### Post by psusi on 2011-07-04
Oh, right... not heard it called "program counter" in many years.  The Intel nomenclature "instruction pointer" has become far more popular.

And yea, you certainly don't want to be mucking about with that.

---

### Post by cgroza on 2011-07-04
Have not seen any of his code, but if he has to do that, he is facing some major design flaw.

---

### Post by ve4cib on 2011-07-04
> **CptPicard said:**
> That's cool... and interesting. But does that not lead to information just sitting in some queue and being late to the party when it needs to be reacted to? (My own experience with issues in asynchronous messaging comes from experiments in agent-based computation...)

Provided you can empty the queue at a consistent rate (i.e. the latency is consistent) you can usually work around the problem.  If you're looking at sensor data that you know is a few tenths of a second old (as an example) you can still identify trends in the data and make an educated estimation about what the real data should be right *now*.  But that assumes that you can keep the latency consistent.  If some data comes in immediately, and other data waits in the queue for 10 seconds it really does become a nightmare to deal with.

The other obvious concern is being able to process the queue at the same rate (or faster) than the data comes in.  If the queue is full you start losing data, and that's bad.  But that kind of thing happens with hardware interrupt-driven I/O (like most serial ports).

---

### Post by CptPicard on 2011-07-04
Okay, I understand. But of course, in games, it's different -- the "world is yours" and its immediate advacement is of far more concern. You just grab the input that is there and go on...

---

### Post by scu-ba-de-buntu on 2011-07-06
> **ve4cib said:**
> The only way I can think of to do this in a "pure" way would be to use inline assembly:
Well darn I was hoping that there was a cleaner way than that which was similarly low-level.
> **unknownPoster said:**
> Assuming you are using the OOP features of C++....
I am, however I am not really interested in an alternative method.
> **Arndt said:**
> One thing you can do which may have the effect you want is to "exec" the same program
Fork & exec and pipes are all useful, but not really what I am looking for. I think if I bothered to do that, I would just reassign values to my data. 
> **ve4cib said:**
> I think what the OP means is resetting the Program Counter (a register on the CPU). 
> **ve4cib said:**
> It's not something most programmers ever have to worry about; the OS deals with manipulating the CPU registers.  The only time most programmers ever need to deal with it is when they're working with embedded systems
That's correct.

> **psusi said:**
> Oh, right... not heard it called "program counter" in many years.  The Intel nomenclature "instruction pointer" has become far more popular.

And yea, you certainly don't want to be mucking about with that.
I will keep that nomenclature in mind next time I am working with the "instruction pointer". We just called it the counter in class, either throwing in 'program' or 'processor' if clarity was needed.

> **cgroza said:**
> Have not seen any of his code, but if he has to do that, he is facing some major design flaw.
um. thanks? I happen to think my code is rather s3xy. I will be porting this to fairly raw hardware, and the hardware specs just shifts the "instruction pointer" to 0x 0000h. 


> **ve4cib said:**
> Provided you can empty the queue at a consistent rate (i.e. the latency is consistent) you can usually work around the problem.  If you're looking at sensor data that you know is a few tenths of a second old (as an example) you can still identify trends in the data and make an educated estimation about what the real data should be right *now*.  But that assumes that you can keep the latency consistent.  If some data comes in immediately, and other data waits in the queue for 10 seconds it really does become a nightmare to deal with.

The other obvious concern is being able to process the queue at the same rate (or faster) than the data comes in.  If the queue is full you start losing data, and that's bad.  But that kind of thing happens with hardware interrupt-driven I/O (like most serial ports).
Do you think you could add some microcontrollers to do some preprocessing for you? If you throw your data through parallel and have it behave normally going to your que (with some ID of course) and had a real-time controller (1 per group/unit?) figure out pre-sorting, and preprocessing, you could trade for improved resolve-time reliability with a little added complexity.

> **CptPicard said:**
> Okay, I understand. But of course, in games, it's different -- the "world is yours" and its immediate advacement is of far more concern. You just grab the input that is there and go on...
Sure, but actually at a hardware level, most systems have a buffer which is effectively a hw poll() operation. Most modern poll() functions are actually just pulling from memory

---

### Post by Arndt on 2011-07-06
> **scu-ba-de-buntu said:**
> 

Fork & exec and pipes are all useful, but not really what I am looking for. I think if I bothered to do that, I would just reassign values to my data. 


No, what I meant was exec only, no fork and pipes. But it sounds like it is not the solution you want either.

---

### Post by nvteighen on 2011-07-06
I don't get why you don't want other methods except resetting the instruction counter. Is this going to run on some kind of emulator or a Sega console?

If this is going to run on a PC or a modern OS, the ways we've proposed are much more practical.

---

### Post by psusi on 2011-07-06
Yes, the closest thing you are going to get to this that is at all portable is to just exec() yourself.  That effectively restarts your program.

---

### Post by ve4cib on 2011-07-06
> **scu-ba-de-buntu said:**
> Do you think you could add some microcontrollers to do some preprocessing for you? If you throw your data through parallel and have it behave normally going to your que (with some ID of course) and had a real-time controller (1 per group/unit?) figure out pre-sorting, and preprocessing, you could trade for improved resolve-time reliability with a little added complexity.

That doesn't really solve the problem, it just changes it slightly.  If each sensor has its own micro-controller to deal with preprocessing the data you still have to get the actual data (preprocessed or not) from the sensors/preprocessors to the main processor.  This requires some kind of communication line, just like the original sensors did.  The issue remains: how do you get the input from the sensors/preprocessors in a reliable, efficient fashion?

Depending on how the external preprocessors are implemented you could actually wind up making things worse.  Each sensor has its own internal latency, and if the preprocessing takes a variable length of time you could wind up with very uneven gaps between data being sent to the main CPU.

That said, if done well, you could potentially offload a fair bit of the work to the sensors themselves by having them preprocess their own data, leaving the main CPU more clock cycles to do more interesting/useful tasks.

---

