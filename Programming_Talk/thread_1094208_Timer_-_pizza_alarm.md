---
title: "Timer - pizza alarm"
date: 2009-03-12
forum: Programming Talk
---

### Post by WitchCraft on 2009-03-12
Hi, question:

I want to write a little program that rings an alarm (wav/ogg file) at a time specified.

For example:
It's now 19:00 o'clock. I'm moving a pizza into the oven. It will be baked at 19:10, and at 19:20 it will be charred.

So I want to write a little program that plays an alarm at 19:10.

Now, I know how to output wav/ogg, but I have a problem with executing this at a specified time.
How do i do that?
Is there anything like a kernel callback that I can use, or do I have to use cron (would prefer not to)?

---

### Post by squaregoldfish on 2009-03-12
You can use the at command for this.

At the command prompt, type:

```
at <time>
```

You will then be given a sub-prompt, where you can enter all the commands that you wish to have executed at that time. Press CRTL-D when you've entered your commands.

As always, the man page will give you more details.

Of course, you could probably find a nice little application/widget to do this as well...

Steve.

---

### Post by WitchCraft on 2009-03-12
> **squaregoldfish said:**
> You can use the at command for this.

At the command prompt, type:

```
at <time>
```You will then be given a sub-prompt, where you can enter all the commands that you wish to have executed at that time. Press CRTL-D when you've entered your commands.

As always, the man page will give you more details.

Of course, you could probably find a nice little application/widget to do this as well...

Steve.

mh, that doesn't work on Unix systems.

I think I'll launch a function as thread, infinite loop a sleep(MAX_INTEGER) in sub main, and make the thread sleep until either it is time, or in an interval, shortening the interval time if it comes close to the specified time, and call an alarm function in main, then terminate the process.

Anybody has a better idea?

---

### Post by squaregoldfish on 2009-03-12
You've confused me there. In what way doesn't it work? I use it all the time.

Steve.

---

### Post by WitchCraft on 2009-03-12
> **squaregoldfish said:**
> You've confused me there. In what way doesn't it work? I use it all the time.

Steve.

it requires at to be installed. 
If at isn't installed by default, it will fail.
Also, at is/was a linux program. It's not certain it is available everywhere.

---

### Post by nvteighen on 2009-03-12
> **WitchCraft said:**
> 
For example:
It's now 17:00 o'clock. I'm moving a pizza into the oven. It will be baked at 19:10, and at 19:20 it will be charred.


What kind of pizza needs 2:10 to be baked??? A handmade fresh pizza is ready in 20 minutes.

Ok, but I can't make **at** work either...

---

### Post by squaregoldfish on 2009-03-12
Ah, I hadn't twigged that you were looking for a non-Linux solution. What with this being a Linux forum and all.... ;)

I think a better architecture to your program would be:

1. Keep a store of all alarm events somewhere.
2. Have your main thread spend most of its time sleeping, and wake up every minute to check the time against the list of alarms.
3. If an alarm is due, kick off a separate thread to run whatever command you need.
4. Go back to step 2.

This will prevent you from having to create a dormant thread up front, and potentially losing it in the future. Instead, you create threads as they're needed and let them do their thing - you can forget about them then.

Steve.

---

### Post by jimi_hendrix on 2009-03-12
> **WitchCraft said:**
> it requires at to be installed. 
If at isn't installed by default, it will fail.
Also, at is/was a linux program. It's not certain it is available everywhere.
uhh at is installed by default on my system
> **nvteighen said:**
> What kind of pizza needs 2:10 to be baked??? A handmade fresh pizza is ready in 20 minutes.

well, if the dough is made ya...but it takes a day to make the dough
> 
Ok, but I can't make **at** work either...

me neither?

its installed but it didnt print hi at 14:30 EST like i asked

its also installed by default on BSD systems

---

### Post by squaregoldfish on 2009-03-12
at jobs, like cron jobs, will be run within their own shell environment, so you won't see anything in the shell you used to set up the at job. If you try:

```
echo "Hello" > /tmp/hi.txt
```

you should see it work.

Steve.

---

### Post by nvteighen on 2009-03-12
> **jimi_hendrix said:**
> 
well, if the dough is made ya...but it takes a day to make the dough


No. It doesn't take a day! The dough is made in two hours or such... depends on what recipe you use and how much you want it to grow.

---

### Post by stevescripts on 2009-03-12
WitchCraft - why not just script a little desktop countdown timer app?

Easy enough in the language/GUI toolkit of your choice...

Adding support for playing a wav/ogg file takes a bit more effort than using the system bell, but certainly doable.

Just curious...

Steve

---

