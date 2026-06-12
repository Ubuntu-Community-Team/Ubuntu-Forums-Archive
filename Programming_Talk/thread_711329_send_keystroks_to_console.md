---
title: "send keystroks to console"
date: 2008-02-29
forum: Programming Talk
---

### Post by Green_Star on 2008-02-29
I have a program running on Unix environment. Once I start that program it has a menu kind of options(not gui, just console) and couple of forms to fill etc. I want to automate that process using shell script. 

My idea of doing shell script is like

1. execute that program to start.
2. select the oppropriate menu option
3. fille the form with already given values. 

I need to send following keys to complete that task

Down/Up Arrow, Ctl+x, Ctl+e, all alphanumaric chars.

I can do some shell programming but do not know how to send above keys !!

and that is a full screen(in console) application, is there any way to read text located at specific co-ordinates and specific length? 

Thanks in advance.

---

### Post by pmasiar on 2008-02-29
menu using nCurses or something?

non-GUI text based programs have either commandline parameters, or ask for input in commandline, wait, and process it. I have hard time imagining what exactly you are trying to do, and why.

---

### Post by Mr. C. on 2008-02-29
There's a problem...

When you run a command line program that reads from your terminal via STDIN, it reads what is typed from that TTY.

You can put your keystrokes in a file, and have your command line program read from the file via redirection or a pipe, but then you have no TTY and can't type anything more yourself (eg. you've lost TTY input control).  It is also possible that such a program is programmed to only accept values from a TTY and not from a redirected STDIN.  This then requires more software to work around.

There were (are?) ways to stuff characters into another TTYs character queue; but this requires some programming on your part.

Once the characters are output to the screen, the TTY driver itself doesn't readily give you access to the characters at given screen coordinates; in fact, it doesn't know anything about coordinates.  Rather, the terminal emulator is responsible for this.  And control of the terminal emulator is typically managed by the program itself, using a screen library like curses, ncurses, or manage the screen display by themselves via lower level terminal libraries which use termcap/termlib.

For you to do what you want would require you to not only intercept the characters input and output, but you would have to interpret the special meanings of various terminal emulator key sequences to know what the screen looked like.  And that is a *much harder* problem.

If you input is simple, and easily scripted, and you need no more input outside of what you place into a file, and don't need to interpret what is on the screen, you can solve this.  You just have to learn what exact key sequences are being output.   I'll explain how if this is sufficient and meets your needs.

---

### Post by Green_Star on 2008-03-11
Thanks guys, i will research on that software and let you know.

Basically it is like an editor it has text menus, like old style C language editor on DOS. Or a mainframe screen.

---

