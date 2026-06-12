---
title: "Playing with System Processes"
date: 2007-03-04
forum: Programming Talk
---

### Post by studiesrule on 2007-03-04
Hey.
    I wanted to know if it is possible to control and handle processes (or programs) through another program. For example, if I wanted to execute, say `ifconfig` in a program, and use that output to some end (find my ip address and print it). More importantly, is it possible to interactively handle a process? The example I can give here is gdb. I want to create a GUI for gdb (based on gtk), where I want to be able to communicate with gdb, to send it a request ("run" or "break" or  "disas main"), to take its output and function on it (print all the registers or print the output of "disas main"). 

   I am aware of DBus that does a lot of this, but is there another way? Namely for things like gdb or gcc which does not have DBus integrated in it (or does it? I'm not sure). Also any pointer on usage of DBus would be welcome.

Thanks a lot for the help.

---

### Post by lnostdal on 2007-03-04
```
man 2 pipe
``` ..contains an example that illustrates this

Using Common Lisp (SBCL) `sb-ext:run-program' has an easy and comfortable API to this stuff. I've used it to interact with GNU Go (an implementation of the game [Go]("http://en.wikipedia.org/wiki/Go_%28board_game%29")) here: [http://nostdal.org/~lars/programming/lisp/swgo/gnugo.lisp](http://nostdal.org/~lars/programming/lisp/swgo/gnugo.lisp)

Doing something similar with ifconfig should be easy. Use [cl-ppcre]("http://weitz.de/cl-ppcre/") to help with parsing if you happen upon any complex output.

---

### Post by studiesrule on 2007-03-04
I guess that this would be applicable to C++ programs as well right?

Thanks a bunch.

---

### Post by Mr. C. on 2007-03-04
The pipe(2) call has many different bindings: C, C++, ...

Opening a pipe to communicate with an interactive program requires more than a simple pipe connection.  Start reviewing ptys.

MrC

---

### Post by studiesrule on 2007-03-05
Thanks Mr.C , the pty is more like what I wanted.

---