### Post by johnl on 2009-03-12
If you are actually looking to write a program to do this, take a look at the alarm() function and the SIGALRM signal.

```

man 3 alarm

```

or if you need more precision:

```

man 3 ualarm

```

---

### Post by WitchCraft on 2009-03-12
> **squaregoldfish said:**
> Ah, I hadn't twigged that you were looking for a non-Linux solution. What with this being a Linux forum and all.... ;)

As I use (Debian) Linux, I'm not looking for a non-linux solution, but I want any solution to work on any platform/distribution. Speaking of Linux, that requires either kernel calls, glibc functions, or statically linked libraries, because everything else might not work. And the use of cron/at is not possible, because it would require any user on windoze to install some special programs.


> **nvteighen said:**
> What kind of pizza needs 2:10 to be baked??? A handmade fresh pizza is ready in 20 minutes.
 
 Ok, but I can't make **at** work either...
 Then, use cron :evil:
Yea, 2 hours is a bit long. Moreover, I shouldn't mistype numbers  ](*,)
 

> **johnl said:**
> If you are actually looking to write a program to do this, take a look at the alarm() function and the SIGALRM signal.


I've already found that when I look at the implementation of sleep in the glibc sources *(sysdeps/posix/sleep.c).*
But maybe i should look at the at/cron sources.

> **stevescripts said:**
> 
WitchCraft - why not just script a little desktop countdown timer app?
 
 Easy enough in the lan guage/GUI toolkit of your choice...
 
I'm basically doing that. 
It's just that I'm testing the wxWidgets wxTaskBar class, implementing it as a shared library as reusable component later on for possible use in more complex (cross-platform) applications.

> **stevescripts said:**
> 
 Adding support for playing a wav/ogg file takes a bit more effort than using the system bell, but certainly doable.

 No, it isn't. You simply have to download a lib, install OpenAL, and then call a beep equivalent with some more parameters, e.g. filename. 




> **squaregoldfish said:**
> 
I think a better architecture to your program would be:

1. Keep a store of all alarm events somewhere.
2. Have your main thread spend most of its time sleeping, and wake up every minute to check the time against the list of alarms.
3. If an alarm is due, kick off a separate thread to run whatever command you need.
4. Go back to step 2.

This will prevent you from having to create a dormant thread up front, and potentially losing it in the future. Instead, you create threads as they're needed and let them do their thing - you can forget about them then.

Steve.

I agree on 1, which is a truism if you have more than one alarm pending. I was thinking of just one for the start.

I disagree on two, it shouldn't do that, that requires too much processing time, and it's unreliable because if you have an alarm scheduled at 19:20, and if the last time it checks is 19:19:59, then it will next check at 19:20:59, which is about one minute off schedule...
Also, if the next alarm is due in 9 hours, it will check for alarms 9 * 60 =  540 times... 
So the check interval needs to be adjusted, depening on the next scheduled alarm.
Also, sleep is in seconds (milliseconds on windows), I need to take care of integer overflows if i wait for very long, so I must use a bigint library for arithmetic, and break up intervals that are too big.

3. I agree on 3, since i shouldn't open a thread for each alarm that shall be issued... i realize it was stupid to just think of one alarm for the start.


4. I figured that i need not an infinite loop (=while(true)), but a while(bool) loop, so I can exit the alarm program by setting bool to false once there are no more alarms to issue 


Implementing BigInt class now \\:D/

---

### Post by WitchCraft on 2009-03-12
> **nvteighen said:**
> No. It doesn't take a day! The dough is made in two hours or such... depends on what recipe you use and how much you want it to grow.

The dough is made in 5 to 10 minutes, but it takes at least 3 hours until the yeast has grown sufficiently.
It's however better to wait at least half a day after making the dough.
Then, bakeing the pizza takes 30 to 45 minutes.
Altogether, it takes about 8 hours to get a good pizza.
And it's a shame it carbonizes when ubuntuforums takes too much of my attention... Need to implement pizza alarm! It also has to work when I'm forced to work under windoze & maccrap ! ! !


Adding chees to the edge.
Yum, yum.

---

### Post by squaregoldfish on 2009-03-12
> I disagree on two, it shouldn't do that, that requires too much processing time, and it's unreliable because if you have an alarm scheduled at 19:20, and if the last time it checks is 19:19:59, then it will next check at 19:20:59, which is about one minute off schedule...
Also, if the next alarm is due in 9 hours, it will check for alarms 9 * 60 = 540 times...
So the check interval needs to be adjusted, depening on the next scheduled alarm.
Also, sleep is in seconds (milliseconds on windows), I need to take care of integer overflows if i wait for very long, so I must use a bigint library for arithmetic, and break up intervals that are too big.


