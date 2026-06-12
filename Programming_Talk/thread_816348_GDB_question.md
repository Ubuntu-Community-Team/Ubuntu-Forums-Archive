---
title: "GDB question"
date: 2008-06-02
forum: Programming Talk
---

### Post by thefestival on 2008-06-02
I've been tooling around with the gnome debugger and so far it seems great but I can't seem to set a breakpoint.  (yes I did compile with -g)

When I run the program: 
gdb programname
break 20 ( breakpoint on line 20 )

I get this: No line 20 in file "init.c"

I don't know what this means or what init.c is.  And there is definitely a line 20 in my program.

Thanks.

---

### Post by sq377 on 2008-06-02
try this
gdb ./programname
break sourcefile.c:20

That way it should know exactly where to go.  Maybe it's something you linked to that has an init.c.

---

### Post by thefestival on 2008-06-02
I tried your suggestion but it's telling me no such thing as sourcefile.c

It can't be this hard to set a breakpoint can it?

---

### Post by Can+~ on 2008-06-02
compile with the -ggdb flag instead of -g

Not sure if this is the reason, could you post your C file so I can try it?

---

### Post by stroyan on 2008-06-03
> **thefestival said:**
> I tried your suggestion but it's telling me no such thing as sourcefile.c

It can't be this hard to set a breakpoint can it?

When sq377 said "sourcefile.c" he meant the source file that you
are trying to set the breakpoint in.  It sounds like you used a literal
"sourcefile.c" instead of your own file name.

Perhaps you should start with setting a breakpoint at a function.
"break main"

---

