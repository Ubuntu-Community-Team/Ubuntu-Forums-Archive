---
title: "STDIN fd0 who is closing it?"
date: 2010-06-15
forum: Programming Talk
---

### Post by Agent Smit on 2010-06-15
Greetings,

I've recently been working on a small server/daemon and have come across a strange situation where stdin/fd0 is being closed. This of course returns fd0 to the file/socket descriptor "pool" which I was not expecting.

I have checked my code and am certain I have not close fd0. So this leads me to believe that the OS is closing it for some reason.

Now, I have already search Google but am most likely not using the correct search terms as I have not been able to find anything regarding this issue.

So...

Could any of you please point me in the right direction? Why would stdin be closed by the OS?

Thanks!

---

### Post by MadCow108 on 2010-06-15
I don't think the os will close stdin.
I had a similar problem once and it did turn out is was a bug in the programs source.

strace was a great help finding the source of the close(0)

---

### Post by Agent Smit on 2010-06-15
Thanks MadCow,

I have it strace running now and will wait for the event to resurface. In the mean time would you mind, if possible to show me the command options/switches you used?

Thanks!

---

### Post by MadCow108 on 2010-06-15
I just searched for a close(0) and looked at the surrounding system calls for something I was familiar with in the code.
I was lucky that near the occurrence there was another unique system call in the same function (logging to a file) so it was very easy to find the exact location in the code.
You may not be so lucky, depending on where and how it happens.

useful switches are -f for tracing forks and child processes, -T for timing the system calls (for profiling) -ttt for timestamps, -p to attach to running process.
see manpage for further information.

I guess if you have debugging symbols for the kernel you could also use a debugger by setting a conditional breakpoint on close with fd == 0
But I never did something like that.

---

### Post by Agent Smit on 2010-06-15
Ok so I've been running this daemon all afternoon with strace. So far nothing has closed fd0.

I ran the daemon via the command line options in strace:

strace -o strace.log /home/hydra/hydra > hydra.log &

I'm going to restart the process again but this time attaching an existing process to see if that makes any difference (-p PID).

Thanks again for your input.

---

