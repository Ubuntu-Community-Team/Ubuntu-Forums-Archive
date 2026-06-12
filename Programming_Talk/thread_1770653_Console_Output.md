---
title: "Console Output"
date: 2011-05-29
forum: Programming Talk
---

### Post by roadkillguy on 2011-05-29
I'm working on a little something in c++ that needs to output text to a console. I'd like to know two things:

A. Under linux, how do I make a terminal open up at runtime?  Running my program through file browser doesn't open one automatically, even If I specify /dev/tty in freopen.

B. When under windows, why is it that a console opens up but remains blank for the duration of my program?  When specifying "CON" it only redirects output when the program is run through cmd.  I'm cross compiling with mingw.

Basically, I need the user to be able to see what is going on in real time, and at this point it's ok to use #ifdef WINDOWS.

Thanks a bunch!

---

### Post by ziekfiguur on 2011-05-29
I don't think it's possible like you say it, though you could write a script that runs something like `xterm -e yourprogram'
But, why don't you just run the program from a terminal?

---

### Post by dwhitney67 on 2011-05-29
Under Linux, you have two options for running your program in a terminal:


1.  Open a terminal, goto where your program resides, and then manually run it from the command line.

2.  On your desktop, right-click and select "Create Launcher".  When the dialog box pops up, choose "Application in Terminal" for the Type.  For the command, specify the full path to the location of your program (e.g. /home/user/helloworld) or just browse for it.  The Name and Comment fields are optional.  When done, you should be able to double-click on the new launcher to run the program.


P.S.  Most Linux users prefer option 1.

---

### Post by roadkillguy on 2011-05-29
Hmmm... I certainly prefer to run things through the command line, but I was really only thinking about the layman.

I was able to get the windows part working with AllocConsole() and stdout under wine, so I guess that problem is solved.  [http://www.codeproject.com/KB/dialog/ConsoleAdapter.aspx?display=Print]("http://www.codeproject.com/KB/dialog/ConsoleAdapter.aspx?display=Print") helped with that.

---