I take the point on the specific timing of your checks - I suppose that depends on how accurate you want your timer, and for short cooking jobs a minute might give you less than perfection.

However, the idea of checking an in-memory list of alarms once per minute taking up too much processing power isn't really going to be a problem. 

Think about a system monitor like conky - I have it checking over a dozen different items, and it does this, along with updating the display, every second. From a system responsiveness viewpoint, I can't tell it's running, and I defy anyone to be able to notice the effect of a quick check like the one you need every minute. I agree that one should keep extraneous processing to a minimum, but there comes a point where it's not worth worrying about.

Steve.

---

### Post by jimi_hendrix on 2009-03-12
> **nvteighen said:**
> No. It doesn't take a day! The dough is made in two hours or such... depends on what recipe you use and how much you want it to grow.

if its good it takes a day...it has to sit over night

---

### Post by WitchCraft on 2009-03-12
> **squaregoldfish said:**
> 
However, the idea of checking an in-memory list of alarms once per minute taking up too much processing power isn't really going to be a problem. 

Think about a system monitor like conky - I have it checking over a dozen different items, and it does this, along with updating the display, every second. From a system responsiveness viewpoint, I can't tell it's running, and I defy anyone to be able to notice the effect of a quick check like the one you need every minute. I agree that one should keep extraneous processing to a minimum, but there comes a point where it's not worth worrying about.

Steve.

That depends on the circumstances. If you have a fast 4 GHz Dual/OctoCore CPU with 4 gigs of RAM, that's certainly true, if you have a 16 MHz 386 SX with 16 MB RAM, that's certainly different.
Also it depends on what else you run.
Certainly no problem if you only run a program with marginal processor use, like a wordprocessor/spreadsheet, but different if you run a program that uses the processor to full capacity, like compiling the kernel or performing textsearch indexing in the background.

---

### Post by dwhitney67 on 2009-03-12
> **WitchCraft said:**
> Hi, question:

I want to write a little program that rings an alarm (wav/ogg file) at a time specified.
...

If you can figure out how to play the wav/ogg file, then really all you need is to set up an alarm (or timer) to expire after a certain interval has passed.

I've attached a timer class object (written in C++) in which I have never found a practical purpose to use.  Nevertheless, I wrote it in my spare time and was happy with the result.  It allows one to kick off as many timers as they wish, and to configure these timers to be one-shot, repeating up to N-times, or continuous (i.e. repeating, but run indefinitely).  You can also set the timer to block the application or not; the choice is yours.

If you are familiar with C++, all you need to do is define a functor object that defines your callback routine; this routine can be used to play your audio file.  For example:
```

#include "Timer.hpp"
#include <string>
#include <iostream>

class PlayAudio
{
  public:
    PlayAudio() {}

    void operator()(void* arg)
    {
      const char* wavFile = reinterpret_cast<const char*>(arg);

      // open wav File and play back audio
      std::cout << "opening wav file '" << wavFile << "'" << std::endl;
    }
};

int main()
{
  typedef Timer<PlayAudio>  PizzaTimer;

  // set up timer for 2 hours, to be non-repeating, and to not block.
  PizzaTimer timer(7200, PizzaTimer::ONE_SHOT);   // 7200 = 2 hours * 60 minutes * 60 seconds

  // start the timer (duh)
  const char* wavFile = "myWavFile";
  timer.start((void*)wavFile);
}

```

Hopefully the code will find a new home!

------------------------

EDIT:  Sorry for the updates; it has been awhile since I used the timer, and only now did I discover some of it's limitations (i.e. inability to pass args to the callback routine).  That's been corrected (at least I hope so).

---

### Post by squaregoldfish on 2009-03-13
> **WitchCraft said:**
> That depends on the circumstances. If you have a fast 4 GHz Dual/OctoCore CPU with 4 gigs of RAM, that's certainly true, if you have a 16 MHz 386 SX with 16 MB RAM, that's certainly different.
Also it depends on what else you run.
Certainly no problem if you only run a program with marginal processor use, like a wordprocessor/spreadsheet, but different if you run a program that uses the processor to full capacity, like compiling the kernel or performing textsearch indexing in the background.

Also a fair point. However, I think you just might be in danger of taking a pizza timer a little too seriously. If you want a timer that's reliable to that extent, just go to a shop and buy a kitchen timer. This has the added bonus that they're either battery powered or mechanical, and hence immune to a system crash on your computer.

---

### Post by nvteighen on 2009-03-13
> **WitchCraft said:**
> The dough is made in 5 to 10 minutes, but it takes at least 3 hours until the yeast has grown sufficiently.
It's however better to wait at least half a day after making the dough.
Then, bakeing the pizza takes 30 to 45 minutes.
Altogether, it takes about 8 hours to get a good pizza.


