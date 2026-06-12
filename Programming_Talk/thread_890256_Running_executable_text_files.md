---
title: "Running executable text files"
date: 2008-08-14
forum: Programming Talk
---

### Post by ZachS on 2008-08-14
Hi, I am relatively new to linux and python, which I am currently trying to learn. I made a small executable file in python:

#!/usr/bin/env python
print 'Hello World'

and saved it as brian, then added chmod +x to it.
However, when I double click the actual file icon and the popup comes up with the usual options (Run in Terminal, Run) and I click on Run, nothing happens. What am I doing wrong here?

---

### Post by OutOfReach on 2008-08-14
The script trys to print out "Hello World" to the console, but there is no console, so nothing displays. Instead, try Run In Terminal

---

### Post by ZachS on 2008-08-14
I did, and still nothing happened.

---

### Post by OutOfReach on 2008-08-14
Open a terminal and navigate to where your script is stored and then type
```
./your_script.py
```
it should work.

---

### Post by mike_g on 2008-08-14
Maybe its because need to add a ./ before it. IE: 
```
./progname
```

---

### Post by Zack McCool on 2008-08-14
Open a terminal and run it from the command line.  If it doesn't work, you should be able to give some error messages...

---

### Post by Mothinator on 2008-08-14
This is probably because it is executing so fast, you don't see the window pop-up (if you choose run in terminal). If you choose run, it will execute in the background and you won't see anything.

Try opening a terminal, cd to the directory, and type ./brian

You should see Hello World  and then be dropped back to the command prompt.

---

### Post by pmasiar on 2008-08-14
install simple Python IDE, called IDLE. It will help you to avoid all such problems.

See wiki in my sig for links, tasks and tricks for Python learners

---

### Post by Can+~ on 2008-08-14
Terminal usually opens, runs the command and closes. A workaround is to request user input, which pauses the shell:

[PHP]print "Hello world"
raw_input("Click to finish.")[/PHP]

---

