---
title: "gdb doesnot display source code"
date: 2006-02-22
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-02-22
I compiled a c program using

```
gcc -Wall -g example.c
```

I tried to debug the program using gdb.

```
gdb -tui a.out
```

But the source code of my program is not being displayed in the window.
How can I view the source code while I debug the program?

Thanks and Regards,
Vijayanand.

---

### Post by oakz on 2006-02-22
see the LIST command

also, read "info gdb" for all of the commands available to you from the (gdb) prompt

---

### Post by jerome bettis on 2006-02-22
apt-get DDD, it's a gui frontend to gdb and a lot easier to work with.  gdb doesn't show enough info at once and is tedious to use.

---

### Post by twopoint718 on 2009-02-04
It actually does this in two ways. Here's how I usually use GDB. After I compile my program with the '-g' flag (this inserts debugging information) I run this (if my program is the default 'a.out'):

$ [COLOR="Blue"]gdb a.out[/COLOR] 

Then gdb prints a little about itself and dumps you into the command line. Here you can set a few break points, something like "b 19" for break on line 19 or "b foo" to break on function foo.

If you want to see a quick listing of the lines that are around the line you're on type:

(gdb) [COLOR="Blue"]list[/COLOR]

if you want to see a separate panel that always shows your code type:

[COLOR="Blue"]C-x C-a[/COLOR] (that is type and hold "Ctrl" while also pressing 'x', then hold "Ctrl" and press 'a'). 

This will show you a pane at the top that displays your code (GDB calls this "TUI" mode: [GDB user manual]("http://sourceware.org/gdb/current/onlinedocs/gdb_24.html#SEC253")). If you haven't already, type "run" and gdb will run your code. You'll see the top pane paused at your breakpoint (if you set one) or the last line that your program got to.

I hope this is more of what you were looking for.

---

