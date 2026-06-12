---
title: "Keep Terminal Interactive whilst/after running a Ptyhon program"
date: 2011-06-01
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-06-01
Hi,

When using IDLE, if i run a program, i can interact with it on the console after it has run.
If i use Geany, Eclipse or Netbean with Pyhon, the program runs and then it terminates. When i run a GUI, the cursor is idle, and i cannot interact with the program from the console in those programs either.

How can i keep the Console interactive so i can query my program?

Thanks.
B.

---

### Post by dwhitney67 on 2011-06-01
> **jesuisbenjamin said:**
> 
How can i keep the Console interactive so i can query my program?


Perhaps you are posing a trick question or I did not fully understand what you are asking?

Anyhow, if you want to continue interacting with the console (or terminal), try running the program in the 'background', using the & character following the program name.  For example:
```

myprog &

OR

python myprog &

```

---

### Post by TwoEars on 2011-06-01
By using execfile from within python - 
```

>>> execfile("file.py")
Hello world!
>>> execfile("file.py")
Hello world!
a is  2
>>> a=3
>>> a
3
>>> execfile("file.py")
Hello world!
a is  2
>>> main()
Hello world!
a is  2
```

(file.py in this case contains -)
```

#!/usr/bin/env python

a = 2
def main(*args,**kwargs):
	print "Hello world!"
	print "a is %d" % a
	
if __name__ == "__main__":
	main()
```

---

### Post by jesuisbenjamin on 2011-06-01
That didn't do what i wanted.

What i need is to be able to query the objects of my program while it's running or after it has run.
If i run a GUI, it enters the event-loop, while it's in the loop i want to query some vars from that running programs:

[PHP]
#! usr/bin/env python

import gtk

def main():
    print 'program is running!'
    var = 'foo'
    gtk.main()

if __name__='__main__'
    main()
[/PHP]

Then i run:
```

$ python ./main.py

program is running!
>>> print var
foo
>>> var = 'baz'
>>> print var
baz
>>> gtk.main_quit()
$ _

```

So what i need is to have access to the console, iow i want the '>>>' expecting me to enter some python commands lines.

---

### Post by jesuisbenjamin on 2011-06-01
Thanks TwoEars: i saw your response afterwards.

---

### Post by HornedBeast on 2012-02-14
Did you ever get to the bottom of this?

I have a piece of code that uses the GTK.Main loop and I wish to find out values or variables and objects whilst its running... but through the Python Interpreter.

For example, when I run gtk.main(), I then don't get the >>> in Python, so I can't issue commands. However, my software requires the gtk.main loop to be running, whilst also being probed for information.

Is there any way to do this!?

---

### Post by Tony Flury on 2012-02-14
Not exactly what you need - but this might help 

[http://www.pygtk.org/pygtk2tutorial/ch-Introduction.html#sec-ExploringPygtk](http://www.pygtk.org/pygtk2tutorial/ch-Introduction.html#sec-ExploringPygtk)

Whe i am debuggig a GTK application in Python - three things help me : 

1) a liberal sprinkling of useful print statements
2) a modular design - processing in one module (which can be tested and proved easily in the console, and GUI in another - so when you come to test the GUI you know that the bugs must be in you GUI code (and not your applicatio code) - see MVC type design pattern
3) Use of a decent debugger - IDLE has a good one if i remember correctly.

---

