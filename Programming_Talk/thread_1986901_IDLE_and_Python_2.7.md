---
title: "IDLE and Python 2.7"
date: 2012-05-25
forum: Programming Talk
---

### Post by J Swarthout on 2012-05-25
Hey everyone

I'm new to Ubuntu/Linux and programming in Python as well.  I installed Ubuntu on my parents old dell yesterday.  The last two weeks or so I've been learning Python.  I installed idle on my windows computers and haven't had any issues using it so far.  Now I'm trying to use IDLE for Ubuntu and am having quite a few problems.  I'm new to this so if these seem like dumb questions please bear with me.  Any help would be appreciated.

-When I write a file in IDLE and save it to a file on my desktop with the .py extension and then proceed to click on it, instead of executing the file like it does in windows it just comes up as a text file with the code.  In windows a command prompt comes up and executes the file as written. 

-I wrote the following code
   
       name = input("Hi.  What's your name? ")
       print(name)
       print("Hi,", name)
       input("\n\nPress the enter key to exit.")

When I run this in the shell it will prompt me to enter my name like it should.  Then after entering it I get this big error message in red print.

Maybe I'm missing something simple here-any help would be appreciated.

---

### Post by samitharansara on 2012-05-25
I'm not sure what you are after, but I assume you want to execute a .py script without typing 

```
python myscript.py
``` in a terminal.

So the first thing you should do is , give the path to the interpreter.  As such, include this line on the top of your file

```
#!/usr/bin/env python
```

Then make your .py file an executable..

```
$ chmod +x myscript.py
```

And to run it, type

```
./myscript.py 
```

---

### Post by J Swarthout on 2012-05-27
Ok so when I write this code
```

name = "Steveo"
print(name)
print("Hi,", name)

input("\n\nPress the enter key to exit.")
```

This is the output I get from IDLE

> 
Steveo
('Hi,', 'Steveo')


Press the enter key to exit.

I push enter and get this

> 
Traceback (most recent call last):
  File "/home/steve/Desktop/PythonFiles/steveo.py", line 5, in <module>
    input("\n\nPress the enter key to exit.")
  File "<string>", line 0
    
   ^
SyntaxError: unexpected EOF while parsing


and its in red.  When I do this on my windows machine it works as it should.

---

### Post by Bachstelze on 2012-05-27
Never ever use input() in Python 2.x. Always use raw_input(). the reason you are getting this error is that Python is trying to parse the string you get it (and fails, because there is nothing for it to parse).

---

### Post by J Swarthout on 2012-05-27
Thank you so much.  One more question. Why does the 

> Hi,Steveo

come out like this

> ('Hi,','Steveo')

---

### Post by Bachstelze on 2012-05-27
Because in Python 2, print is a statement, not a function. You should do

```
print "Hi,", name
```

If you wrap parentheses around it, you create a [tuple](http://docs.python.org/tutorial/datastructures.html#tuples-and-sequences).

---

### Post by J Swarthout on 2012-05-27
Thanks again.  I'm currently reading this book 

[http://www.amazon.com/Python-Programming-Absolute-Beginner-Edition/dp/1435455002/ref=sr_1_1?ie=UTF8&qid=1338137549&sr=8-1](http://www.amazon.com/Python-Programming-Absolute-Beginner-Edition/dp/1435455002/ref=sr_1_1?ie=UTF8&qid=1338137549&sr=8-1)

to learn python.  And while its a great book thus far I had no idea the syntax only worked on windows computers-I had no idea there were so many differences.

---

### Post by Bachstelze on 2012-05-27
Python is the same on all platforms, if you have the same version of Python. From the looks of it, your book seems to be using Python 3, so you should use that.

---

### Post by J Swarthout on 2012-05-27
That's what did it, Thank You!

---

### Post by Ravi5kumar on 2012-08-07
> So the first thing you should do is , give the path to the interpreter.  As such, include this line on the top of your file

```
#!/usr/bin/env python
```

This is not working for me! I am using IDLE 2.7 on ubuntu 12.04..

---

### Post by Bachstelze on 2012-08-07
> **Ravi5kumar said:**
> This is not working for me! I am using IDLE 2.7 on ubuntu 12.04..

You should only use this if you plan to run Python scripts directly from the shell as executables. If you are using idle, you do not need it.

---

### Post by Ravi5kumar on 2012-08-07
I want that on double click the .py scripts should run.....

---

