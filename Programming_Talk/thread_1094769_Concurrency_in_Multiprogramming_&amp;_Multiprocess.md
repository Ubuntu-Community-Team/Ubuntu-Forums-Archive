---
title: "Concurrency in Multiprogramming &amp; Multiprocessing"
date: 2009-03-12
forum: Programming Talk
---

### Post by cs_kid on 2009-03-12
I just recently finished a homework assignment dealing with threads, and now I'm left wondering a few things....

K, I know the difference between multiprogramming(running multiple programs on single processor machines) and multiprocessing(running multiple programs on multiple processors), and am aware that multiprogramming and multiprocessing both create the same problems with respect to concurrency......but what other differences are there?

It only makes sense that there would be ...more differences, in addition to a single vs multiprocessor.... 

please tell me if I'm thinking too deeply into this...

---

### Post by eye208 on 2009-03-13
Multiprogramming went out of fashion long ago. It was replaced by multitasking (either cooperative of preemptive). The difference between cooperative and preemptive MT was a big one, because the former required programmers to pass CPU control to other tasks voluntarily (e.g. by inserting sleep() calls into loops). Otherwise they would block all other tasks and the system would effectively be turned into a single-tasking one.

Preemptive MT operating systems perform task switching without the programmer's cooperation. They can run CPU-intensive tasks at lower priorities to prevent an overall system slowdown. UNIX, Linux, Amiga OS and Win32 are preemptive MT systems. Win16, Mac OS 9 and Risc OS were cooperative MT systems.

Although multiprocessing affects parallelism in computing, it is not really related to multitasking. Multiprocessing is a hardware property, not an operating system property. It does not turn a single-tasking OS into a multitasking one. Multiprocessing is relevant to kernel developers but not to application developers.

---

### Post by tneva82 on 2009-03-13
> **eye208 said:**
> Preemptive MT operating systems perform task switching without the programmer's cooperation. They can run CPU-intensive tasks at lower priorities to prevent an overall system slowdown. UNIX, Linux, Amiga OS and** Win32** are preemptive MT systems

Though bolded one isn't neccessarily that good. Had to fix excel script which ate up 100% of processor cycle(not kidding). Without sleep() calls here and there the second macro booted up processor cycle went to 100% and the overall performance of machine started to lag.

Tiny sleep there and computer could actually be used for other things while script was running.

---

### Post by CptPicard on 2009-03-13
Conceptually at least and from a high-level process/thread perspective, I can't really think of a difference. If you think of it, a thread will not know at which times it is running or not, and what sort of other threads there are around in addition to itself. Shared resources can change *at any time* from the thread's own timeline's POV. The idea here is that any execution order of multiple threads on single CPU could just as well have been distributed over many CPUs, and the effect to the view on things to one thread does not change. Vice versa, you can take parallel execution on many CPUs and interleave them on one, and because the executing/not executing distinction of the thread is invisible to the thread itself.

It all boils down to the observable state changes of mutual state. That's what carries the information, and that is the problem in concurrency.

A lot of the practical magic needed there is handled by hardware (most importantly memory access from many CPUs), and then there are kernel implementation issues (scheduler has more cores to work with, synchronization primitives/IPC need probably some changes), but especially if you assume existing and working OS concurrency basics, it should be all the same.

---

### Post by eye208 on 2009-03-13
> **tneva82 said:**
> Though bolded one isn't neccessarily that good. Had to fix excel script which ate up 100% of processor cycle(not kidding). Without sleep() calls here and there the second macro booted up processor cycle went to 100% and the overall performance of machine started to lag.

Tiny sleep there and computer could actually be used for other things while script was running.
Running at 100% CPU is not a bug if the program is actually doing something useful. Slowing it down with sleep calls makes no sense.

For example, if you encode a video, the CPU will run at 100% for hours. This is not a bug. If such a task is assigned a priority below normal, it won't affect system responsiveness at all because high priority tasks can interrupt it at any time. However, if there is nothing else to do, the program _should_ run at 100% CPU instead of wasting time in sleep calls.

On Windows you can assign priorities using the task manager. Lowering Excel's priority would have fixed your script problem.

---

### Post by tneva82 on 2009-03-13
> **eye208 said:**
> Running at 100% CPU is not a bug if the program is actually doing something useful. Slowing it down with sleep calls makes no sense.

It does if program causes everything else to lag down...Including mouse! Using computer to anything else would be major pain in the *** when even simply moving mouse from point A to point B is going to take a while just for cursor to move...

And yeah you could change priorities but not particulary user friendly if you have to switch excel priority down everytime they need that script. Much more effective to sleep it for a while when it doesn't need 100% CPU cycle for itself anyway. It's not like it's doing some heavy math that needs to be done ASAP.

---

### Post by eye208 on 2009-03-13
> **tneva82 said:**
> And yeah you could change priorities but not particulary user friendly if you have to switch excel priority down everytime they need that script.
You can change the priority from within the script.

> Much more effective to sleep it for a while when it doesn't need 100% CPU cycle for itself anyway.
No. The macro will just take longer to complete. If it didn't take long, you wouldn't notice it in the first place.

