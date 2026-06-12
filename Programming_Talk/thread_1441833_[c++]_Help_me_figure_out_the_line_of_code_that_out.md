---
title: "[c++] Help me figure out the line of code that outputs this"
date: 2010-03-29
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-03-29
I have a Gtkmm program and when I run it I get this gtk-warning in the terminal:

```
(test_program:2843): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtktreestore.c:765: Unable to convert from gchararray to gboolean
```

How do I "decode" the number 2843 to a particular part of the code? (my code is in multiple source files)

---

### Post by MindSz on 2010-03-29
```
"...gtktreestore.c:765: ..."
```

It looks like the error is in line 765 of the file gtkreestore.c

---

### Post by SledgeHammer_999 on 2010-03-29
No, that's just the line that emits the warning on the side of Gtk. I want to inspect my side, what is is the line in my code that makes the gtk-code emit the warning...

---

### Post by MindSz on 2010-03-29
have u tried with a debugger (such as gdb)?

---

### Post by SledgeHammer_999 on 2010-03-29
I don't know what to use one?!?!! :S

---

### Post by MadCow108 on 2010-03-29
gdb executable_compiled_with_-g
break g_log
run
backtrace

and follow that until you land in your code
you can change back into that frame with:
frame number_in_front_of_the_first_line_of_your_code_in_backtrace


depending on if you have the debugging information for gtk or not you may have to break in your own code and continue until the warning

---

### Post by SledgeHammer_999 on 2010-03-29
Wow thanks, I found the problem.

Could you explain to me what "break g_log" does?

---

### Post by MadCow108 on 2010-03-29
break sets a breakpoint at some point in your program, it can be a line in a file, a function, a signal, ... practically everything in a good debugger.
when this breakpoint is encountered the debugger halts the program and you can inspect whatever you wish and even continue line by line, instruction by instruction, change values of variables and registers etc.

break functionname  breaks in the beginning of the function
break file.c:70 would break on line 70 of file file.c

g_log is just the logging function of gtk. Anything which the framework outputs to stdout/stderr should go through there, so its a reasonable point to break in when looking for the source of that warning.

There are lots of tutorials on gdb and debuggers in general. I highly recommend reading some.
A good visual debugger (which uses gdb underneath) is ddd.

---

### Post by SledgeHammer_999 on 2010-03-29
> **MadCow108 said:**
> 
g_log is just the logging function of gtk. Anything which the framework outputs to stdout/stderr should go through there, so its a reasonable point to break in when looking for the source of that warning.

A very interesting piece of information. Thanks.

---

