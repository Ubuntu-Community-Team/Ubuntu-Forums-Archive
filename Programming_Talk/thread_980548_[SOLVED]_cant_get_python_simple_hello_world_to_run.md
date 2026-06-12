---
title: "[SOLVED] cant get python simple hello world to run from comman line"
date: 2008-11-12
forum: Programming Talk
---

### Post by aszxcv on 2008-11-12
$  sudo python HelloWorld.py
python: can't open file 'HelloWorld.py': [Errno 2] No such file or directory

---

### Post by days_of_ruin on 2008-11-12
> **aszxcv said:**
> $  sudo python HelloWorld.py
python: can't open file 'HelloWorld.py': [Errno 2] No such file or directory

Why use sudo?!

```
ls
``` in the same directory and post the output

---

### Post by aszxcv on 2008-11-13
here is python code i am using     print "Hello, World!" i saved the script in my desktop


but i still get an error
ray@ray-desktop:~$ ls python HelloWorld.py
ls: cannot access python: No such file or directory
ls: cannot access HelloWorld.py: No such file or directory

---

### Post by tvtech on 2008-11-13
I had a killer of a time the first time I tried doing this lesson too. I had to redo it three or four times before I got it right.  

if I remember what I was muckin' up I'll letcha know.

---

### Post by jimi_hendrix on 2008-11-13
display the output of plain old ls

---

### Post by aszxcv on 2008-11-13
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos

---

### Post by tvtech on 2008-11-13
if I remember right I had to change it from a hidden file to a non hidden file.  give that a try and see if that fixes it.

do a locate helloworld.py 
or whereis helloworld.py

it may have been a directory location problem..... I can't remember it's been a year or two since I was playing with it.

---

### Post by tvtech on 2008-11-13
try doing a locate .helloworld.py
or even whereis .helloworld.py

I promise it works, but the lesson is wrong, or missing some critical info on how to execute it.

---

### Post by aszxcv on 2008-11-13
no dice i dont know what gives 

i know how to run it on windows but i am just trying a basic hello world to get a feel for the command line and i cant get simpliest of programs to run

---

### Post by tvtech on 2008-11-13
yeah, it's a directory call problem.  I had a hell of a time getting it done the first time.  and I almost want to say that for some reason it was dumping it into a .  file directory which in linux means it's hidden.  so you had to remove the . and it worked.   it was something really simple that drove me nutts for hours.

---

### Post by sisco311 on 2008-11-13
type *python* and a space  

then drag and drop your script in the terminal.

read this to learn the basic commands:[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by aszxcv on 2008-11-13
still doesnt work

i even press pwd to get current directory then save the file in there

---

### Post by scoutstyle on 2008-11-15
hmm im having the same problem
i just installed ubuntu over my xp. (deleted xp)
and want to learn python (im new to programming and new to linux)
i installed kate.

save this as helloworld.py

#!usr/bin/python
# Filename : helloworld.py
print 'Hello World'

in the command i type
python helloworld.py

and i get the same erorr
python: can't open file 'helloworld.py': [Errno 2] No such file or directory

when i type ls i get
tk@tk-desktop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos


am i missing something here?

---

