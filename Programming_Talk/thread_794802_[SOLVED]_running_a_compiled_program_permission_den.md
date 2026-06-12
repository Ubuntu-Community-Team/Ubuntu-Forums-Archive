---
title: "[SOLVED] running a compiled program: permission denied?? (error 126)"
date: 2008-05-15
forum: Programming Talk
---

### Post by mooglinux on 2008-05-15
I have put together my first c++ program and after some confusion with the iostream (at first i thought it was isostream...that worked great lol) now everythign compiles great (using geany but compiling from terminal does the same thing) but when i try to run the program, with either ./gameover or executing it with geany, i get error 126, and it tells me that permission is denied. but if i try sudo ./gameover then it tells me "command not found"

here is my program:
```

// Game Over
// My first C++ Program
#include <iostream>
int main()
{
	std::cout << "Game Over!" << std::endl;
	return 0;
}

```

---

### Post by agim on 2008-05-15
Ok, first of all, there is no reason to use sudo. I would suggest finding a guide highlighting when to use sudo. Using it incorrectly is the easiest way to make your machine no more safe than even Windows.

Okay, now that that is out of the way.

Here is how you use g++

g++ <source-file> -o <executable>

then run the executable by running

./<executable>

---

### Post by mooglinux on 2008-05-15
Yea i know i shouldnt have to use sudo. i figured it might fix the problem if its a permissions thing. so running g++ with just the -o works. so why is geany running the command with -Wall as well? and where would i change that?

---

### Post by dwhitney67 on 2008-05-15
The -Wall is merely for the compilation stage that g++ uses.  It has no bearing on the linking stage that makes the executable you are trying to run.

I do not use geany... whatever that is... so therefore I cannot comment on that.  Do you have any experience using the gnome-terminal?  If so, find out what permission are assigned to your executable.  Use a command such as:
```
$ ls -l myExe
```
and report back.

P.S. -Wall is used to report _all_ warnings that may be generated during compilation of your code.

---

### Post by mooglinux on 2008-05-15
Found it. I went to Build > Set includes and arguments and there is the option to edit the command it runs to compile it. just took out -Wall so it reads g++ -c "%f" ("%f" is replaced by the current filename when it runs) and now my program runs just dandy!

would be curious to know what the -c -o and -Wall options do tho

---

### Post by agim on 2008-05-15
When compiling from the command line, -o specifies what you are going to call the output file. Otherwise the default is a.out.

---

### Post by dwhitney67 on 2008-05-15
Ok...

the -c indicates to generate an object file (a .o file) AND not attempt to link to form an executable file.

the -Wall indicates to generate "errors" on all warnings... this will prevent an object file from being generated (I need to verify this!!!)

the -o is used to indicate where to place the results of a compiled program (i.e. where to place the object file), or in the case of linking, where to place the executable file.

P.S.  Removing the -Wall should not have prevented you from running the executable unless...

1)  The executable was not generated because of one or more "warnings" during compilation

2)  Because 'geany' is a POS.

---

### Post by gabopk on 2011-04-06
I have a similar proble, but when i open the gdb, set the break point and when i type run i get:


Starting program: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2 
/bin/bash: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: Permission denied
/bin/bash: línea 0: exec: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: can't execute: Permission denied
During startup program exited with code 126.

Same thing when i try to run it. And i get it with every program i compile.. Any help?

---

### Post by dwhitney67 on 2011-04-06
> **gabopk said:**
> I have a similar proble, but when i open the gdb, set the break point and when i type run i get:


Starting program: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2 
/bin/bash: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: Permission denied
/bin/bash: línea 0: exec: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: can't execute: Permission denied
During startup program exited with code 126.

Same thing when i try to run it. And i get it with every program i compile.. Any help?

Welcome to Ubuntu Forums!

Now, will you please open a new thread rather than piggy-back on this thread which is nearly 3 years old.

---

### Post by gabber777 on 2012-03-05
> **gabopk said:**
> I have a similar proble, but when i open the gdb, set the break point and when i type run i get:


Starting program: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2 
/bin/bash: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: Permission denied
/bin/bash: línea 0: exec: /media/gaBo/U/IE-1503/Tareas/Tarea 2/A75967tarea2: can't execute: Permission denied
During startup program exited with code 126.

Same thing when i try to run it. And i get it with every program i compile.. Any help?


You must compile the program from the directory /home....etc, but not from /media

---

