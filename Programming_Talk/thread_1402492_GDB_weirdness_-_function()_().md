---
title: "GDB weirdness - function() ()"
date: 2010-02-09
forum: Programming Talk
---

### Post by night_fox on 2010-02-09
GDB is being weird. My main() calls a funtion which appears in GDB in the backtrace as "function () ()" with two pairs of brackets. The function is in a separate file to main.

I stop execution during a sleep statement to try and determine what is going on (i cant be bothered to find out how to set breakpoints). None of the data local to function is visible ("No symbol bla in current context") except something called buffer which i declared to be char*, and GDB tells me its struct utmp*. However the stuff i declared at the top of the file is visible.

Has anyone had this before and what does it mean?

---

### Post by MadCow108 on 2010-02-09
thats normal display in gdb when you have no debugging information or the function takes no argument
compile with -g to get some more info in those empty brackets

also compile without optimizations, as that often destroys your debugging possibilities (by reordering and elimination of code)

---

### Post by night_fox on 2010-02-09
Ahh thankyou, i'd been compiling it with -pg which isnt like -g and -p

---

### Post by dwhitney67 on 2010-02-09
@ the OP

You can set a breakpoint using the keyword 'break', or its shorthand notation of 'b', followed by the function name, or (I believe) the module name and line number.

For example:
```

(gdb) b function

```

For newbies, or for that matter advanced programmers, 'ddd' is a nice GUI front-end for interfacing with GDB.  You should consider installing/using it:
```

sudo apt-get install ddd

```
With ddd, you launch the debugger in a similar fashion as if you were using GDB.
```

ddd myapp &

```

---

### Post by night_fox on 2010-02-09
Thats really cool! I dont like the interface though, its not gnome-like and compiz treats each menu as a window and does some slow effects.

Thankyou

---

### Post by MadCow108 on 2010-02-09
> **night_fox said:**
> Ahh thankyou, i'd been compiling it with -pg which isnt like -g and -p

yes pg is a different flag which adds profile information for gprof (only p is for prof)
gcc does not support adding various characters to one option. They all need their own minus

the ddd interface takes getting used to, but it offers many really cool features for data display (hence its name data display debugger)

---

### Post by pbrane on 2010-02-09
If you want a GUI debugger try Nemiver. It's a GNOME app, and it's in the repos. Also I believe that if you type *break* at the gdb command prompt it will set a break at *main()*. Then you can step through the code from there.

---

