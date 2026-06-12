---
title: "Terrible noob question about including"
date: 2008-04-27
forum: Programming Talk
---

### Post by tomgoos on 2008-04-27
Forgive me for asking this terrible noob question but I can't find a good recourse on the web. Here's the thing. I installed gcc and netbeans with the c/c++ package. Now I got this piece of code that I want to run but the comiling already goes wrong with the first #include statement.

When I compile something with
```
#include <stdio.h>
#include <stdlib.h>
```
The inclusion goes perfect, no problems. However, this other code has:
```

#include "ALLOC.H"
#include "DOS.H"
#include "CONIO.H"
#include "STDIO.H"

```
in the preamble. This goes wrong (newmain.c:14:19: error: alloc.h: No such file or directory). Now I remember that there is a difference between the <> and the "" symbols. So I tried both, and also both in  upper and lowercase. Nothing worked. What should I do to get it compiled? 

Cheers,
Tom

---

### Post by LaRoza on 2008-04-27
> **tomgoos said:**
> 
```

#include "ALLOC.H"
#include "DOS.H"
#include "CONIO.H"
#include "STDIO.H"

```

Well, they should be lowercase to begin with.

DOS.H should be a dead give away. You are not using DOS ;)

alloc.h, dos.h, and conio.h are not standard. They are Windows (DOS) specific.

---

### Post by tseliot on 2008-04-27
> **tomgoos said:**
> Now I remember that there is a difference between the <> and the "" symbols.
Have a look at this page:
[http://www.thinkage.ca/english/gcos/expl/c/incl/expl.html](http://www.thinkage.ca/english/gcos/expl/c/incl/expl.html)

---

### Post by samjh on 2008-04-27
> **tomgoos said:**
> ```

#include "ALLOC.H"
#include "DOS.H"
#include "CONIO.H"
#include "STDIO.H"

```
in the preamble. This goes wrong (newmain.c:14:19: error: alloc.h: No such file or directory). Now I remember that there is a difference between the <> and the "" symbols. So I tried both, and also both in  upper and lowercase. Nothing worked. What should I do to get it compiled? 

Cheers,
Tom

First of all, you need to find out where those files are.  Secondly, you will need to set one of the project options in Netbeans to point to those files so that the compiler can find them (I don't know how to do this on Netbeans, so consult its documentation).

However, as LaRoza had pointed out, those header files are for MS DOS, so your code almost certainly will not compile if you're running Linux.

---

### Post by JupiterV2 on 2008-04-27
> Now I remember that there is a difference between the <> and the "" symbols.

Quotations ("") are used for "local", project dependent, headers. Basically, headers that you, or the project maintainer, have created for inclusion into the project but have no use outside of it. The angle brackets (<>) are used for headers located in /usr/include/... or directories specified with the -I compiler flag. These headers are usually standard C/C++ or external libraries (GTK+, Boost, etc).

Whether you are using "" or <> when including files, they are case-sensitive, so "DOS.H", "dos.h" and "DoS.h" are all different.

---

### Post by WitchCraft on 2008-04-27
As others said, this looks like you want to compile a Windows program on Linux.

#include "ALLOC.H"
#include "DOS.H"
#include "CONIO.H"
#include "STDIO.H"

you can try to replace the include files with the linux equivalents:
"ALLOC.H" --> #include <cstring>
"DOS.H"   --> #include <unistd.h>
"CONIO.H" --> #include <termios.h> or  <linux/input.h>
"STDIO.H" --> #include <iostream>

and then google the functions to adjust them

or you can google for DOS.H CONIO.H STDIO.H etc. and look whether you find them, usually you find something useful at koders.com

---

### Post by Compyx on 2008-04-27
> **WitchCraft said:**
> As others said, this looks like you want to compile a Windows program on Linux.

#include "ALLOC.H"
#include "DOS.H"
#include "CONIO.H"
#include "STDIO.H"

you can try to replace the include files with the linux equivalents:
"ALLOC.H" --> #include <cstring>
"DOS.H"   --> #include <unistd.h>
"CONIO.H" --> #include <termios.h> or  <linux/input.h>
"STDIO.H" --> #include <iostream>

and then google the functions to adjust them

or you can google for DOS.H CONIO.H STDIO.H etc. and look whether you find them, usually you find something useful at koders.com

Sorry, but that's just bad advice. First off the #include's of <stdio.h> and <stdlib.h> and probably all others ending in ".h" lead me to believe this is C code we're talking about, not C++.

Secondly, you can download non-portable headers like "dos.h" and "conio.h" but this won't help at all because these libraries just do not exist on Linux system (or anything non-MS). Using these header files will give you prototypes for the functions used in the code but you cannot compile/link the code.


To the OP: check the code to see if these libraries are really needed, usually in small example programs you'll only find calls to clrscr() and getch() or something similar and can normally just be omitted. But from the looks of actually #include'ing alloc.h this is either very old code or just written by a bad programmer.

---

### Post by tomgoos on 2008-04-27
Thanks for all these replies guys. It's been years since I've last programmed in C(++), it's coming back now :-k . I also thought it was strange that these were all in uppercase (which was why I tried them lowercase as well). I was trying to use this code because I could import .wav files with it. The DOS.H include should have rang some bells that this was not meant for linux systems. The first one (alloc.h) looked standard enough though and this one also didn't work so I thought I might be doing something even more stupid. I'll just toss this piece of code. Any hints for im/exporting and playing/recording audio are greatly appreciated! 

Thanks all!
Tom

---

### Post by tomgoos on 2008-04-28
Pages I should have found before posting this question:
[Troubleshooting common C and C++ compilation errors]("http://ubuntuforums.org/showthread.php?t=691451")
[Compiling your first C or C++ programs]("http://ubuntuforums.org/showthread.php?t=689635")
Both from this forums faq:
[programmers talk faq]("http://ubuntuforums.org/showthread.php?t=606009)

---

