---
title: "C++ using Unix system calls execl() - forking problem"
date: 2013-02-20
forum: Programming Talk
---

### Post by Dirich on 2013-02-20
I wrote a program that outputs some numerical data, which I plot via gnuplot. Since sometimes there are a lot of plots to do, the program uses a fork(), so I can use execl() to run an instance of gnuplot.

I am forced to do the fork since, for what I understand, execl() will kill my current process.
I found some workaround to be sure to avoid any memory problem, since my  program does need a lot of it with certain setups, but what I would really like is for a more elegant option that doesn't need to kill my current process to call gnuplot, so that I can avoid forking.

My problem with forking is that it creates another process identical to the original one, thus if the father is using a lot of memory, so will do the son. And all that memory is a waste, even if it is released immediatly after thanks to execl() killing the process.


Any suggestion on how to proceed?

---

### Post by Tony Flury on 2013-02-20
> **Dirich said:**
> I wrote a program that outputs some numerical data, which I plot via gnuplot. Since sometimes there are a lot of plots to do, the program uses a fork(), so I can use execl() to run an instance of gnuplot.

I am forced to do the fork since, for what I understand, execl() will kill my current process.
I found some workaround to be sure to avoid any memory problem, since my  program does need a lot of it with certain setups, but what I would really like is for a more elegant option that doesn't need to kill my current process to call gnuplot, so that I can avoid forking.

My problem with forking is that it creates another process identical to the original one, thus if the father is using a lot of memory, so will do the son. And all that memory is a waste, even if it is released immediatly after thanks to execl() killing the process.


Any suggestion on how to proceed?

instead of using fork/execl - why not use a simple call to system - in this case that sounds like a better idea to me.

Doh : of course system uses fork/excl unde the hood - so that doesn't help either - sorry

---

### Post by Dirich on 2013-02-20
I checked the function system() (<cstdlib>) that was your suggestion (before you edited it).

From what I understood, it waits for the program I call through it to end, only then my original program continues its flow.
This would also be a problem since I do not need to wait for the execution of gnuplot, I just want to start it as soon as I can to make use of all the processors I have available, since my main program only uses 1. :(

Thanks for the try though.

---

### Post by steeldriver on 2013-02-20
It's a long time since I've done anything like this, but I seem to remember using named pipes (mkfifo etc.) to pipe the plot *data* to a separate plotting process (which could be gnuplot... or whatever) - buffering of the pipe effectively means that your main program can continue to run while the buffering / plotting does its own thing

I guess you could implement some kind of true socket-based IPC (number crunching client --> plot server) if you really wanted to do it 'right'

---

### Post by MadCow108 on 2013-02-20
> **Dirich said:**
> 
My problem with forking is that it creates another process identical to the original one, thus if the father is using a lot of memory, so will do the son. And all that memory is a waste, even if it is released immediatly after thanks to execl() killing the process.


the memory is not wasted, any operating system worth its bytes uses copy-on-write for forking processes.
So if the parent uses 99% of memory you can still span hundreds of children, they will use the same 99% of memory
Only when the memory is modified it new memory is allocated (on page level)

starting another program is impossible without forking (on unix/windows like systems at least).

you can use popen to start gnuplot with a stdin pipe. (popen like system uses fork under the hood)
you can then write your commands into the pipe to control gnuplot, thats usually enough for simple tasks.
Problematic is waiting for results in gnuplot used in this way, either you poll the filesystem for files it creates (via inotify for good efficiency) or you let gnuplot send a signal to the parent via !kill -USR1 pid

---

### Post by Dirich on 2013-02-20
> **MadCow108 said:**
> the memory is not wasted, any operating system worth its bytes uses copy-on-write for forking processes.
So if the parent uses 99% of memory you can still span hundreds of children, they will use the same 99% of memory
Only when the memory is modified it new memory is allocated (on page level)

starting another program is impossible without forking (on unix/windows like systems at least).

you can use popen to start gnuplot with a stdin pipe. (popen like system uses fork under the hood)
you can then write your commands into the pipe to control gnuplot, thats usually enough for simple tasks.
Problematic is waiting for results in gnuplot used in this way, either you poll the filesystem for files it creates (via inotify for good efficiency) or you let gnuplot send a signal to the parent via !kill -USR1 pid
Thanks!


For future reference for those that may read this thread for help:

Since I was using fork() explicitly, I was simply using a wait(0) on the father when I had reached the maximum amount of child I decided to allow. The first child that ends its task allows the father to go back to work.
It is not a 100% safe solution, but if the gnuplot instance lasts long enough (not too much actually), then it works perfectly well.

---

