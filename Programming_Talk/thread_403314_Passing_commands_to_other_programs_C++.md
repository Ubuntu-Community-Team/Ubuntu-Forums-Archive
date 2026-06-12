---
title: "Passing commands to other programs: C++"
date: 2007-04-06
forum: Programming Talk
---

### Post by qpwoeiruty on 2007-04-06
How would I go about passing commands from one program to another?

I'd like to be able to start a program and be able to pass commands to it, by typing it into my program, having it execute in the terminal, and having output passed back to me.

Example: I type: "locate gnome" and the output of that command goes into a string back in my program.

---

### Post by duff on 2007-04-07
The **popen** function would be the easiest way.

---

### Post by qpwoeiruty on 2007-04-09
Thanks! Is there a way to continue entering commands into the pipe or is there a more powerful way to do this? I need the output to not go to the screen at all but to a string or something so that I can parse it eventually.

```

pid_t pid;
switch(pid = fork()) {
case 0:
	pclose(popen("totem file","w"));
              //need to write more to console (like totem --pause, etc)
	break;
default:
	//rest of program
}
```

---

### Post by j_g on 2007-04-09
There are a few ways of passing data between programs (ie, processes).

The fastest way is to put that data in shared memory (which each process can access). Use shmget() to allocate some shared memory (and also to get access to it within each process). Use shmat() to map the memory into each process. This is similiar to Windows APIs CreateFileMapping and MapViewOfFile, respectively. You may also need to use some signals to synchronize access to the shared memory, if both processes access it simultaneously, or to alert another process that you want it to read the data that you just wrote into the shared memory.

Another way is with message queues. Not as fast as the above, but it does relieve you of dealing with synchronization. One caveat: Each message can transfer no more than 4,056 bytes of data.

Another way is with pipes. This is slower than shared memory, and often involves busy-wait polling if you want the process to be abortable.

If the processes are running on different machines then you may have to resort to something like the sockets library, Corba (ack), or Bonomo.

Go to google and type in "linux interprocess communication" to read numerous articles on the above.

---

### Post by slavik on 2007-04-09
global variables and mutex (between threads)
shared memmory and semaphores (between processes)
pipes (between processes)
sockets (between processes, possibly over network)

---

### Post by qpwoeiruty on 2007-04-09
Wow. TYVM, both of you! I couldn't figure out what to search for. Now I've got some reading to do :)

As it looks so far, difficulty wise, message queues seem the easiest to start with (if I can figure out how to make it do what I want that is ;)), although I'm not up to the section on shared memory yet.

Again, TYVM for the informative posts. I appreciate it and it really helps.

---

### Post by slavik on 2007-04-09
threads are the easiest IMO ... but if you need to call another program, it's not an answer (same with pretty much everything except pipes)

pipes is the only thing which will work universally (as long as the program you need can read from stdin and write to stdout).

another thing that I missed is 'exec'

---

