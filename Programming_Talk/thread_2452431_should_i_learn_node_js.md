---
title: "should i learn node js"
date: 2020-10-21
forum: Programming Talk
---

### Post by tendouser on 2020-10-21
why some people advise not to you use node js for some specific tasks like calculating fibonacci serie?

---

### Post by TheFu on 2020-10-21
Because compiled C is so much faster, it isn't even funny. Almost any compiled language wold be faster.

Javascript is scripted and slow. NodeJS is great for lightly used sites, say 1-2 thousand concurrent connections.  For tens of thousands of concurrent connections, languages that scale better are available.

There are lots and lots of good reasons to use NodeJS and places where it makes really good sense.  Doing heavy math just isn't the best use for javascript.

As always, the best tool for the job should be used.

---

### Post by tendouser on 2020-10-21
is python compiled available for this matter on the server side? 

i ask because i've only seen hosting provider offering interpreted python

i've read that in some python compilations are faster than compiled c

is that true?

---

### Post by TheFu on 2020-10-22
Any language can product slow code.  If you are a bad C programmer, then you can make terrible code. The same applies to python, javascript, perl, Rexx, C#, C++, Rust, ruby, or the other 500+ other languages.

The only way to know for sure that any implementation of a program is faster or slower than any other would be to create both, using experts for each language, then use a profiler to time the runtimes.  If the program runs once a month for 2 minutes in python and the C version runs in 1 minute, how useful is that?  OTOH, if the program runs 50,000x a day, spending the time to get the C version down to :54 seconds would be very worth while. I doubt the python version could be made faster by an expert, considering that python is implemented in C.  But a crappy C programmer's code vs an expert Python programmer would likely be more on par for performance.

In short, the answer is "it depends."

---

