---
title: "running a simulation at a defined rate. python."
date: 2011-01-04
forum: Programming Talk
---

### Post by insane_alien on 2011-01-04
Hi, 

I use python to simulate a few systems, in particular their interactions to aid in determining if a change should be made.

up until now i have been content to have these simulations run as fast as they can and throw out a nice big data file for post simulation analysis (also handled by a python script).

This simulation however (sorry i can't give details of it, confidentiality for work and all that) i need to run in real time as we intend to use it for training purposes and our human operators cannot run at 200x realtime.

I tried just putting in a pause for 1 second in the loop thinking the rest of the loop didn't take very long to complete and while it is fine for a few minutes the simulation will take two shifts to complete and by that time its unacceptably unsynchronised with what it should be.

what do i need to do to make the loop execute every second on the second?

---

### Post by MadCow108 on 2011-01-04
you could remember the time at each iteration and have small sleeps(e.g. a few milliseconds) in a loop until current_time > previous_time + 1

---

### Post by insane_alien on 2011-01-04
that seems quite inefficient.

are you sure there isn't a better way of doing this? i thought there would be a good way of doing this from games which have to run at a specified rate otherwise they'll throw off the gaming experience.

---

### Post by insane_alien on 2011-01-04
double post, not sure how it happened, delete please.

---

### Post by talonmies on 2011-01-04
You could try using the python signal module to set up a timer which delivers sigalrm at the appropriate interval and then trap the signal to call your simulation code, having the code sleep otherwise.

---

### Post by MadCow108 on 2011-01-04
> **insane_alien said:**
> that seems quite inefficient.

are you sure there isn't a better way of doing this? i thought there would be a good way of doing this from games which have to run at a specified rate otherwise they'll throw off the gaming experience.

not really, microseconds are aeons for cpu's, you can also get the time to next second and do it with one sleep.
But if you sleep for one second, is efficiency really an issue?

but talonmies suggestion is better, the signal modules has lots of functions for this kind of stuff ( alarm(), pause(), set_wakeup_fd() +select())

or maybe replace the loop with this:
[http://docs.python.org/library/sched.html](http://docs.python.org/library/sched.html)

---

### Post by SaintDanBert on 2011-01-04
I think that what you describe is called ***discreet event simulation***. There are all sorts of online resources and books on this topic. I've been slinging bits for 40 years and sims are among my top-five ways to have fun with code though my hints and tricks have gotten rusty of late.

It seems that you need a stream of events once per second. This is the clock-tick of your simulation. Each event causes a tick-handler within your sim to execute. This tick-handler might then cause a "scheduler" to execute in addition to other sim-time housekeeping.

The "scheduler" could then look at all of the various things to do
(maybe with multiple threads) and launch threads based on various
sim-time or ready-to-run or launch-on-simEvent or whatever.

In a previous life, we built a sim driven by a queue of events.
One run mode had various processes making the events with other processes reading the queue and taking appropriate action. Another, and often most useful mode used special getNextEvent() code to read the event stream from a file. We could salt the file with whatever weird and wonderful patterns of behavior and watch things happen on a per-subsystem basis. [snicker] Since all of *nix is a file, we could even single-step using a pipe from a sendEvent application.

Please return to this thread with whatever you can share of the solution. I'm sure that others will be interested.

Bonne chance,
~~~ 0;-Dan

---

### Post by insane_alien on 2011-01-04
It's not discrete event simulation. It's just that the timestep used is 1 second as this is the minimum temporal resolution to accurately describe the events taking place. 

The only discreet events taking place in the simulation are when an external control action by an operator is activated. be this increasing a flowrate or triggering the emergency shutdown feature. previously, these were fed to the simulation using a file containing a 'script' for instance 

```
5000 FR1 20
```

this would be interpreted by the simulation as 'at timestep 5000 variable FR1 should be set to 20.'

the simulation loop calculates the state of the system after one step using a set of differential equations and an RK4 integrator.

i'm going to try the signal stuff as that looks like what i'm after.

the reason i said the stuf about the micro sleeps seems inefficient is that its going to be waking up the program at a fast rate to do nothing. it just seems messy to me.

---

### Post by insane_alien on 2011-01-05
okay the signal thing works a charm. the loop pauses until it recieves a signal then carries on.

now to slap a GUI on this and it'll be done.

---

