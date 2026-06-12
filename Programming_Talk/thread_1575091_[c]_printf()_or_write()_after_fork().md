---
title: "[c] printf() or write() after fork()?"
date: 2010-09-15
forum: Programming Talk
---

### Post by dawwin on 2010-09-15
I read somewhere, that I should use snprintf() and write() instead of printf() after fork(), if I want to print from more than one process. Is this true?

---

### Post by dwhitney67 on 2010-09-15
You do not have to worry about printing from separate processes, which is what you get when you fork(), although as a side-effect, the output from each process may be jumbled together.

When printing from a separate thread (LWP = Light-Weight Process), then it matters.  Here you have to ask yourself whether a function is thread-safe or not.  In the case of printf(), it is not (**EDIT:  dawwin has found that this statement is incorrect**).  The function snprintf(), which writes to a buffer, and write(), which writes to the specified file descriptor, are thread-safe.

Read more about thread-safeness here: [http://en.wikipedia.org/wiki/Thread_safety](http://en.wikipedia.org/wiki/Thread_safety)

P.S.  If two threads are sharing the same file pointer, and each is calling write(), then you need to protect the file-descriptor with a mutex.  It is similar if two threads are sharing the same buffer when calling snprintf().

---

### Post by Zugzwang on 2010-09-15
In addition to what dwhitney said, if your output is buffered, it might be a good idea to flush the outputs to your open files and the error and output streams in order to avoid duplicating the content of their respective buffers when the processes eventually flush their buffers. But I'm not 100% sure about whether this is really an issue.

---

### Post by dawwin on 2010-09-15
I read about it here -> [http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html](http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html)
> What is the reason of using **write** rather than **printf**? It is because **printf()** is "buffered,"  meaning **printf()** will group the output of a process together.  While buffering the output for the parent process, the child may also use **printf** to print out some information, which will also be buffered.  As a result, since the output will not be send to screen immediately, you may not get the right order of the expected result.  Worse, the output from the two processes may be mixed in strange ways.  To overcome this problem, you may consider to use the "unbuffered" **write**. Why printf() isn't thread-safe? According to linux/unix manuals it should be -> [http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html)

---

### Post by rnerwein on 2010-09-15
> **dawwin said:**
> I read somewhere, that I should use snprintf() and write() instead of printf() after fork(), if I want to print from more than one process. Is this true?

hi
my opinion is --> if you calling a fork the fs-descriptors are inherited. you will have ( i'm coming from sys V )
and it's the same in linux. 
pintf is using a buffered area ( e.g. 4096 byte ). and in the kernel you will have two "file tables". one for the
kernel direct and one ( user fs ) for the process. that means that the system will wait until the buffer is filled
up before the buffer will be flashed. but uninx/linux is a multitasking system, that means the buffer can be
filled up by different "tasks".
i prefer to use on critical situations ( no every time ) to use " fprintf(stder,".... or open a file for write with
O_SYNC ) both means no buffering.
i prefer for critical situations in C -- the wirte.
ciao

---

### Post by dwhitney67 on 2010-09-15
> **dawwin said:**
> I read about it here -> [http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html](http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html)
Why printf() isn't thread-safe? According to linux/unix manuals it should be -> [http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html)

Well, then it probably is.  That's why it is always important to read the documentation.  But who has the time.  :-)

---

### Post by dawwin on 2010-09-15
I will use write() to be sure

---

### Post by MadCow108 on 2010-09-15
all glibc io stream functions lock the stream. So what says on that page is probably outdated, you will not get interleaved output if using "atomic" outputs (e.g output is in a single f... call) .
if that is not possible use flockfile et al.:
[http://www.gnu.org/software/libc/manual/html_node/Streams-and-Threads.html#Streams-and-Threads](http://www.gnu.org/software/libc/manual/html_node/Streams-and-Threads.html#Streams-and-Threads)

if you want functions without locking use the _unlocked stream functions

write on the other hand may not be threadsafe.
I recall some discussion about making it so, but (at least at the time) it was considered to expensive (and I agreed with that, you can always use the threadsafe higher level interface or lock yourself).
No idea what the current situation is.

---

### Post by dawwin on 2010-09-15
So which function I should use? printf() or write()? I am talking about [COLOR=#000000]multiprocess program, not multithreading
[/COLOR]

---

### Post by MadCow108 on 2010-09-15
oh I somehow missed the main point :/
my post does not apply to forked processes.

Maybe you should state what exactly you want to do.
As fprintf internally calls write anyway and on a fork everything of the process is copied (on write) you should not get any problems assuming write is threadsafe.
So it should not matter which one you use.
For immediate display you can still use fflush

---

### Post by rnerwein on 2010-09-16
> **MadCow108 said:**
> oh I somehow missed the main point :/
my post does not apply to forked processes.

Maybe you should state what exactly you want to do.
As fprintf internally calls write anyway and on a fork everything of the process is copied (on write) you should not get any problems assuming write is threadsafe.
So it should not matter which one you use.
For immediate display you can still use fflush
hi
sorry but have a look at " man fcntl" - i'm talking about C pure - multi threading is a very difference herausforderung - fore sure.
and anybody want to program in C --> C is like a razor but without a grip
have fun
ciao

---

