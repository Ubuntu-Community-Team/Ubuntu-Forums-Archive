---
title: "is localtime_r really thread safe and do I need to delete the tm*?"
date: 2009-01-11
forum: Programming Talk
---

### Post by jmartrican on 2009-01-11
I was using boost::date_time to get timestamps but in my tests C's gettimeofday() followed with localtime is faster.  I have a bunch of threads that will be calling gettimeofday and localtime quite often.

So here are my questions.

1)  From reading [Open Group's documentation on locatime]("http://www.opengroup.org/onlinepubs/007908799/xsh/localtime.html"), I deduce that localtime is not reentrant because it seems like localtime is using some shared memory space for storing a copy of an object called 'tm'.  Is it shared across a thread or across you program?  Is it allocated some where in the time.h code?  This might be a stupid question but I just want to be sure of why it is not reentrant.

2)  The Open Group mentions that there is localtime_r which is suppose to be reentrant.  So my question is how is it made reentrant and do we need to delete the tm* that is passed to it?  Has anyone used it before (or know how it works) and can speak for its reentrant properties?

thanks!

---

### Post by clustermonkey on 2009-01-31
localtime uses an area for the tsm struct that is global
to the program.  The area is used for each localtime call.
It is NOT threadsafe since the global area is not mutexed
and thread 2 could overwrite thread 1s value before it was
used.

localtime_r uses the local struct supplied in the function
for the tsm data.  This allows each thread to keep its own
copy of the time,  You may or may not have to delete the 
tsm depending on how you defined and allocated space for
the struct in your code.

Good luck...

---

