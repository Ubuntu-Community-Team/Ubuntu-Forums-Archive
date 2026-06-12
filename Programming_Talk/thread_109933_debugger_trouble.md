---
title: "debugger trouble"
date: 2005-12-29
forum: Programming Talk
---

### Post by oldmanstan on 2005-12-29
I've got a small program that compiles just fine with g++ but when run hits a range check error (the program has no built-in error handling since it's mainly something i'm doing to learn c++). Quite a while back I used to write programs in VB then later in Delphi and when you would run your program from the IDE and it ran into an error it would give you a line number that was causing the error. So the question is how do I get that with c++/Anjuta or KDevelop or even the command line debugger (I have gdb installed)?

Any help would be awesome!

---

### Post by darth_vector on 2005-12-29
to start the debugger type:

$ gdb progname

and you will get a dgb prompt. here you can set the arguments for the program to be run, set breakpoints, etc (type help at the gdb prompt for a quick rundown). when you are ready to run your program type:

(gdb) start

and when the program dies type

(gdb) bt

to backtrace the problem.

---

### Post by dave84 on 2005-12-30
hello everybody!

this is my first post, so let me apologize myself for the awful style first.
kdevelop provides a graphical interface for the gdb.
configure it, by following these steps:

1.) make a new project:
to make it as simple as possible choose the SIMPLE HELLO WORLD one

2.) build the project with F8

3.) configure the debugger:
PROJECT\PROJECT SETTINGS\DEBUGGER and enter '--enable-debug=full' as the Program arguments;
for the gdb directory insert '/usr/bin'
exit with the OK-button

4.) rebuild your project

5.) debug your programm by adding breakpoints everywhere you find it useful.
(start the debugger with DEBUG\START)

6.) now you can watch your variables, step through your program,...

ps: for other projects it's always a good idea to the compile options -Wall -g if you have to debug your programs the graphical way.
if s.b. has other good ideas, please post it here.

---

### Post by flowtron on 2006-10-03
Although this thread is already pretty old it seemed most appropriate.

I've been trying to debug a threaded app,
which is a problem in it's own right; the issue with gdb I'm having is the following :

With Ubuntu (6.06) I only get about 12 lines of backtrace,
running thew same under Debian Sarge I get at least 42 lines ...
... which give a lot more insight.
My question is : Why does it not show as much backtrace in Ubuntu (6.06)
and : Can I somehow fix this myself?

The update of the gdb package today raised my hopes,
but still - the backtrace is too short to be helpful. :-/

---

