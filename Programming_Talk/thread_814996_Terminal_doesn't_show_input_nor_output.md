---
title: "Terminal doesn't show input nor output"
date: 2008-06-01
forum: Programming Talk
---

### Post by Nullius on 2008-06-01
Hi there !

I've created a program written in C++. It has about six classes that I wrote myself. The program is about 4200 lines long and main.cpp contains more than 1500 lines itself.
I don't know if the number of lines is important here, but you never know.

Now, the program itself works fine. It has to be started with some arguments (./program -t 1 -e 1 ...). If one of many arguments isn't defined, it returns an error message and quits:
```

cout << "Error" << endl;
return 1;

```
This handling is being done by the main function.

The program terminates and I get my standard linux terminal back.
But now the problem occures: the terminal doesn't respond to any key I press. If I press up, the previous command doesn't show up.
If I press another button, it doesn't get printed.
And the weirdness isn't over yet. When I (blindly because none of the characters get printed) type 'exit', the terminal closes so it does the things I ask it to do, but nothing gets shown.

Does anyone has an idea what this could be ?
Even if I put a simple cout << "Hello" << endl; and return 1; at the beginning of the main function, it produces the same problem.

I'm out of options here and I've searched for hours to find the problem. I couldn't find anything on Google either. I've tried 'terminal no output', 'terminal hangs', 'terminal does not respons', ...

Since this program is my master thesis, it would be nice it gets solves ;)

Thanks in advance !
Greets

*edit*: another weird thing is that when my program shuts down without an error but a lot of other couts, it doesn't have this problem.

---

### Post by geirha on 2008-06-01
Are you using any libraries like ncurses? It generally turns off echoing and the likes, and if you don't clean up before exiting, you will get such a result.

Typing "reset" blindly should reset the terminal to normal.

---

### Post by stroyan on 2008-06-01
If you are using curses you could use the atexit function to arrange to
have the curses "reset_shell_mode" function called when your program exits.
```

#include <stdlib.h>
...
atexit(reset_shell_mode());

```

---

### Post by Nullius on 2008-06-01
No, but I am using the MySQL++ library.
Maybe it uses ncurses .. I'll check that out ;)

Thanks for any responses so far ... I'll report back here :)

---

### Post by Nullius on 2008-06-01
Nope, doesn't seem to be the MySQL++ library.
I'm using the BeID library, maybe that's the problem.

I'll report back again ;)

---

### Post by Nullius on 2008-06-01
Doesn't seem to be the BeID library neither.
I've commented all the variables of the BeID and the header file out and I get the same problem.

Isn't there a way to make sure that the echoing is back on ?

---

### Post by geirha on 2008-06-01
You could link with ncurses and run echo() or reset_shell_mode() as stroyan suggested, but it would be much better to figure out what part turns off echoing, and how to reverse it without involving another library. 

```
ldd executable
``` should return the libraries your executable is linked against. Do you see any curses there?

Since the error happens during argument parsing, it should be fairly early in the program. Perhaps you can make a smaller program with the same symptoms and possibly debug it with gdb and/or pasting it here?

---

### Post by Nullius on 2008-06-02
> **geirha said:**
> 
```
ldd executable
``` should return the libraries your executable is linked against. Do you see any curses there?

Since the error happens during argument parsing, it should be fairly early in the program. Perhaps you can make a smaller program with the same symptoms and possibly debug it with gdb and/or pasting it here?

No sign of ncurses. (used 'ldd executable | grep curses' ... with 'executable' replaced with the right name ofcourse ;))
I've created another project this week which was almost an exact copy of the original code (sort of a light version).
Only one library was removed (the BeID one), so I'll check that one out.

@geirha: Even when I put cout << "Hello" << endl; and return 1; at the very beginning of the main function, it gives me the same problem. That was something very strange to me. Now I know some library can be the cause of this problem, I'll keep searching :)

Thanks for all the help though !
I'll report back if I find the cause (and I don't forget to report it here :D)
Maybe it could help someone else in the future .. you never know :)

Greets !

---

