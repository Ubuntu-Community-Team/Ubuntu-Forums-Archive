---
title: "Automated Bas User Input"
date: 2007-04-28
forum: Programming Talk
---

### Post by ediggs on 2007-04-28
Hello, I am using this program <http://web.mit.edu/drela/Public/web/avl/>.
Basically, it has a command line driven user interface. I want to perform the same sequence of user input about 60 times (one for each input file to AVL I have created). This would take me hours, but I want to write a script that will open the AVL program, and automatically enter commands. The problem is, when I open AVL in bash, it waits for a user input. Is there a way to do this in one bash process or can I control one process from another process? I have no clue how I would go about doing this? Any suggestions??

ecd

---

### Post by lloyd_b on 2007-04-29
Try this:

Create a text file, containing the exact sequence of responses you want to use for the program.  Call it, for example, "responses.txt".

Then, in a terminal window, "cat responses.txt | AVL" (I'm assuming that the command to run AVL is "AVL" - if it's something different, then substitute the correct command).  Note that the "|" is the "pipe symbol" (Shift + "\" on most US keyboards).

If the program using "stdin" for input (as most terminal programs do), then this should work.

Lloyd B.

---

### Post by bharatiaero on 2011-09-11
Hi
In Ubuntu..hope it works..I am at present not using Ubuntu...and for my thesis I have to do the same automation for many designs in XP.....How to do this in XP OS? any Idea how this same automation can be done in the cmd window or in a DOS script or any other script file? 

Thanks & Regards :)
Bharati.

---

