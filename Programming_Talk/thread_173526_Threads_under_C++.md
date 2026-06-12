---
title: "Threads under C++"
date: 2006-05-10
forum: Programming Talk
---

### Post by Zdravko on 2006-05-10
Hi,
I am a C++ programmer, and I have to build a rich set of libraries with various types of functions - math calculations, I/O, graphical visualization etc. I will need a basic threading library for several parts. What threading system for C++ can you recommend me (it should be also compatible with other platforms)?

---

### Post by RavenOfOdin on 2006-05-10
Threading has been discussed various times on here already. ;)

FWIW I would keep multithreading out of C/C++ applications, but hey, that's just me. As the old saying goes "your mileage may vary."

---

### Post by kBanshee on 2006-05-10
I'm using boost threading for a program that should run on Mac, Windows and Linux. So far it's been working great!

---

### Post by pharcyde on 2006-05-10
The Boost thread library will be useful if you are doing threading in C++.  Check it out at [http://www.boost.org/doc/html/threads.html](http://www.boost.org/doc/html/threads.html).  Hopefully this will be sufficient for your needs.

You can also get some info on POSIX threads here -> [http://www.llnl.gov/computing/tutorials/pthreads/](http://www.llnl.gov/computing/tutorials/pthreads/)

---

### Post by thumper on 2006-05-11
[QUOTE=RavenOfOdin]FWIW I would keep multithreading out of C/C++ applications, but hey, that's just me. As the old saying goes "your mileage may vary."[/QUOTE]
FWIW I'd keep multithreading out of any program if it can be avoided.  It often adds extra complexity without adding a huge amount.

That said, there are situations where multithreading is necessary.  Threading in C++ is platform dependant as LordHunter317 mentioned (in another thread), but the boost threading library makes some attempt to have a simple cross platform implementation.  If all you are doing is using threads and mutexes the boost::threads should be sufficient.  If you are wanting to use events and semaphores as well, you may need to wrap those yourself.

There is no fundamental problem with having multithreaded apps in C++, and there are many successful ones out there.

---

### Post by RavenOfOdin on 2006-05-11
[QUOTE=thumper]FWIW I'd keep multithreading out of any program if it can be avoided.  It often adds extra complexity without adding a huge amount.

That said, there are situations where multithreading is necessary.  Threading in C++ is platform dependant as LordHunter317 mentioned (in another thread), but the boost threading library makes some attempt to have a simple cross platform implementation.  If all you are doing is using threads and mutexes the boost::threads should be sufficient.  If you are wanting to use events and semaphores as well, you may need to wrap those yourself.

There is no fundamental problem with having multithreaded apps in C++, and there are many successful ones out there.[/QUOTE]

Have you tried wxWidgets?

I hear its both cross platform and multithreaded.

---

### Post by nihilocrat on 2006-05-11
Multithreading naysayers should look at the newest processors coming out. Taking advantage of multi-core processors will (as far as my understanding goes) require multithreaded apps. I'm getting this crazy idea from these sources: ([shorter](http://gamearchitect.net/Articles/ManagingConcurrency1.html) [longer](http://www.gotw.ca/publications/concurrency-ddj.htm)) Hopefully the development community will make tools to make this easier, or perhaps someone will make a parallel-aware high-level programming language within the next few years.

---

### Post by LordHunter317 on 2006-05-11
[QUOTE=nihilocrat]Taking advantage of multi-core processors will (as far as my understanding goes) require multithreaded apps.[/quote]Nope.  It just requires running multiple processes at once.

You do run multiple applications, right?

However, being a multithreaded naysayer is silly because nearly all applications these days are mulithreaded at some level, save for basic console applications (e.g., filetools, shelltools, basic texttools).  UNIX is the rare exception where this isn't the case.   On Windows and OS X it's universally true that everything you run has multiple threads.  Java GUI applications are written that way is well.  I have one Windows app running that isn't multithreaded right now.  It's the Putty systray agent.

It isn't done for performance, but for resposiveness.  Windows and Java (dunno about OS X) require all GUI events and responses to occur on one thread.  That means that the message 'Paint your Window' is always sent to the same thread, and the painting must occur on that thread.  Now imagine my application talks to a database and the database times out.  It may hang for several seconds waiting on the timeout.  If I'm blocked waiting on the DB in that thread, I cannot respond to the 'Paint your Window' event and you get the dreaded 'grey window of death'.  But if I do the DB work on another thread, I can still respond to those events in the interim while I wait on the timeout.  So the app appears to be responsive to the user.

And the big major apps on Linux, like Firefox, gaim, oo.org, etc. are all threaded in some manner. They may use threads, they may use processes, but they do it for the reason I stated above.

---

