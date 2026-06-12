---
title: "capturing stderr from many spawnd applicaitons"
date: 2009-10-25
forum: Programming Talk
---

### Post by RichardUK on 2009-10-25
In windows when I spawn an application, that is run it as a new process I can pass it pipes that the spawned app writes to. In my case the application is GCC.

My code creates many GCC calls and so I capture the output so I can print the errors all together and not all mixed up.

In the Linux code for the same app using system means all the output to std pipes get all mixed up. I've been reading up on Linux pipes and it seems all I can do is redirect the global std pipe for my application. That is if I run 4 instances of GCC the four threads that handle batching the output will all redirect the std output to the point where the last one to do so will get the out put of all the instances of GCC.

The best Idea I can come up with is to for each thread that handles a GCC call to have a unique file name and tag 2>gcc-errorsN.txt on the end of the system call. Not that ideal really.

Anyone have any ideas?

P.s Compiling 8 source files at once on a 4 core CPU really speeds up builds. :) Which is why I'm doing this.

---

### Post by RichardUK on 2009-10-25
Done it. :)

Don't know if there is a better way but I create a pipe in the /tmp folder. I make it unique by using the process and thread ID's.

I then open the pipe with the NONBLOCK option in the thread that calls GCC. I then call GCC with 2>/tmp/the-pipe-name.....

Works a treat, the output of the many GCC calls are now all together and not mixed up now. 

:guitar:

---

### Post by Zugzwang on 2009-10-25
@OP: First of all, the GNU make utility is already capable of doing parallel builds. Just invoke "make -j4" or "make -j8" instead of "make".

Second, sure it can be done. However, how to do it heavily depends on your programming language/environment. For example, in Java, this is relatively easy using the [Process]("http://www.j2ee.me/j2se/1.4.2/docs/api/java/lang/Process.html") class (returned from Runtime.exec(...)). In C and/or C++, this is a little bit more tricky. Probably someone knows a suitable library?

---

