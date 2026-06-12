---
title: "If I have an integer, how can I put it in a time_t* structure?"
date: 2009-01-02
forum: Programming Talk
---

### Post by tom66 on 2009-01-02
This part is giving problems:

```

raw_time = (time_t *)(cctvTxt.start_time + (short)(frame / cctvTxt.fps));
time_info = localtime(raw_time);
		
sprintf(time_format, "%s\n%s", cctvTxt.date_row1, cctvTxt.date_row2);
strftime(time_buffer, 80, time_format, time_info);

```

*raw_time* is a time_t value.
*time_info* is a *struct tm *time_info*
*time_format* and *time_buffer* both have 1,000 bytes allocated to them.

But, when running it, I get a segmentation fault. What have I done wrong? 

Thanks,
Tom

---

### Post by nvteighen on 2009-01-02
Why is raw_time being cast to **time_t ***? Shouldn't it be just **time_t**? Or, if raw_time is a pointer, then you should do ***raw_time = ...**.

---

### Post by tom66 on 2009-01-02
Casting to just *time_t* causes a compilation error (invalid conversion or something like that). I'll try the other method you suggested.

Thanks

---

### Post by nvteighen on 2009-01-02
> **tom66 said:**
> Casting to just *time_t* causes a compilation error (invalid conversion or something like that). I'll try the other method you suggested.

Thanks
Then raw_time is a pointer... if you want to change the contents of the address that pointer points to, you have to use the * operator. Otherwise, you'll be just changing the address the pointer points to... And who knows what the hell is there...

---

### Post by tom66 on 2009-01-02
Sorry, I forgot to mention it was. In several C++ guides I've read, I've seen that it must be a pointer for some reason. Using a normal value doesn't work. 

However, this code still throws a segmentation fault. I have narrowed it down to the topmost line, as a printf statement after there doesn't get printed. So, I'm confused.

```

*raw_time = (cctvTxt.start_time + (short)(frame / cctvTxt.fps));
time_info = localtime(raw_time);
		
sprintf(time_format, "%s\n%s", cctvTxt.date_row1, cctvTxt.date_row2);
strftime(time_buffer, 80, time_format, time_info);

```

---

### Post by nvteighen on 2009-01-02
Hmm... Compile using the -g flag and run the code using gdb.

```

gdb myprog

```

Use the "run" command at gdb to make it start... when it segfaults, it will throw the exact line where it occurred.

---

### Post by Tony Flury on 2009-01-02
in my experience - a segfault is often not caused by the line that actually fails.

It could be a memory allocation problem many lines before.

---

### Post by nvteighen on 2009-01-02
> **Tony Flury said:**
> in my experience - a segfault is often not caused by the line that actually fails.

It could be a memory allocation problem many lines before.
No and yes: the SEGFAULT hits exactly at the illegal access line. Of course, then you have to backtrack where the error comes from.

---

### Post by tom66 on 2009-01-02
My compiler line is, which includes GDB, libmath, and libgd:

```

g++ timestamp.c -g -lm -lgd

```

which isn't giving much useful information:

```

[New Thread 0xb7a538d0 (LWP 3878)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7a538d0 (LWP 3878)]
0xb7fad754 in ?? () from /lib/ld-linux.so.2

```

---

### Post by nvteighen on 2009-01-02
> **tom66 said:**
> My compiler line is, which includes GDB, libmath, and libgd:

```

g++ timestamp.c -g -lm -lgd

```

which isn't giving much useful information:

```

[New Thread 0xb7a538d0 (LWP 3878)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7a538d0 (LWP 3878)]
0xb7fad754 in ?? () from /lib/ld-linux.so.2

```

I love the ?? () warnings from gdb... :p

Do the same and then, use the "bt" command to look at the backtrace and see from where that function has been called.

---

### Post by tom66 on 2009-01-02
I ended up fixing my problem, but my going down a route I didn't want to take... it's a very esoteric route to take. 

I used PHP, wrote a small script and piped it's output into a file, then read the file, using that in my program. I expected it to be a performance hog, but it's actually OK. 

Thanks for your help.

---

### Post by dwhitney67 on 2009-01-02
> **tom66 said:**
> Sorry, I forgot to mention it was. In several C++ guides I've read, I've seen that it must be a pointer for some reason. Using a normal value doesn't work. 

However, this code still throws a segmentation fault. I have narrowed it down to the topmost line, as a printf statement after there doesn't get printed. So, I'm confused.

```

*raw_time = (cctvTxt.start_time + (short)(frame / cctvTxt.fps));
time_info = localtime(raw_time);
		
sprintf(time_format, "%s\n%s", cctvTxt.date_row1, cctvTxt.date_row2);
strftime(time_buffer, 80, time_format, time_info);

```
This problem could have been solved in a couple of minutes if you had provided more code that demonstrated how raw_time was declared and initialized.  Instead you found a questionable workaround.

time_t is nothing more than a value stored in a 4-byte space (I believe it is defined to be a 'long' integer).

Thus the proper usage would be something along the lines of:
[php]
#include <time.h>
...

time_t t = (cctvTxt.start_time + (short)(frame / cctvTxt.fps));

struct tm* tm = localtime(&t);

...
[/php]
where **struct tm** has the following definition:
[php]
           struct tm {
               int tm_sec;         /* seconds */
               int tm_min;         /* minutes */
               int tm_hour;        /* hours */
               int tm_mday;        /* day of the month */
               int tm_mon;         /* month */
               int tm_year;        /* year */
               int tm_wday;        /* day of the week */
               int tm_yday;        /* day in the year */
               int tm_isdst;       /* daylight saving time */
           };
[/php]

---

