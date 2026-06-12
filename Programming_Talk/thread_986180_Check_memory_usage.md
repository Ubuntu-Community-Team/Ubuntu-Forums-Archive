---
title: "Check memory usage?"
date: 2008-11-18
forum: Programming Talk
---

### Post by Sunnz on 2008-11-18
Hello I am just wondering what are the ways to check the memory usage of a program?

I have written a little daemon for my own use, and I have been watching its memory usage using `top`, as far as `top` is concerned, the memory usage have not been increasing in the last few hours when I started the daemon.

But I am wondering if `top` is good enough? Or that if you know a better tool to watch the memory usage of your program?

It is written in C by the way, I guess that's why I really want to be careful, because it is easy to create memory leak in C, and since this is a daemon to be run forever on my server, memory leak would be a huge problem.

It is a command line tool by the way, so I just SSH into the server and run top to see how it is going. It also logs messages to syslog, which I check regularly.

---

### Post by Idefix82 on 2008-11-18
The top command is pretty accurate, I think, more so than most graphical tools. If you only want to monitor one process you can use
```
top -p PID
```
replacing PID by the process ID in question. You can also replace PID by a comma separated list of several PIDs.

---

### Post by cyfur01 on 2008-11-18
> It is written in C by the way, I guess that's why I really want to be careful, because it is easy to create memory leak in C, and since this is a daemon to be run forever on my server, memory leak would be a huge problem.
You could check for leaks using [valgrind]("http://valgrind.org/"). Valgrind should do a decent job with your daemon, but will not work perfectly because you'll have to kill your daemon mid-process in order to get the leak report which is printed at the end of the program's execution (unless you have a tidy way of ending your daemon).

To use valgrind, compile with the "-g" flag, and then run:
```

valgrind --leak-check=full ./program > output.log

```
Note that **the resulting process will be named, "memcheck,"** not, "program".

This is an example program that runs into the issue daemons do:```

#include <stdlib.h>

void func(){
        // Leak memory
        int *leak = malloc(100*sizeof(int));
}

int main(){
        // Leak memory
        int *leak = malloc(100*sizeof(int));
        // Non-leaked memory
        int *good = malloc(100*sizeof(int));

        func();

        while(1){
                // Do nothing
                int i=1;
        }
        free(good);
        return 0;
}

```
When killed (via Ctrl+C, or "killall memcheck" from a different shell), the valgrind report is:```

==8986== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==8986== malloc/free: in use at exit: 1,200 bytes in 3 blocks.
==8986== malloc/free: 3 allocs, 0 frees, 1,200 bytes allocated.
==8986== For counts of detected errors, rerun with: -v
==8986== searching for pointers to 3 not-freed blocks.
==8986== checked 52,036 bytes.
==8986== 
==8986== 400 bytes in 1 blocks are definitely lost in loss record 1 of 3
==8986==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==8986==    by 0x80483D5: func (prec.c:6)
==8986==    by 0x804840E: main (prec.c:13)
==8986== 
==8986== 
==8986== 400 bytes in 1 blocks are still reachable in loss record 2 of 3
==8986==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==8986==    by 0x8048406: main (prec.c:11)
==8986== 
==8986== 
==8986== 400 bytes in 1 blocks are still reachable in loss record 3 of 3
==8986==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==8986==    by 0x80483F7: main (prec.c:10)
==8986== 
==8986== LEAK SUMMARY:
==8986==    definitely lost: 400 bytes in 1 blocks.
==8986==      possibly lost: 0 bytes in 0 blocks.
==8986==    still reachable: 800 bytes in 2 blocks.
==8986==         suppressed: 0 bytes in 0 blocks.


```
In this example, 800 bytes of memory were actually leaked, but only 400 bytes of the leaked memory was detected as definitely lost because some was still pointed to mid-process since the program get stuck in the infinite loop before freeing "good" and exiting.

One expansion to valgrind is [Omega]("http://www.brainmurders.eclipse.co.uk/omega.html") which [apparently can detect memory leaks on the fly]("http://www.nabble.com/debug-a-daemon-program-td6046154.html").

---

### Post by Cracauer on 2008-11-18
Do you want to check memory load or memory leaks?

You cannot check for memory leaks in top and the like. Because virtual memory might be overcommitted and memory leaks might not show up in physical memory.

For memory leak checking you want a malloc checker, as posted.

For memory load measuring you want the display in top(1), but you can get the same data in a more munchable form in /proc/$pid/statm .

---

### Post by Sunnz on 2008-11-21
> **Cracauer said:**
> Do you want to check memory load or memory leaks?

I guess I do want to check for memory load first.

I am a bit new to programming in C... so maybe I have misunderstood a bit... so I'll try explain what I was thinking.

I am not that much concern with how much memory my code uses overall, as long as its usage stays consistent, it is a really small program and really doesn't use all that much.

What I am concern with is, in the main loop, if it does something like:

while(1) { ptr = malloc(4); *ptr = 1; }

Even if it only takes up 4 bytes in each loop, overtime its memory usage is going to explode, as ptr is not freed properly.

While things outside of the main loop doesn't matter that much... say I do a malloc(4000) before the main loop, it will only do that once and gets freed when the program calls 'exit', right? I mean, it may be reserving memory unnecessarily, but it will not eat up more and more as I leave the process running forever, right?

Anyway the code is something like this:

```
char* ip;
unsigned int interval = 60;

while(1) {
ip = inet_ntoa(in);
sleep(interval);
}
```

Here's what I find the most confusing... what *really* happens when I call inet_ntoa?

I know that it returns a char* containing the IP address in a.b.c.d format... but how does it work as far as memory goes?

It is a pointer to the beginning of the "array", right? So, it is a pointer to some sort of a stack, isn't it?

Now, I do call inet_ntoa in the beginning of every loop. But I can't free something from the stack, so, what happens there, does it gets free at all?

From looking at top, the memory usage is not increasing in the last 2 days that my daemon is running.

---

### Post by Cracauer on 2008-11-21
inet_ntoa uses a preallocated string space that is shared by all calls to inet_ntoa. You don't manage that memory. Typically you use strdup() to get the result into your own space.

Which idiot came up with that interface, anyway?

---

### Post by Sunnz on 2008-11-21
Ahhh I see, so use strdup if I write my own function that returns a char* eh?

Thanks!!

EDIT: It looks like inet_atop is the better way to do this, I'll convert all calls to ntoa to ntop. :D

---

