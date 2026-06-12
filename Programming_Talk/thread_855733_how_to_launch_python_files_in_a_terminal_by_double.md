---
title: "how to launch python files in a terminal by double clicking?"
date: 2008-07-10
forum: Programming Talk
---

### Post by dracule on 2008-07-10
I have a terminal based Python program

This is what i want to do:

Have a launcher icon which will launch a terminal window with my program already running. 

I just want to double click an icon on my desktop to run my program in a terminal.

---

### Post by galileon on 2008-07-11
try using 

bash /path/to/file/program.py

might work :)

---

### Post by samjh on 2008-07-11
> **galileon said:**
> try using 

bash /path/to/file/program.py

might work :)

Nope.  It doesn't. :)

1. Create a launcher (typically right-click on desktop and choose "Create Launcher")

2. In the Type field, select "Application in Terminal"

3. Fill in the name, specify the program, and any comments.

Viola!  Your program will launch in a terminal! :)

---

### Post by dracule on 2008-07-13
tried it and got:
"There was an error creating the child process for this terminal"


it runs fine if i go into terminal and go ./program.py

---

