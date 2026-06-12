---
title: "Weird problem with fork() and output pipes."
date: 2009-06-18
forum: Programming Talk
---

### Post by ydraliskos on 2009-06-18
This problem came up when trying to pipe the output of a small C program on a file.


C program roughly does this.

main()
-starts with args at runtime.
-printfs a line depending on how many args it received.
-runs a child function.
-ends.

Child function forks the living **** out of itself but this is of no real importance, it's just a demonstration of tree structures as processes. Forks print a bunch of stuff then die.


Ok so I run it in terminal and get the expected output. 1 informative line about how many args it received, then the fork output.

if however, I try
./a.out 2 3 5 > output.txt

the output.txt file, instead of the text i saw without pipes, will contain the informative line multiple times, intermingled with the fork outputs. I haven't really counted but I suspect it will be as many times as there are forks.

Why does this happen. At no point during their lives do the forks visit the start of main(). Why are those lines printed, and why only when piping the output?

---

### Post by fr4nko on 2009-06-18
From the info page of libc:
   > Call `_exit' to accomplish this.  The reason for using `_exit'
instead of `exit' is to avoid flushing fully buffered streams such as
`stdout'.  The buffers of these streams probably contain data that was
copied from the parent process by the `fork', data that will be output
eventually by the parent process.  Calling `exit' in the child would
output the data twice.  *Note Termination Internals::.I suppose it is clear enough, when you fork the data in the output buffer are duplicated and when you call exit in the child processes the stdout is flushed and the parent data printed. So it seems that you should use '_exit' to terminate the child.

Why the problem does not happens is not clear to me but may is related to the way the terminal get the output. Probably the '>' redirections in the shell cause a fopen call and I suppose for normal stdout a different polling methods is used, I guess asynchronous data read with signals (?).

Francesc

---

### Post by ydraliskos on 2009-06-18
> **fr4nko said:**
> From the info page of libc:
   I suppose it is clear enough, when you fork the data in the output buffer are duplicated and when you call exit in the child processes the stdout is flushed and the parent data printed. So it seems that you should use '_exit' to terminate the child.

Why the problem does not happens is not clear to me but may is related to the way the terminal get the output. Probably the '>' redirections in the shell cause a fopen call and I suppose for normal stdout a different polling methods is used, I guess asynchronous data read with signals (?).

Francesc

nice, I do use exits() in the forks, that's probably it, thanks a bunch

---

### Post by Habbit on 2009-06-18
Actually, if that's the problem, calling _exit would kill the data that you are trying to print. I think the parent should flush its stdout before forking.

---

### Post by ydraliskos on 2009-06-19
> **Habbit said:**
> Actually, if that's the problem, calling _exit would kill the data that you are trying to print. I think the parent should flush its stdout before forking.

ok yeah I tried that and it killed all of my output so you're exactly right.

How would I go about doing what you say? Keep in mind this:


A child prints an output, then passes that same output to the parent. The parent then prints its output (a modified output of the child with some extra stuff) then passes it above.




EDIT: I could always do the file writing inside the program but man I'm too lazy, and at this point this is more out of interest to know how it can be fixed

---

