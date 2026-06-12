---
title: "Std streams"
date: 2007-09-04
forum: Programming Talk
---

### Post by DBQ on 2007-09-04
Hey Guys,

Some processes (ie more), can have a piped input, and keyboard input at the same time.  How is this possible in bash, since each process can have only one stdin stream?  I will spend some time looking at the source , but if anybody has a simple explanation it'd be cool.

---

### Post by lisati on 2007-09-04
I'm not sure what arrangements there are in BASH but some versions of the C programming language have multiple "std" i/o streams - these include "stderr".

---

### Post by DBQ on 2007-09-04
How does C do that?

---

### Post by lisati on 2007-09-04
> **DBQ said:**
> How does C do that?

I'm not sure of the exact details, I'm a bit rusty on "C". If memory serves, for console programs, most output involving the screen goes through "stdout", e.g. fprint(stdout,message) 
"stderr" is normally used for error messages, but the idea is pretty much the same e.g. fprint(stderr,message)

EDIT: p.s. "stdout" and "stderr" are often treated as "files" by C that are normally associated with the screen (terminal, console, insert word of choice)

---

### Post by Lux Perpetua on 2007-09-04
> **DBQ said:**
> Hey Guys,

Some processes (ie more), can have a piped input, and keyboard input at the same time.  How is this possible in bash, since each process can have only one stdin stream?  I will spend some time looking at the source , but if anybody has a simple explanation it'd be cool.I actually looked at the source code of the more utility some years ago when I was learning C trying to understand issues like this, just like you're trying to do. If I recall correctly, it simply opens /dev/tty for input. 

**edit**. To see /dev/tty in action, try the following in your terminal: 
```
$ echo "Here is some text" > /dev/tty
$ cat < /dev/tty > test.txt     # Then type some text and press control-D
$ cat test.txt
```

---

### Post by DBQ on 2007-09-04
what about something like ps -aux | more ?

---

### Post by Lux Perpetua on 2007-09-04
Do you know anything about files and streams? A program can have many files open at once. So a program can receive input from many different places. If its input is redirected, so stdin no longer refers to the terminal, the program can still access the terminal via special files in the dev directory.

---

