---
title: "gdb doubt"
date: 2008-08-13
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-08-13
How do i execute the running of the program in steps. When enter the command step in gdb it gives me the error that i have to run the program first.

Does this mean that step can be initialized only after a breakpoint.
Someone please help.

---

### Post by sdennie on 2008-08-13
Moved to Programming Talk as more people may be able to give you advice.

---

### Post by NathanB on 2008-08-14
Yes.  Do something like:
```

break _main
run

```

...to begin stepping from the start of your program.

Nathan.

---

### Post by nvteighen on 2008-08-14
Usually, I call gdb this way:
```

gdb filename

```

If you started using "gdb", without specifying a file in the arguments, then use the "file" command to load the executable into the debugger.


A bit off-topic:
I set break points using line numbers, usually, using:
```

(gdb) break myfile.c:12

```

But you can use a function name or possibly a variable name (I never tried that) ... whatever it's included in the symbols table should work. Whatever is more comfortable to you.

---

### Post by nvteighen on 2008-08-14
Forget my last post; I misunderstood OP's question.

---

### Post by dwhitney67 on 2008-08-14
I would recommend that you use/install 'ddd'.  It is the GUI front-end to 'gdb'; it provides a palette of control buttons that allow you to execute 'run', 'step', 'next', 'cont', etc.

---

### Post by 7raTEYdCql on 2008-08-14
This is how i use gdb.

Now suppose i set a break point at the start of for loop. Then when i continue the execution of the program, it returns to the loop. Now suppose if i want to come out to the loop and want gdb to go to the next breakpoint which is somewhere in the program, how is it done???

---

### Post by dwhitney67 on 2008-08-14
If you are no longer interested in stopping at the entry point of the for-loop, then 'clear' the breakpoint; then continue so that the next breakpoint is hit.

For instance:
```
break 50
break 75
...
clear 50
cont
```
This is sooo much easier to accomplish if you use 'ddd'.

---

### Post by Cygnus on 2008-08-14
> **i.mehrzad said:**
> This is how i use gdb.

Now suppose i set a break point at the start of for loop. Then when i continue the execution of the program, it returns to the loop. Now suppose if i want to come out to the loop and want gdb to go to the next breakpoint which is somewhere in the program, how is it done???

Just set a breakpoint after the loop and use continue. I use the gdb mode inside emacs. You can also set conditional breakpoints that break when the loop has run a certain number of times, might be handy when you know the error occurs after for example 6000 iterations, you don't want to manually step your way there :)

---

