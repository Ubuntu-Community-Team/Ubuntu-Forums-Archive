---
title: "programming with threads"
date: 2009-07-22
forum: Programming Talk
---

### Post by iochinome on 2009-07-22
hey guys, so i was assigned to do a project and i have determined that, since it requires two concurrent processes, i should use threads. i found some pretty good, detailed tutorials (if anyone knows any more, though, please share!) but i was told that you had to pay for the API in many cases. what api should i be using? this is not a ridiculously high demand program, but i would like to avoid shelling out cash for software, esp. since this is ubuntu! 
(i am running 9.10, btw.)
thanks everyone! much appreciated-

---

### Post by t4thfavor on 2009-07-22
What language are you using? 

Threads in .Net are a helluva lot different than threads in C++.

But no, for a simple application, no pay API will be nessecary in either case.

---

### Post by Rocket2DMn on 2009-07-22
Moved to Programming Talk.  Please be aware that we don't do homework help, but we can answer higher level questions, like how to get started, how to compile, etc...

---

### Post by t4thfavor on 2009-07-22
Thats precisely the reason I didn't go posting code snippets. I will (usually) just lead the horse to water in this case.

---

### Post by iochinome on 2009-07-22
dont worry, rocket2dmn, this is not homework- its summer. 'assigned' = group of associates thought i should take care of this aspect of the project. i am using c++ to do this project. it seems like pthreads is the most discussed. how do i get a copy of their api?

thanks!

---

### Post by Rocket2DMn on 2009-07-22
No problem guys, I wasn't implying that anybody here had done anything wrong, I was just giving you a heads up.

I think the POSIX threads library is standard in C++, the API should be available all over the web.  Sorry I don't have a link handy, it's been awhile since I wrote anything in C++.  I'll let the PT gurus help you out.

Cheers.

---

### Post by dwhitney67 on 2009-07-22
pthreads are available with the GNU C Library, and they are free.

If you are working with C++, you could also consider using Boost's thread API.  It too is free.

---

### Post by t4thfavor on 2009-07-22
I second the "Boost api" as anyone who has worked with posix threads knows that its alot of work. Any work you can save by using it will be a very nice addition to the end of the project when hunting bugs.

Make sure that it will not interfere with your intended license scheme, if its open source, you may not want to include it, just in case you ever want to sell your app.

---

### Post by kjohansen on 2009-07-22
openmp is also very easy to work with...

---

### Post by soltanis on 2009-07-23
OpenMP is the way to go if you are actually trying to use two (or more) processors at the same time. pthreads are a pain in the ***, otherwise use the Boost threads API because it makes everything easier.

---

### Post by slavik on 2009-07-23
openmp depends on compiler support and uses pthreads anyway.

pthreads are easy if you are careful about using them.

---

### Post by Sockerdrickan on 2009-07-23
Use C++0x std::thread

---

