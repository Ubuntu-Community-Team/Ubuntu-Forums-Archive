---
title: "[SOLVED] calling a program from within another"
date: 2008-12-20
forum: Programming Talk
---

### Post by Woody1987 on 2008-12-20
Im writing a program that at some point will have to execute another program and use its output. How do i execute a program from within another one? Oh, and im using C.

---

### Post by kjohansen on 2008-12-20
how does the other program write output?  does it write it to a file, does it put it on std out?

you are probably going to want to use fork and pipes if this is for *nix...

---

### Post by Woody1987 on 2008-12-20
im not too bothered about getting the output, just how to actually execute a program from within another.

---

### Post by Woody1987 on 2008-12-20
a bit of searching has turned up the system command, i.e. system("program B"). Ill try this.

---

### Post by Woody1987 on 2008-12-20
It worked! Solved

---

### Post by wd5gnr on 2008-12-20
If you just want to spin off a program and don't care much, system() will do it. However, you invoke another copy of the shell.

The "good" way to do it is to first use fork() to create a copy of the current running process. Then use one of the exec() functions to load a new program image into the copy. If you just use exec, you REPLACE your current program with the new one. If you just do the fork() you wind up with two copies of your program running (which can be useful, by the way).

With system, the library does the fork and exec AND executes a shell for you (which, if you need a shell anyway is no great loss). But if you just launch a shell which then launches something else, it is a waste of time (although probably harmless). 

[http://linux.die.net/man/3/execl](http://linux.die.net/man/3/execl) 
[http://linux.die.net/man/3/fork](http://linux.die.net/man/3/fork)
[http://linux.die.net/man/3/exec](http://linux.die.net/man/3/exec)
[http://linux.die.net/man/3/system](http://linux.die.net/man/3/system)

---

