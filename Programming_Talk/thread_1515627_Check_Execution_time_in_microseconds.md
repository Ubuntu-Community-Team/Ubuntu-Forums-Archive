---
title: "Check Execution time in microseconds"
date: 2010-06-22
forum: Programming Talk
---

### Post by discover07 on 2010-06-22
Hi,
How can i get the execution time of a C program in microseconds ?

Is there any shell command to do so?

thanks

---

### Post by tbastian on 2010-06-22
you might be looking for the 'time' command?

```

time ls

```

output:

```

// contents of directory...

real	0m0.020s
user	0m0.000s
sys	0m0.012s

```

edit:
'real'  is the amount of time it actually took
'user' is... I'm not 100% sure, but you're not interested for this application
'sys' is the system time

if you notice, sys + user != real. Thats because 'ls' apparently didn't use the CPU the entire time

---

### Post by Emill on 2010-06-22
With 'time', you only get milliseconds...
It is quite hard to measure microseconds.

---

### Post by mbsullivan on 2010-06-22
See [here]("http://stackoverflow.com/questions/275004/c-timer-function-to-provide-time-in-nano-seconds/275231#275231"). gettimeofday and clock_gettime() both have high enough precision. Definitely don't trust their results to the full resolution (nanoseconds), but microseconds should be okay.

You're not saying what programming language you're using. If you're using Boost under C++, it also has a high performance timer built in.

Python has the ability to measure in the order of useconds, too... Through the standard libraries. For timing your own code, use "timeit".

Mike

---

### Post by discover07 on 2010-06-23
> **mbsullivan said:**
> See [here]("http://stackoverflow.com/questions/275004/c-timer-function-to-provide-time-in-nano-seconds/275231#275231"). gettimeofday and clock_gettime() both have high enough precision. Definitely don't trust their results to the full resolution (nanoseconds), but microseconds should be okay.

You're not saying what programming language you're using. If you're using Boost under C++, it also has a high performance timer built in.

Python has the ability to measure in the order of useconds, too... Through the standard libraries. For timing your own code, use "timeit".

Mike

thanks a lot  Mike..
gettimeofday() worked for me...:)

---