Oh, you're a gourmet... Of course, waiting half a day makes the pizza impressive, but you generally don't have that time to do it. My trick is to heat the kitchen (using the oven... it has to be preheated anyway) and it makes the dough grow faster... of course, you lose quality (lossy compression pizza codecs? :p) but not too much.

> **jimi_hendrix said:**
> if its good it takes a day...it has to sit over night

That remembers me to a humorous situation at home. My mom was baking a pizza and told my little brother the pizza "had to sit over" (in Spanish we say it the same way). My brother looked at her confused and asked "And where's the chair?". :)

---

### Post by WitchCraft on 2009-03-15
> **squaregoldfish said:**
> Also a fair point. However, I think you just might be in danger of taking a pizza timer a little too seriously. If you want a timer that's reliable to that extent, just go to a shop and buy a kitchen timer. This has the added bonus that they're either battery powered or mechanical, and hence immune to a system crash on your computer.

Yea, but those timers can't play an mp3/ogg, and they aren't for free (while writing a pizza-alarm program is free & fun).
 :lolflag:

Besides, I use Debian Squeeze, so my system is so damn stable that it only crashes when I have a sigsegv in my Quake3/OpenArena/UrbanTerror aimbot source (SDL 3D app.) - and even then it's only the X-window system that crashes (seldomly, and most times I expected it...). 

However, I can make the timer & alarm run as daemon and have a client that runs on x-window. That way, you enter the data in the client, and even though the client crashes on X-Window crash, the alarm daemon doesn't. If the daemon crashes, it will be restarted, and the alarms will be reloaded from a .txt file.

Nice, ey ?
Just need to figure out how to make a daemon.

> **nvteighen said:**
> 
Oh, you're a gourmet... Of course, waiting half a day makes the pizza impressive, but you generally don't have that time to do it. My trick is to heat the kitchen (using the oven... it has to be preheated anyway) and it makes the dough grow faster... of course, you lose quality (lossy compression pizza codecs? :p) but not too much.


LoL, a singual value decomposition pizza codec.
Doesn't heating a room with a pizza oven use a bit too much electricity?

---

### Post by nvteighen on 2009-03-15
> **WitchCraft said:**
> 
LoL, a singual value decomposition pizza codec.
Doesn't heating a room with a pizza oven use a bit too much electricity?

You use the same amount of electricity: you have to preheat the oven anyway before baking. Of course, you have to close doors and windows... :p

---

### Post by WitchCraft on 2009-03-16
> **nvteighen said:**
> 
You use the same amount of electricity


That's an interesting theory you have there.
But I doubt its correctness.

---

### Post by Habbit on 2009-03-16
Indeed, keeping the oven on for the same amount of time will most likely use the same amount of electricity (not taking into account that most ovens automatically switch off when they reach the desired temperature), but you won't preheat the _whole room_, which is way bigger than the oven and is also not insulated, to the same temperature that the closed oven would reach. You don't need to be studying rocket science (like yours truly) to know a bit of thermodynamics.

---

### Post by nvteighen on 2009-03-16
> **Habbit said:**
> Indeed, keeping the oven on for the same amount of time will most likely use the same amount of electricity (not taking into account that most ovens automatically switch off when they reach the desired temperature), but you won't preheat the _whole room_, which is way bigger than the oven and is also not insulated, to the same temperature that the closed oven would reach. You don't need to be studying rocket science (like yours truly) to know a bit of thermodynamics.
When I meant to "preheat the room" I just wanted to mean that you can take advantage of the preheating oven to rise the temperature in the room (and specially near the oven) in order to speed the dough's growth a bit up...

Of course, this is a method you should use if you can't wait 12 hours (for any reason... either because you have no time or because you are really hungry).

---

### Post by s.fox on 2009-03-17
Isn't this thread getting a little of topic? :D

@ Original Poster:  Where you able to sort out the alarm?

---

### Post by WitchCraft on 2009-03-19
> **Ash R said:**
> Isn't this thread getting a little of topic? :D

@ Original Poster:  Where you able to sort out the alarm?

Yea, it's getting a bit off-topic, but that does no harm.
I've not yet had enough time to do it (probably i was talking/writing too much last weekend) but I'll keep you informed of any progress  ;-)))  .

---

### Post by s.fox on 2009-03-19
> **WitchCraft said:**
> Yea, it's getting a bit off-topic, but that does no harm.
I've not yet had enough time to do it (probably i was talking/writing too much last weekend) but I'll keep you informed of any progress  ;-)))  .

Okay.  Thanks.  It has triggered my interest :D

---