sleep() in a preemptive multitasking system is not the same as sleep() in a cooperative MT system. The latter will just pass on CPU control to the next task for an unspecified amount of time and may in fact return immediately if there is nothing else to do. The former will halt execution for a specified amount of time even if the system is completely idle otherwise.

---

### Post by tneva82 on 2009-03-13
> **eye208 said:**
> No. The macro will just take longer to complete. If it didn't take long, you wouldn't notice it in the first place.

Since it is "done" only when user TELLS it to stop it hardly matters ;-) Sure it might take 1ms longer to get things done when it needs to act but who notices that? When it does something it completes it faster than human can notice. Sleep or not.

We aren't talking about some 3d-game where simple sleep middle of program could cause noticable drop in FPS. We are talking about script that is faster-than-human-can-see wether there's 1ms sleep in there or not. What did change was however that CPU cycle went from 100% to <1% without additional programs.

The slowness was noticed because computer was effectively unusable while macro was running. Mouse: Lags. Keyboard input: Lag. Telling macro that your job is now done for example would take up ages and that's just clicking one button and pressing enter(or clicking second button)...

---

### Post by eye208 on 2009-03-13
> **tneva82 said:**
> Since it is "done" only when user TELLS it to stop it hardly matters ;-) Sure it might take 1ms longer to get things done when it needs to act but who notices that?
So the macro was using 100% CPU doing nothing but waiting for input? #-o

I guess they don't teach event-based programming at Excel classes...

---

### Post by tneva82 on 2009-03-13
> **eye208 said:**
> So the macro was using 100% CPU doing nothing but waiting for input? #-o

Waiting for user input or changing data to excel sheets. But stops only when user tells him.

Hey I didn't write it. I just had to get it working without grinding down whole computer with zero experience with Excel before this ;-) And the worksheet itself was ad-hoc thing which was done quickly by non-expert excel coders and then sat there with nobody having time to improve it.

---

### Post by anthonytw on 2009-03-24
> **cs_kid said:**
> K, I know the difference between multiprogramming(running multiple programs on single processor machines) and multiprocessing(running multiple programs on multiple processors), and am aware that multiprogramming and multiprocessing both create the same problems with respect to concurrency......but what other differences are there?

Differences with respect to concurrency:

On multiprocessing machines, generally individual cores have their own private cache. If a thread modifies some portion of shared memory, that change is apparent in its cache but not necessarily in the main system memory, at least not until that page is written back (either because it is swapped out or because the processor decides it's time to commit the changes). This issue must be handled by the OS to make sure threads on other processors are using the recent changes. This is not an issue you would find on a uniprocessor machine.

Additionally, with respect to concurrency, synchronization is a bit easier on uniprocessor machines because it can be handled by the kernel who has a complete overview of the system and may make intelligent decisions handling thread and process events. On a machine with multiple cores, no single agent has a complete view of the entire system: each core only know what's on its own plate. This is an issue an OS on a multiprocessor machine has to deal with.

Those issues above generally require both hardware and kernel efforts to ameliorate.

---

### Post by slavik on 2009-03-24
> **anthonytw said:**
> Differences with respect to concurrency:

On multiprocessing machines, generally individual cores have their own private cache. If a thread modifies some portion of shared memory, that change is apparent in its cache but not necessarily in the main system memory, at least not until that page is written back (either because it is swapped out or because the processor decides it's time to commit the changes). This issue must be handled by the OS to make sure threads on other processors are using the recent changes. This is not an issue you would find on a uniprocessor machine.

Additionally, with respect to concurrency, synchronization is a bit easier on uniprocessor machines because it can be handled by the kernel who has a complete overview of the system and may make intelligent decisions handling thread and process events. On a machine with multiple cores, no single agent has a complete view of the entire system: each core only know what's on its own plate. This is an issue an OS on a multiprocessor machine has to deal with.

Those issues above generally require both hardware and kernel efforts to ameliorate.
you are slightly incorrect here. whatever is in the L2 cache of an individual CPU makes it back to the memory is decided by the hardware and what type of caching is implemented, not the OS.

---

### Post by anthonytw on 2009-03-26
> **slavik said:**
> you are slightly incorrect here. whatever is in the L2 cache of an individual CPU makes it back to the memory is decided by the hardware and what type of caching is implemented, not the OS.

Right, but the OS has to handle what happens in between and after hardware write-backs (e.g. resolving conflicts with two processors writing to shared memory at the same time, then other processors requesting that shared memory). That was the issue I was referring to. Like I said, you need software and hardware to handle those issues and practically all other concurrency issues brought about by multiprocessing specifically.

---

### Post by CptPicard on 2009-03-26
But those kernel concurrency primitives are needed anyway regardless of whether you're dealing with multiple CPUs or not, because from application perspective the problems of, say, concurrent access to memory would exist in any case.

For the kernel programmer there may be implementation issues involved, but the outside interface is and should be and work the same...

---

### Post by slavik on 2009-03-26
> **anthonytw said:**
> Right, but the OS has to handle what happens in between and after hardware write-backs (e.g. resolving conflicts with two processors writing to shared memory at the same time, then other processors requesting that shared memory). That was the issue I was referring to. Like I said, you need software and hardware to handle those issues and practically all other concurrency issues brought about by multiprocessing specifically.
switch and test as an atomic instruction :)

---

