---
title: "specifiying % of cputime for pthreads"
date: 2008-05-06
forum: Programming Talk
---

### Post by kikazaru on 2008-05-06
Is it possible to specify the relative percentage of cputime a pthread will be granted?

I want to guarantee that the main thread always gets say at least 50% of the cpu time alloted to my program, and the total cpu time alloted to all the parallel threads open at any one time does not exceed the remaining 50%.

If this is possible using pthreads, could you explain to me how to set the thread priorities in terms of their relative time slices occupying the cpu?

Thanks!

---

### Post by Zugzwang on 2008-05-06
Note that the actual percentage of CPU time allocated to your program depends heavily on the internals of the scheduler. Since that may change from kernel version of kernel version, that task looks quite tough (although these internals are well-documented). My best advice would be to use sleep functions accordingly.

Just out of curiosity: Why do you want to do so?

---

### Post by kikazaru on 2008-05-06
Thanks for the reply! 

I have been trying to find some documentation that explains how I can break up the CPU usage but I havn't got further than, as you point out, "implementation specific". I'm not too desperate to get an exact percentage of the CPU but I want to ensure that one thread retains at least around 50% and the other threads get some reasonable share of whats left. Any idea where I can find out where this stuff is described, or even some example code?

I'm writing a flight simulator, and I want to retain a certain threshold of processing for the main thread which does integrations and rendering and so on. I also want to farm out certain tasks for parallel processing so they don't slow down the simulator even though they may take a while to compute in the background, e.g., heavy computational geometry processing occurring when a polyhedral object is blasted into pieces -the fragmentation will be prepared over a second or so, and then the original object will be replaced with it's fragmented pieces, but the simulator continues smoothly while the extra processing is going on in the background. I don't want to have to punctuate all the heavy processing functions with sleep checks.

---

### Post by Zugzwang on 2008-05-06
I would say the usual way of doing this is having your rendering thread compute one frame and sleeping util the next frame is to be rendered, similarly with the physics/game control thread. These two frames should get a high priority, whereas your explosion pre-computation thread gets a low priority but is never sleeping. Obviously, this would require the usage of some fixed frame rate.

Your 50/50 rule is by the way not so good if you have a multi-core CPU. ;-)

I know that that may be not quite what you want. Sorry, can't help you any further here.

---

### Post by kikazaru on 2008-05-06
Thanks!

---

### Post by dwhitney67 on 2008-05-07
> **Zugzwang said:**
> Note that the actual percentage of CPU time allocated to your program depends heavily on the internals of the scheduler. Since that may change from kernel version of kernel version, that task looks quite tough (although these internals are well-documented). My best advice would be to use sleep functions accordingly.

Just out of curiosity: Why do you want to do so?
Use the sleep functions??  I hate to say this, but that is probably the least effective advice one could give!

The better thing to do is to set up the scheduling that you wish your threads to employ, including the priority of the threads.  You can set the priority at thread creation or after the thread is already running.  Here's some sample code on how to do the latter:
[PHP]// Thread priority is set at thread creation.  This function allows
// priority changes after thread creation. 
//
void set_priority( int threadID, const unsigned int priority )
{
  // Use the param for this particular thread so that other possible
  // fields of the data structure will not be changed.  With pthread, it
  // is a safer practice.
  //
  struct sched_param param;
  int                priority_range = sched_get_priority_max(SCHED_OTHER) -
                                      sched_get_priority_min(SCHED_OTHER);

  if ( priority > priority_range )
  {
    param.sched_priority = sched_get_priority_max(SCHED_OTHER);
  }
  else
  {
    param.sched_priority = sched_get_priority_min(SCHED_OTHER) + priority;
  }

  // The pthread function pthread_setschedparam allows policy change.
  // However, on Solaris, only SCHED_OTHER is supported.  Other policy
  // values will result in error ENOTSUP. That is why we simply specify
  // SCHED_OTHER as the second parameter. 
  //
  if ( pthread_setschedparam( threadID, SCHED_OTHER, &param ) != 0 )
  {
    throw std::runtime_error( "Set Sched Param Failed for Priority" );
  }
}
[/PHP]

---

### Post by Zugzwang on 2008-05-07
> **dwhitney67 said:**
> Use the sleep functions??  I hate to say this, but that is probably the least effective advice one could give!


Why is that the case? Changing the priorities might not be wise in the OP's case because that might cause the painting thread to update the screen more often than necessary while the background pre-computation task might not get its work done on time. On the other hand, if the priorities for the background process are too high, then the "Frames per second" (FPS) rate will decrease. Of course the OP can set the priorities such that it works fine on his/her machine, but that's not very portable. The sleep-version should be (except for the case that there's simply not enough computation power to do the explosion pre-computation in the background, but then the FPS rate will have to drop anyway).

---

### Post by kikazaru on 2008-05-11
Thanks indeed for your advice!

---

### Post by joe_bruin on 2008-05-12
Realistically, pthreads (and the Linux kernel) were not designed to do the CPU percentage split in the way that you want.  Besides, what if your game runs on a faster or slower CPU?

Zugzwang gave you pretty much the correct answer.  You need a high priority thread sleeping until it has work to do, in which case it preempts the other threads and does its thing (like drawing a frame).  Now, if timing becomes a serious issue, this thread may need to keep track of how long it takes to draw a frame, and how much time there is in between, and maybe start dropping frames if you don't think there's enough time left for the others.  But there is no built in system that will do this for you.

---

