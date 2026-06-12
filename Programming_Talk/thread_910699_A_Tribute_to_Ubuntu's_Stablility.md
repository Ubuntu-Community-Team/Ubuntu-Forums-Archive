---
title: "A Tribute to Ubuntu's Stablility"
date: 2008-09-04
forum: Programming Talk
---

### Post by Envergure on 2008-09-04
In a deliberate attempt to cause a kernel panic, i wrote this (i call it Memleech):
```
/*  ___________________________________________________________________
 *  A program that sucks up all the memory, just to see what happens :)
 */

#include <iostream>
using namespace std;

struct ListItem
{
	long long int a;
	ListItem *Next;
};

int main ()
{
	ListItem *Root;
	
	while (1)
	{
		Root = new ListItem;
		Root = Root -> Next;
	}
	
	return 0;
}

```

At the time i ran this i already had the followinf stuff running:  Firefox (with 4 downloads going), Rhythmbox (playing Mood for a Day by Yes), Geany, PDF Viewer, a Nautilus window, Compiz-Fusion and System Monitor.  I ran Memleech from a terminal.

Here's the results of my experiment :)
1)  My 4G of RAM was sucked up in about 15 seconds.  At this point mouse movement became jittery, but everything still worked OK.
2)  My 4G of swap starts going when RAM is 97.8% used up.  At 50% of swap gone everything is very slow and System Monitor updates sporadically.  Firefox freezes and downloads stop.
3)  At 85-ish % of swap gone Rhythmbox starts sputtering, System Monitor stops updating.  Compiz stops working.
4)  Three minutes after launching Memleech, System monitor updates one last time, showing RAM 99.0% used and swap 100%.  System goes unresponsive for several minutes.  Rhythmbox finally stops.
5)  After several minutes of frozenness Ubuntu came back.  The Terminal window reported "killed".  It took a few minutes to get back on its feet, though.  Firefox came back and reported all downloads had finished (even though they hadn't really and i had to restart them).  Compiz was stuck far some time but after a while ran smoothly again.  Rhythmbox froze permanently.

So Ubuntu held.  Impressive!  Ubuntu is awesome!


EDIT:  Oh btw i do NOT recommend trying this on a laptop like i did because it'll get REALLY HOT!

---

### Post by CptPicard on 2008-09-04
To be honest, Ubuntu would seriously suck if that was enough to cause a **kernel panic**...

To manage a situation where a runaway process consumes all resources such as memory is really something an OS must be able to handle. The kernel out-of-memory-killer isn't anything that special :)

---

### Post by Can+~ on 2008-09-04
Interesting.. what does windows do? I imagine that windows can handle it too.

---

### Post by loganwm on 2008-09-04
If you want to get sophisticated, try to break the system :)

---

### Post by mrsteveman1 on 2008-09-04
Is there even a panic specified in the kernel code when memory completely runs out? I think it's just supposed to kill stuff, not actually call panic()

But yea, i've abused Linux quite a bit in the past and seen it come out doing just fine :D

---

### Post by slavik on 2008-09-04
I configure my system to actually fail malloc if there isn't enough memory ...

---

### Post by mrsteveman1 on 2008-09-04
> **Can+~ said:**
> Interesting.. what does windows do? I imagine that windows can handle it too.

Windows tends to send itself into a spiral swapping in and out until you hit the power button.

---

### Post by loganwm on 2008-09-04
> **mrsteveman1 said:**
> Windows tends to send itself into a spiral swapping in and out until you hit the power button.

It's a proverbial "death roll".

---

### Post by StOoZ on 2008-09-05
dude that just a typical linked list , without an ending rule for the while... I didnt check it , but does this really kills linux? :lolflag:

---

### Post by Zugzwang on 2008-09-05
> **StOoZ said:**
> dude that just a typical linked list , without an ending rule for the while... I didnt check it , but does this really kills linux? :lolflag:

No, it doesn't - this has been described by the OP.

And slavik, the problem here is that when there is no memory left, then the kernel also can't allocate more memory for its work which might be fatal for it. But it apparently can deal with the situation.

Actually, this is a very nice way to stall a multi-user machine for several minutes. ;-)

---

### Post by mujambee on 2008-09-05
> **Zugzwang said:**
> Actually, this is a very nice way to stall a multi-user machine for several minutes. ;-)

We used do that all the time at work, but the servers killed our processes when reached 4Gb or so (it's a 16Gb server). It was on Solaris.

Finally we got rid of that programmer... :(

---

### Post by Zugzwang on 2008-09-05
> **mujambee said:**
> We used do that all the time at work, but the servers killed our processes when reached 4Gb or so (it's a 16Gb server). It was on Solaris.

There's a limit that can be set for a user. It's likely that it is set to 4GB. Actually, there are applications for which 4GB is nothing. I can easily filled 128GB with a scientific computation once. ;-) And no, this was *not* a memory leak.

---

### Post by mujambee on 2008-09-05
> **Zugzwang said:**
> ;-) And no, this was *not* a memory leak.

Ours was ;)

---

### Post by Npl on 2008-09-05
So the PC Runs out of Memory, new fails and throws an exception (or returns null) and the program aborts. Wheres the big deal :confused: , it not even like Ubuntu killed the process because its stalling/sucking up all memory.

---

### Post by samjh on 2008-09-05
It's nothing special. ;)  As CptPicard said, an OS *should* be able to handle fairly simple situations like this.

---

### Post by signifer123 on 2008-09-05
It tried this too. Similar result, but mine just took alot longer to recover...
I messed up a multithreaded app once, and i felt it was interesting to see top show an app using 199% of cpu (Dual Core). I would have screen capped but it was in console.

Ran it on windows with two downloads running and two browser windows(IE), filled up RAM in about 5 seconds. (only 1.25 gig DDR). Constantly kept 4 megs free of RAM. Once RAM was filled, there was minimal lag(some mouse hops, but mostly smooth), my downloads stayed at a contant speed, and the indicator didn't have a hickup, and passed the checksum. CPU usage was at 100% while filling up RAM, but once it used the page file(500 meg to 1800 meg) it was at or below 25%(Dual Core 2.4 ghz). It took 1 minute and 44 seconds before the app was closed, with the message:
```

This application has requested the Run time to terminate it in an unusual way. Please contact the applications support team for more information.

```

Compiled via Visual Studio 2008, without precompiled header.

Of course this is on a very minimal windows xp missing nearly everything that nlite let me take out. Minus what i would use for games. So someone should try it on a regular install.

All in all windows seems to be very CPU dependant. In case you've never had a game get stuck in a loop and wait for taskmanager to load...

---

### Post by imdano on 2008-09-06
Sounds like a job for the [OOM Killer](http://linux-mm.org/OOM_Killer).

---

### Post by Reiger on 2008-09-06
> **signifer123 said:**
> All in all windows seems to be very CPU dependant. In case you've never had a game get stuck in a loop and wait for taskmanager to load...

Very true. You can load it with a lot of RAM consuming apps and still start up another hog; but beware if you touch it's precious CPU time. It'll sulk and refuse to respond to even the most, ehrm, compelling arguments until you cut off the power it depends on even more... <_<

Yet. I've had Linux go crazy (regularly) over running just *one* app which wouldn't even have been noticed in Windows. Can be a faulty piece of code in the app, of course; can also be the habit of Linux to idle to some sort of trance in which it does *not use the CPU at all* and persist in refusing to be desturbed...

---

