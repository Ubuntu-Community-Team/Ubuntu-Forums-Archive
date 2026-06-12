---
title: "Interactive Programs"
date: 2007-09-01
forum: Programming Talk
---

### Post by DBQ on 2007-09-01
Hey Guys,

I am was writing a shell.  How do you handle programs that require input/output assuming we want to be able to pause them, background them etc.

---

### Post by jpkotta on 2007-09-01
stdin, stdout, stderr for I/O.  You get this for free with any program.  

Signals to pause, restart, and terminate.  I believe you also get these for free (i.e. the default signal handlers do what they should).  Just send the proper signals from the shell.

---

### Post by DBQ on 2007-09-01
It is not as simple as that for the applications such as pico and vi.  You need to worry about the terminal state I think.  Also when trying to run top on ubuntu I get a message similar to unable to open ttyd file descriptor.

---

### Post by DBQ on 2007-09-01
Perhaps you need to link up the stdin and stdout of the interactive program with to the stdin and stdout of my shell -- but the problem is, the shell runs in the background during that time.

---

### Post by CptPicard on 2007-09-01
If I were you, I'd dig into the source of some existing shells and investigate how they work. If I were writing my own, I would probably just fork the one with the cleanest source and adapt it to my needs. :)

---

### Post by jpkotta on 2007-09-01
Picard has the best advice.  That's the (or rather, a) point of Free Software, right?  

If I were doing this, the first scheme I would use is a fork and exec to start a new process.  It seems like file descriptors are preserved across both fork and exec, so long as a certain flag is not set (FD_CLOEXEC).  Thus they are probably still associated with the same tty?  You probably know more about this than I do.

---

