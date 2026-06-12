---
title: "make a process run with very low priority"
date: 2012-07-24
forum: Programming Talk
---

### Post by hakermania on 2012-07-24
Hey!

Let's say I have a small system running Debian and does a task every second. This task writes to a file.

At the end of every day, I want to archive this file in tar.gz format. The archiving process is something like 'too much' for this little system and slows it down. As a result, the other process that now writes to another file (not to the one being archived) isn't as efficient as it was.

Can I give very low priority to the compression process? I mean, I don't care even if the compression take 1 hour or so (in a normal PC the conversion of such a text file should't take more than 3-4 seconds), so is this even possible?

---

### Post by Lars Noodén on 2012-07-24
> **hakermania said:**
> Can I give very low priority to the compression process? I mean, I don't care even if the compression take 1 hour or so (in a normal PC the conversion of such a text file should't take more than 3-4 seconds), so is this even possible?

Yes, you can use [nice](http://manpages.ubuntu.com/manpages/precise/en/man1/nice.1posix.html) when you launch the script or process.  The higher the number, the lower the priority.  There is also [renice](http://manpages.ubuntu.com/manpages/precise/en/man1/renice.1.html) if you change your mind after the script or process is launched.

---

### Post by m_duck on 2012-07-24
I think ***nice*** should achieve what you want. It changes the scheduling priority of a given process.

So```
nice -n# your_command
```Where ***#*** is a number between 0 and 19 (or -20 and 19 if you are root) and ***your_comman***d is, well, your command.

I think this should achieve what you want, though I've never actually tried it myself.

EDIT: Yeah, as Lars Noodén points out, a lower nice value equals higher priority.

---

### Post by Hetepeperfan on 2012-07-24
> **m_duck said:**
> I think ***nice*** should achieve what you want. It changes the scheduling priority of a given process.

So```
nice -n# your_command
```Where ***#*** is a number between 0 and 19 (or -20 and 19 if you are root) and ***your_comman***d is, well, your command.

I think this should achieve what you want, though I've never actually tried it myself.

EDIT: Yeah, as Lars Noodén points out, a lower nice value equals higher priority.

just to add: 19 is the lowest priority and -20 is the highest priority.  For priorities below 0 you need to be root (however there are exceptions possible). you can see in the system monitor the niceness of your program.

cheers

---

### Post by hakermania on 2012-07-24
Thanks for any answers so far!

So, giving the writing process a priority of -20 and the compressing process a priority of 19 (the writers of 'nice' must be Australians?) will do the trick?

---

### Post by Zugzwang on 2012-07-24
> **hakermania said:**
> Thanks for any answers so far!

So, giving the writing process a priority of -20 and the compressing process a priority of 19 (the writers of 'nice' must be Australians?) will do the trick?

You have to try it out. "nice" only affects the share of processing time that the process will get. What can happen in principle is that your problem is less processor load, but I/O load. The nice'd process will still generate a lot of I/O load, which may slow down all other processes. However, typically, a nice'd process will also be a bit nicer in terms of I/O, but by how much is something that you should try out, especially as nicing a process is certainly the most simple possible solution to your problem.

---

### Post by trent.josephsen on 2012-07-24
> **hakermania said:**
> the writers of 'nice' must be Australians?

Niceness describes how willing a process is to give up its cycles to other processes who need them. Very nice processes (with a high nice value) are generous with their cycles and will let other processes go first and wait until they're done. Very greedy processes (with a low nice value) cut in line and steal cycles away from other processes.

That's not nice.

---

### Post by Lars Noodén on 2012-07-24
> **Zugzwang said:**
> You have to try it out. "nice" only affects the share of processing time that the process will get. What can happen in principle is that your problem is less processor load, but I/O load. The nice'd process will still generate a lot of I/O load, which may slow down all other processes. However, typically, a nice'd process will also be a bit nicer in terms of I/O, but by how much is something that you should try out, especially as nicing a process is certainly the most simple possible solution to your problem.

For that, there is [ionice](http://manpages.ubuntu.com/manpages/precise/en/man1/ionice.1.html).

---

