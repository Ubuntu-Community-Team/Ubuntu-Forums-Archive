---
title: "Getting Java code to run cocurrently"
date: 2007-02-24
forum: Programming Talk
---

### Post by NeoChaosX on 2007-02-24
Alright, I've got something of a problem here.

I'm developing a program that simulations handling of processes by a CPU in Java. The basic design is in two classes; one, a Scheduler class that does the simulation itself, and a GUI made with Swing that controls whether to run, pause and stop the simulation.

Here's a simplified version of the Scheduler class:

```
public class Scheduler
{
   public void run()
   {
      paused = false; // pause the simulation
   }

   public void pause()
   {
      paused = true; // resume simulation
   }

   public void stop()
   {
      paused = true;
   }

   public void simulate()
   {
      while(!paused)
      {
         // this is where the simulation is performed
      }
   }

   boolean paused;
}
```

The GUI has buttons that call the run(), pause() and stop() methods. The simulate method is supposed to constantly running and will execute the code in while loop when the boolean paused is false. However, this will only work while the simulate thread is called. I previously had the run() method call the simulate() method, but it turns out it locks up the the GUI when the button that call run() is pressed until simulate() is finished.

So, what I want to do is have simulate() running constantly (or is at least constantly called by the GUI), so that the program is able to respond to pause and stop commands when necessary. Is there a way I can do this?

---

### Post by lnostdal on 2007-02-24
this is very easy in java .. take a look: [http://java.sun.com/docs/books/tutorial/essential/concurrency/](http://java.sun.com/docs/books/tutorial/essential/concurrency/)

---

### Post by Tomosaur on 2007-02-24
The only way to reliably simulate threading is to use threading, which, obviously, is not a simulation at all. You could, I guess, do everything extremely incrementally, with a check_paused() function being called every other statement, something like this:
```

i++;
check_paused();
x++;
check_paused();
System.out.print("s");
check_paused();
System.out.print("l");
check_paused();
System.out.print("o");
check_paused();
System.out.print("w");
check_paused();
System.out.print("\n");

```

But that's just horrible really. Best idea is to just use multi-threading, and to have your pause / stop buttons do just that: pause the threads.

---

### Post by NeoChaosX on 2007-02-24
> **Tomosaur said:**
> Best idea is to just use multi-threading, and to have your pause / stop buttons do just that: pause the threads.

I guess you're right. I'm going to see if I can get my Scheduler class to implement Runnable and run it as it's own thread, and see if it will respond to any calls made to the separate Scheduler class.

---

### Post by dxxvi on 2007-02-25
> **NeoChaosX said:**
> ... the simulate thread ...
what's the simulate thread? how do you call the simulate method? with a button click on your GUI? if it's what you were doing, then your GUI cannot do anything else because that click hasn't finished yet. 

So your scheduler should be a thread and it'll be a little bit good to let your simulation rest for  a while (don't ask them to work so hard :P)
```

while (!pause) {
    Thread.sleep(1);  // don't forget the exception
}

```

---

