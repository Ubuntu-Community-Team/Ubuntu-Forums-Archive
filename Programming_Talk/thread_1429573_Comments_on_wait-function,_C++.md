---
title: "Comments on wait-function, C++"
date: 2010-03-14
forum: Programming Talk
---

### Post by Dromedar on 2010-03-14
Hello

Here is a cool way of wait for some time to go by:

// Wait for given time
//
// Params:  seconds    Time in seconds to wait
//
void CUtility::Wait(int seconds)
{
     clock_t startTime = clock();
     while((clock()-startTime)/CLOCKS_PER_SEC < seconds) {}
}

what do you guys think ? Is there something to improve or something to be expecially proud of ?

This piece of code was used in a tcp-server software, which supposed to serve thousand or simultanious connections. The guy who wrote the software wanted me to check if there is something to imporve, because there were data losses even when there were only 5 connections.

Please comment on the implementation of wait-method. Ironic that this sort of wait is not needed at all but we eneded up on arguing about the implementation.

---

### Post by MadCow108 on 2010-03-14
it burns cpu cycles while waiting which could be used for more useful tasks.
as you seem to just need second resolution, sleep or usleep should work just as fine without running at 100% cpu doing nothing.

Also that the loop is empty may result in problems depending on the implementation of clock.
If it is implemented as a pure function the compiler may remove the loop during optimization.
I'm not sure the standard requires clock to be a function with side effects.

---

### Post by n0dix on 2010-03-14
You can avoid '{ }' in the while body with simply ';'.

---

### Post by Dromedar on 2010-03-14
> **MadCow108 said:**
> it burns cpu cycles while waiting which could be used for more useful tasks.
as you seem to just need second resolution, sleep or usleep should work just as fine without running at 100% cpu doing nothing.

Yes this is the most important thing that needed to be changed. It would be a funny function if there would be sleep(1) in the while loop (this would cause a bit longer wait:D)

> **MadCow108 said:**
> 
Also that the loop is empty may result in problems depending on the implementation of clock. If it is implemented as a pure function the compiler may remove the loop during optimization. I'm not sure the standard requires clock to be a function with side effects.
I think clock side efect is to return an approximation of processor time used by the program. Can you show me example of function with no side effect (excluding function returning void) ?

I did not say directly that the program was multithreaded (actually it created new process for each connection by calling fork()). What happens if 2 processes call wait(10) roughly at the same time ? How long (in real time) does both process wait ? :o Does it depend on how many processors/cores there is in the system ? -- Actually I don't know how clock() works when there is two or more cores. But probably not what coder expected...

Note that the time can wrap around. On a 32bit system where CLOCKS_PER_SEC equals 1000000 this function will return the same value approximately every 72 minutes. -> This can cause a bit longer wait than expected. That is when clock is about to wrap and wait is called. While wiating return value wraps to 0 or -1*2^31. Then we start to wait a looong time:popcorn:

> **n0dix said:**
> 
You can avoid '{ }' in the while body with simply ';'. 	


True. But what would this change in the program itself ?


To me this is one of the stupidiest code I have ever seen. Couple of lines code and so many mistakes. Simple sleep(n) would do. But like I said the whole wait concept in the program was unneccessary. It is ironic that we end up arguing about function which is not needed. After all the whole program needs to be rewritten.

---

### Post by n0dix on 2010-03-14
> **Dromedar said:**
> 
True. But what would this change in the program itself ?


It's important to me, i don't like to write more code if it isn't necessary.

---

### Post by soltanis on 2010-03-14
Even if the compiler did let that code run it would be horribly inefficient. Burning CPU cycles continuously to take up time is not a good method of waiting around.

Instead you should consider using sleep or usleep to wait small amounts of time which also has the benefit of handing allocated CPU time back to the kernel so that other programs on the system can run.

Are you by chance running in non-blocking mode? If you are, that's also generally a terrible idea; consider using select to wait for connections or data to read on sockets.

TCP servers that use select (sometimes, but not always, with multiple processes) tend to have the best performance (moreso than servers that only fork or use threads).

---

