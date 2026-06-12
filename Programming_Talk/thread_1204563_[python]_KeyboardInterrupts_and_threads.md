---
title: "[python] KeyboardInterrupts and threads"
date: 2009-07-04
forum: Programming Talk
---

### Post by durand on 2009-07-04
Hi,

I'm trying to write a fairly simple python script where I need to run command in the background and then run a set of commands. I have so far managed this with the use of threads. My problem now is that I need to catch KeyboardInterrupts and close the program nicely by running a few other commands first.

I tried adding an except KeyboardInterrupt across the whole script however this seems to be completely ignored. Is there an easier way to do this?

The basic outline is this:

1) Background a task
2) Run a command
3) Wait for a keyboard interrupt or system exit
4) Run a set of commands to quit the program nicely

I'm not even sure if I should use threading here. The command is actually popen and for some reason, using a & doesn't background the task so I was forced to use threads.

Does anyone have any ideas of what I should do, either using threads or not?

Thanks!

---

