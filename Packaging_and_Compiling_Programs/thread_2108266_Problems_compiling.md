---
title: "Problems compiling"
date: 2013-01-24
forum: Packaging and Compiling Programs
---

### Post by cinus80 on 2013-01-24
Dear All,
I am trying to compile a research program to do protest event analysis, but when I run 'make' i obtain an extremely long list of errors, which finishes in this way
```

modify.cp:(.text+0x12bd): undefined reference to `waddnstr'
modify.cp:(.te:(t+0x12c2): undefined reference to `stdscr'
modify.cp:(.text+0x12d2): undefined reference to `waddch'
modify.cp:(.text+0x140b): undefined reference to `stdscr'
modify.cp:(.text+0x141b): undefined reference to `waddch'
modify.o: In function `ModifyClass::setupChange()':
modify.cp:(.text+0x14fc): undefined reference to `stdscr'
modify.cp:(.text+0x1514): undefined reference to `whline'
modify.cp:(.text+0x153b): undefined reference to `move'
collect2: ld returned 1 exit status
```

I have seen in other threads that these messages are usually connected with ncurses, and I tried to follow the suggestions in those threads. But I have seen that libncurses5-dev is already installed (I re-installed it, too), I checked and reinstalled build essentials, I ran 'sudo apt-get update', too. Still the same messages, and when I enter in the directory of the program I see that make worked in part (part of the .o files are there)

Do you have some suggestions? If my gergon sounds strange, I apologize: English is only a second language for me, and this is the first time I use Ubuntu --> consider this last thing in your suggestions!

---

### Post by Impavidus on 2013-01-24
I am curious why only part of the .o files are there and yet the linker runs. Whenever one of the source files doesn't compile the compiler should give an error to make, causing make to abort.

It seems that the linker is unable to find all libraries you use. Open your makefile and check that all (non-default) libraries are included on the command line (-lsome_library). But it may be wise to start fixing the errors at the first error generated.

---

### Post by cinus80 on 2013-01-24
In fact the first time I launched 'make', the procedure was slower (it was actually compiling), than it interrupted. If you want I can attach the entire flow of messages that i receive from 'make' when I try to compile for the first time, but I don't know how to print it on a file (it is too long to copy paste from the terminal)

---

### Post by audiomick on 2013-01-24
Hallo.
A tip that has no direct relation to your problem (which I regrettably can't help you with).

When you post output like that, you should use the "code tags" button to put code tags around your output. That is the # button at the top of the post box. It generates tags like this [noparse] ```
and the output goes here
``` [/noparse]

That means that the output doesn't look like this anymore

> **cinus80 said:**
> 
modify.cp: (.text+0x12bd): undefined reference to `waddnstr'
modify.cp:(.text+0x12c2): undefined reference to `stdscr'
modify.cp:(.text+0x12d2): undefined reference to `waddch'
modify.cp:(.text+0x140b): undefined reference to `stdscr'
modify.cp:(.text+0x141b): undefined reference to `waddch'
modify.o: In function `ModifyClass::setupChange()':
modify.cp:(.text+0x14fc): undefined reference to `stdscr'
modify.cp:(.text+0x1514): undefined reference to `whline'
modify.cp:(.text+0x153b): undefined reference to `move'
collect2: ld returned 1 exit status

but rather like this
```
modify.cp: (.text+0x12bd): undefined reference to `waddnstr'
modify.cp:(.text+0x12c2): undefined reference to `stdscr'
modify.cp:(.text+0x12d2): undefined reference to `waddch'
modify.cp:(.text+0x140b): undefined reference to `stdscr'
modify.cp:(.text+0x141b): undefined reference to `waddch'
modify.o: In function `ModifyClass::setupChange()':
modify.cp:(.text+0x14fc): undefined reference to `stdscr'
modify.cp:(.text+0x1514): undefined reference to `whline'
modify.cp:(.text+0x153b): undefined reference to `move'
collect2: ld returned 1 exit status
```

and the box will have a scroll bar if the output is really long.

---

### Post by cinus80 on 2013-01-24
Thank you, I edited the post following your suggestions

---

### Post by oldos2er on 2013-01-24
Moved to Packaging and Compiling Programs.

---

### Post by cinus80 on 2013-01-25
Thank you Ann,
I posted this thread on a generic place for newbies just because I am a total newbie..

---

### Post by cinus80 on 2013-01-25
> **Impavidus said:**
> I am curious why only part of the .o files are there and yet the linker runs. Whenever one of the source files doesn't compile the compiler should give an error to make, causing make to abort.

It seems that the linker is unable to find all libraries you use. Open your makefile and check that all (non-default) libraries are included on the command line (-lsome_library). But it may be wise to start fixing the errors at the first error generated.

Impavidus, I am doing what you suggested, with some external help. I want to fix the errors from the first error generated, but the problem is that I don't know how to see this first error: it's a very silly problem of scrolling the page in the terminal. the number of errors is so long, that when they finish I cannot scroll up enough to see the first messages. Can you help me with that, for instance suggesting me a way to print the terminal messages on a file?
Thanks

---

