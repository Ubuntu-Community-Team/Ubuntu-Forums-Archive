---
title: "Python 1st code not working?"
date: 2010-02-17
forum: Programming Talk
---

### Post by WannabeFantasma on 2010-02-17
HELLO,

I wanted to learn how to program and in the Ubuntu Magazine Full Circle I found programming in python

I did the first page,[http://img171.imageshack.us/img171/5056/python1.jpg]("http://img171.imageshack.us/img171/5056/python1.jpg")

But when I want to type my name, the terminal closes...

so i'm allready stuck on lesson number 1... :(

can someone help me?

---

### Post by jfparis on 2010-02-17
[LEFT]:)

How are you running the program. If you double click on the file in nautilus that is normal that it closes the window as the execution is terminated

You need to open a terminal

then execute the script by launching 

```
python script1.py
```[/LEFT]

---

### Post by WannabeFantasma on 2010-02-17
kjeld@kjeld-desktop:~$ python hello.py
python: can't open file 'hello.py': [Errno 2] No such file or directory

(hello.py is the name of the file anyway)

I open it by double clicking and saying "Run in terminal"

(aargh even this "easy" tutorial is too hard for me! :D )

Maybe first tell me in an easy way to make it executable?
Now i do right click-> properties->Permissions-> Allow executing file as program(enable it)

---

### Post by munky99999 on 2010-02-17
Go into a terminal. Goto edit->profile preferences->title and command-> Then the last option. When command exits; Set it to hold the terminal open.

Alternatively you can do the python hello.py when you are in the correct folder. Or give the full path to the file.

python $HOME/Desktop/hello.py

That's likely where you put it I suspect.

---

### Post by WannabeFantasma on 2010-02-17
> **munky99999 said:**
> Go into a terminal. Goto edit->profile preferences->title and command-> Then the last option. When command exits; Set it to hold the terminal open.

Alternatively you can do the python hello.py when you are in the correct folder. Or give the full path to the file.

python $HOME/Desktop/hello.py

That's likely where you put it I suspect.

Thanks alot! :)
works now!  (1st thing)

btw I tested that second thing too but that didn't work earlier...

---

### Post by blur xc on 2010-02-17
> **WannabeFantasma said:**
> kjeld@kjeld-desktop:~$ python hello.py
python: can't open file 'hello.py': [Errno 2] No such file or directory

(hello.py is the name of the file anyway)

I open it by double clicking and saying "Run in terminal"

(aargh even this "easy" tutorial is too hard for me! :D )

Maybe first tell me in an easy way to make it executable?
Now i do right click-> properties->Permissions-> Allow executing file as program(enable it)

```
chmod u+x hello.py
./hello.py
```Read up a little on bash commands and linux file permissions.  There's a lot on the web to learn from.  Right now you seem to be fighting two battles- learning python while at the same time learning some cli skills.

I'm a noob in both bash and python- but I have read a few books on bash before I started playing w/ python.  Right now I'm reading IYOCGwP (Invent your own computer game with python), Dive into Python, and a Byte of Python.

I decided to do it the hard way and code in vim- just to add a third thing to my learning curve.  It's a bit slow going...

BM

---

