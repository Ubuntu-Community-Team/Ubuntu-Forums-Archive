---
title: "Need help from an experienced C programmer."
date: 2014-07-25
forum: Programming Talk
---

### Post by Ghostmn on 2014-07-25
Hello, 

I have been writing a physics simulator, which I have put up on github [here]("https://github.com/GhostMD/Physics"), and I am experiencing a runtime issue under certain circumstances.

The steps to reproduce the problem are as such.


[LIST=1]
[*]Initiate particle simulator 
[*]Exit particle simulator by pressing q or closing the window using the menu icon 
[*]Repeat steps 1 and 2 until the program freezes. 
[/LIST]

I'm noticing that during initialization of the program, it's memory usage is around 324 KB, and after setting up the particle simulator it goes up to 6MB.
Upon quiting that particular simulation, the program will accumulate memory if the simulator is executed again. This leads me to believe that there is a memory leak issue happening.

So I began working with GDB and valgrind.

With GDB, I found that after the second or third trial (varies) of the simulation, only two of the # threads were exiting properly. The threads that exited properly were the SDL2 event thread,
and I believe the systemtime thread if I'm not mistaken. Sometimes a third thread will exit correctly, which will be a particle thread.

Using valgrind, I found that there were 127315 issues, with the majority of them being associated with libGL and i915 driver.
There was 96 bytes that were definitely lost, which is no where near 6MB that I was seeing with htop. So with that information, I decided to add a debug option to the renderer at runtime.
This does not make any difference as far as I can tell. The program will freeze after initiating the particle simulator several times.

I would appreciate any help whatsoever that can help me rectify this issue.

Thank you for your time.

---

### Post by dwhitney67 on 2014-07-26
Do you ever de-allocate the 'hydrogen' structures that are allocated?
```

void initialize_elements(int element, int num) {

	int x;
	switch ( element ) {

		case HYDROGEN: **hydrogen = ( struct attributes *)malloc( num * sizeof( struct attributes ) )**; break;
...

```

---

### Post by Ghostmn on 2014-07-26
That's a good catch. I haven't had the time to implement elements yet, so I haven't called that function.

However I did extern and free it. I'll push the change in a bit.


I'm also going to be writing comments. A lot of the recent changes made the previous ones obsolete and therefore I just completely removed most of them.

---

### Post by tgalati4 on 2014-07-26
Run *iostat* while your instances are running.  We need more information to troubleshoot.  It seems like you are running out of resources, but what?  I have found when you hit 4000 processes in a standard linux install, bad things happen.  Of course it depends on what you are doing, but there are some limits in the default kernel.

---

### Post by Ghostmn on 2014-07-26
Right now at most I'm using 7 threads. I discovered that it might be a GL problem that I'm experiencing.

I implemented the use of glTranslatef and the sdl event thread to handle where gl was drawing the particles. The code works, when the simulation isn't frozen, but stops working after running the simulation multiple times. As I mentioned previously the sdl event thread will exit correctly given the proper conditions, which tells me that it's running correctly. This leads me to believe that because it's not shifting the objects while the program is apparently frozen, that GL might be the issue?

I attached some iostat data. If there is something specific you wanted, then please tell me. I never used iostat previously. 

Regarding the data itself, the first two sets in the attached text file were taken while the program was functioning correctly. The third set, the program was running incorrectly. From what I can tell, there doesn't seem to be a significant difference between the first two sets and the last set.

---

### Post by Ghostmn on 2014-07-28
I made a lot of various changes over the past few days, but the issue hasn't been resolved.

I used clang to compile with AddressSanitizer, and it actually received some output but I'm not entirely sure how to read it.

---

### Post by ofnuts on 2014-07-28
[http://en.wikipedia.org/wiki/AddressSanitizer](http://en.wikipedia.org/wiki/AddressSanitizer)

---

### Post by Ghostmn on 2014-07-29
Thank you everyone who made an attempt to help me.

I ended up solving my issue by using clang thread sanitizer. Apparently my program was suffering a large amount of data race conditions, which I ended up solving by using pthread_mutex's.

---

