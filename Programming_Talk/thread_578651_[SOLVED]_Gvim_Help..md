---
title: "[SOLVED] Gvim Help."
date: 2007-10-17
forum: Programming Talk
---

### Post by Neej Suab on 2007-10-17
I am new to programming and linux. I use vim in a class and really liked gvim. So i started programming in it. I would like tha make function to work so i don't have to exit and compile using gcc from the terminal. I have followed a few links and things to solve my problem but nothing has come of it. When i press the make button, or type the make command in Gvim i get this message.

:!make a.out  2>&1| tee /tmp/v652231/15
make: Nothing to be done for `a.out'.
(1 of 1): make: Nothing to be done for `a.out'.

Please help me.

---

### Post by Modred on 2007-10-17
Generally, typing make will look for a Makefile that defines targets for compilation.  Note that you never *have* to leave Vim to type something from a terminal.  Just prepend your command with a !.

For example, press : to go into command mode and do this:

!gcc -o output %

% will be expanded to the current filename, so this is all you need if your program is only one file.  If it's multiple files, you can specify them here just like on the command line.

Anyway, do a little research on basic makefile syntax and you can then integrate that into your projects with very little effort (using the make command, of course).

---

### Post by dwhitney67 on 2007-10-18
Or consider opening a separate terminal where you can perform the Make, the gcc, or whatever.

A simple Makefile would look like this:

```
CXXFLAGS = -O2
#CXXFLAGS += -g

SRC = mySrcFile.cpp
OBJ = $(SRC:.cpp=.o)

myExe: $(OBJ)
        $(CXX) $(OBJ) -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $< -o $@
```

---

### Post by stylishpants on 2007-10-18
Once you have a working makefile, you can then use vim's built-in make command.

Instead of typing :!make, type :make.  This will compile the program, and bring your buffer to the first error if compilation fails.  You can then use :cn to move to the next error in the list.


Also, instead of exiting vim every time you want to do a console command on the command line, consider suspending vim and the resuming it when you're done.  From within vim, type ctrl-z to suspend.  When you're done on the console, use the 'fg' or '%' command to resume your vim session.  This has the advantage that you don't lose your undo history, your buffers, or your place in the file.  This is not specific to vim, it works with other commands too.

---

### Post by ScriptDevil on 2007-10-18
If you are hard-core VIM, keep using it. It has its merits
1) speed
2) syntax highlighting


But.. if you wanna make it perform tasks like compiling and other stuff, without the *:! command* syntax,  i would suggest you try emacs.

It allows you to open multiple buffers, you can write your program in one, compile in another, and for the more geeky, you can browse the web and chat on irc on emacs through the various modes.

I use both. When i need to check the source or look in for some ideas in some one else's code, vim, especially gvim is good... but for editing, it is emacs all the way. if only emacs was extensible in ruby. i suck at lisp!
:oops:

---

### Post by Neej Suab on 2007-10-18
Thanks for the Responses, I tried the command modred gave me from inside Gvim. I got a long list of errors saying that almost everything had an udefined referance to std:: something. I have compiled this program already using the g++ command i learned in my class. It worked fine runs and i receieved a good grade for the project. I'm sorry, i am enough of a newb to not know exactly what a makefile is. I get the idea from what you guys told me, but where is it? is it something i must make myself and put it somewhere? I'm going to post this and do a bit more snooping. And stylishpants, what you said is what i am looking for. I have been running to terminals for a while but i was just looking for something i could write my code in then press the button to make it happen. I will try the emacs, but i would mostly like to get Gvim working because i like it. 
Thanks for the Help. Sorry i'm so noobish. but we all have to learn somewhere.

---

### Post by dwhitney67 on 2007-10-18
Yes, the Makefile is something that you must write (edit) yourself.  Generally it sits at the same level as the source code, but it doesn't necessarily have too.

Since you are doing simple C++ development, I would suggest you create a Makefile similar to what I posted earlier.  If you have any environment variables or special needs that need to be referenced within your projects, let me know so that I can help you.

Back to the Makefile, you should list your source (.cpp) file(s) in the appropriate section as I showed in the example.  If you have more than one source file, then something like this is appropriate:

```
SRCS = myFile1.cpp myFile2.cpp etc.cpp
```

Lastly, to run the Makefile from the command line, you type this command:

[FONT="Courier New"]$ make[/FONT]

P.S.  Note that certain lines within the Makefile must be in a particular format.  Thus when you see an entry like the following, there is a tab in column 0 before the instructions (e.g. gcc -c myFile.cpp -o myFile.o), not just white-space:

```
entryPoint: *dependencies*
<tab>*instructions*
```

---

### Post by Modred on 2007-10-19
As a note, if you try to compile C++ code with gcc, you will get a bunch of errors.  The point is you can type any command after a ! that you would type on the command line.  Just change gcc to g++.

But regardless, a simple Makefile will be easier in the long run.

---

### Post by Neej Suab on 2007-10-20
Thank you guys so much. I still haven't figured out the make file exactly but thats just going to take me some practice i am sure. I think i figured this all out. I got enough information to get what i wanted done. 
Once again thank you so much for the help. I really feel like a noob, but i have to start somewhere.

---

