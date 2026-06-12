---
title: "Ubuntu running out of threads?"
date: 2006-04-11
forum: Programming Talk
---

### Post by kBanshee on 2006-04-11
I'm trying to run a program (c++ under bash) that creates about 250+- threads. This works perfectly on Windows XP and Mac OSX, but under Ubuntu it crashes my entire system after the creation of about 180 threads. I presume it has something to do with the maximum amount of threads that are allowed by the kernel? Is there anywhere I can check/change this amount ?

---

### Post by draenor on 2006-04-11
Sounds strange, I don't know personally about Ubuntu but I have spawned over 1000 threads on a debian system, and that worked fine but for the computer running a bit slow :P

---

### Post by LordHunter317 on 2006-04-11
Relevant code might be helpful.  You can spawn more threads that that, unless you hit a ulimit (which you won't by default).

---

### Post by kBanshee on 2006-04-11
There's not much relevant code to post. I just create 250 objects which startup a boost thread:

// Constructors and Destructor
TabuDayScheduler::TabuDayScheduler( SchedulerBeliefs beliefs) : Scheduler(beliefs) {
                                    
  // Run the thread
	boost::thread tid1( thread_adapter::thread_adapter(&TabuDayScheduler::runWrapper, this) );		                                    
}

The run function doesn't do much more than sleep the thread at this point.

My system just locks up. Apache, terminals and X stop responding. If I call it through putty, the echo freezes. If I control^C at that point, the system continues like nothing happened.
Ulimits are all set to unlimited. I'm running Dapper BTW.

The CPU and MEM usage remain low during this, so the problem shouldn't lie there. Is there any way to monitor the amount of free threads?

---

### Post by LordHunter317 on 2006-04-11
[QUOTE=kBanshee]My system just locks up. Apache, terminals and X stop responding. If I call it through putty, the echo freezes. If I control^C at that point, the system continues like nothing happened.
Ulimits are all set to unlimited. I'm running Dapper BTW[/QUOTE]Sounds like your triggering hte fork() bomb avoidance code to me.  Try adding a delay between the thread creation and see what happens.  Make sure these threads are really sleeping and you're not spinning or something else equally evil.

---

### Post by kBanshee on 2006-04-11
[QUOTE=LordHunter317]Sounds like your triggering hte fork() bomb avoidance code to me.  Try adding a delay between the thread creation and see what happens.  Make sure these threads are really sleeping and you're not spinning or something else equally evil.[/QUOTE]
Well, they work fine under XP and MacOs, so I think the code is good. Offcourse the Boost library could be at fault but I think that is unlikely. I'll try to add a delay and see what happens.

When I was just testing I got a boost thread resource exeption. I never had that before, so it could be a freak occurance. What does the fork() bomb avoidance code do exactly?

---

### Post by kBanshee on 2006-04-12
It appears that I ran out of context switches. Slowing things down a bit (more sleeping) caused the problem to go away completely. This problably didn't happen on  my XP an OSX machine, because they are faster and where able to cope with the amount of context switching I generated.

---

### Post by LordHunter317 on 2006-04-12
[QUOTE=kBanshee]It appears that I ran out of context switches.[/quote]No, you cannot run out of context switches.  It isn't a quota parameter and I'm not even sure it's tracked on a per-process basis at all. 

> Slowing things down a bit (more sleeping) caused the problem to go away completely.Which means you were likely tripping fork() bomb protection.

---

### Post by kBanshee on 2006-04-12
[QUOTE=LordHunter317]No, you cannot run out of context switches.  It isn't a quota parameter and I'm not even sure it's tracked on a per-process basis at all. 
Which means you were likely tripping fork() bomb protection.[/QUOTE]

What I meant was that I created so many context-switches that my system couldn't handle them in realtime, causing the system to freeze completely with 100% CPU Usage.

About the fork bomb protection: I think it's unlikely it was tripped because protection should PROTECT my system, which obviously didn't happen.

---

### Post by LordHunter317 on 2006-04-12
[QUOTE=kBanshee]What I meant was that I created so many context-switches that my system couldn't handle them in realtime, causing the system to freeze completely with 100% CPU Usage.[/quote]Thread creation shouldn't cause many context switches at all.  Very few, in fact.  And you said the CPU usage was minimal.

> About the fork bomb proection: I think it's unlikely it was tripped because protection should PROTECT my system, which obviously didn't happen.It's hardly perfect and it frequently causes system to stop responding or respond slowly.  Which is what would happen under a fork() bomb, so...

---

### Post by kBanshee on 2006-04-13
[QUOTE=LordHunter317]Thread creation shouldn't cause many context switches at all.  Very few, in fact.  And you said the CPU usage was minimal.
[/QUOTE]

True, but a lot of threads that are waking up do. And I thought the CPU usage was minimal, but apperantly top was not displaying things correctly (probably because it had no more cpu-cycles to run).

---

### Post by LordHunter317 on 2006-04-13
That also makes no sense.  No one can help you troubleshoot your problem because you've yet to be truthful or consistent with your description of your code or your description of what you saw.  Stop assuming and post straight observations and facts.

---

### Post by kBanshee on 2006-04-13
I'm sorry if you feel you are talking to a wall, I've got the same on this side. As I said a few posts before: I've allready solved the problem and it wasn't Ubuntu's fault. I'm still not sure what the problem was, but I think I was overloading the system by creating to many highly active threads. The delay proces you suggested made me realize that.

About your second point: I'd like to post straight observations and facts, but no-one has yet suggested a way to me how I can monitor threads / the entire system when ubuntu is grinding to a halt.

---

### Post by LordHunter317 on 2006-04-13
[QUOTE=kBanshee]As I said a few posts before: I've allready solved the problem and it wasn't Ubuntu's fault.[/quote]And I said as much originally.

>  I'm still not sure what the problem was, but I think I was overloading the system by creating to many highly active threads.Which isn't what you said you were doing originally, hence the confusion.

> The delay proces you suggested made me realize that.If the threads are running continually and not sleeping, then delaying between thread invocations shouldn't have solved the problem.  There would have to be a lot of IPC for that to have solved it.

> About your second point: I'd like to post straight observations and facts, but no-one has yet suggested a way to me how I can monitor threads / the entire system when ubuntu is grinding to a halt.You haven't even given us a consistent story about your code, so what you're observing on the system is irrelevant until you tell us what your code is attempting to do.

---

