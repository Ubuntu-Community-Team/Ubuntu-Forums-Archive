---
title: "Working with os module (python)"
date: 2013-10-23
forum: Programming Talk
---

### Post by wingnut2626 on 2013-10-23
I have this script :

```
while True:
	parm += 1
	pid = os.fork()
	if pid == 0:
		os.execlp('espeak', 'espeak','this is parm number'+str(parm))
		assert False, 'error starting program'
	else:
		print('Child is',pid)
		if input() == 'q' : break

```

And it does say 'This is parm number (parm)'  And it does print Child is (pid).  Im confused as to how this works though.  How is the pid of os.fork() == 0?   Whenever I run os.fork() from the interpreter it is never 0......

---

### Post by Vaphell on 2013-10-23
[http://docs.python.org/2/library/os.html#os.fork](http://docs.python.org/2/library/os.html#os.fork)

---

### Post by wingnut2626 on 2013-10-23
are there any conditions in which the child process id would not be 0?

---

### Post by wingnut2626 on 2013-10-23
another question.  Why does

os.fork, os.pid

result in 2 tuples of 2 items each?

---

### Post by Bachstelze on 2013-10-23
Uh, and what is your problem, exactly? Based on what you say, the program seems to work as expected...

---

### Post by Vaphell on 2013-10-23
fork clones the code and the data, with the difference that in the original (parent) you get a non-zero value, while in the child you get 0. The difference allows you to recognize in which parallel 'universe' you are - child gets to run through the pid==0 branch and parent goes through else

```
 parent            |  child
-----------------------------------------------
pid = os.fork()    | pid = os.fork()
if pid == 0:       | [COLOR="#0000FF"]if pid == 0:[/COLOR]
    stuff          |     [COLOR="#0000FF"]stuff[/COLOR]
[COLOR="#0000FF"]else:[/COLOR]              | else:
    [COLOR="#0000FF"]stuff[/COLOR]          |     stuff
```

[http://www.python-course.eu/forking.php](http://www.python-course.eu/forking.php)

---

### Post by wingnut2626 on 2013-10-23
Vaphell I owe you a beer (or whatever).  Thanks so much

---

### Post by wingnut2626 on 2013-10-23
So even though its miliseconds (or nano seconds) , it appears the parrent if/else block would execute first.....

---

### Post by spjackson on 2013-10-23
> **wingnut2626 said:**
> So even though its miliseconds (or nano seconds) , it appears the parrent if/else block would execute first.....
What makes you think that? The if and else branches are executed in separate processes, and to all intents and purposes these are concurrent.

---

### Post by Bachstelze on 2013-10-23
> **spjackson said:**
> What makes you think that? The if and else branches are executed in separate processes, and to all intents and purposes these are concurrent.

This point bears repeating (and emphasis). As it is, there is no way to predict which instruction (print or espeak) will be executed before the other. Assuming that one or the other will run first is a major mistake (called a *race condition*), which can have serious consequences. If for some reason you need to ensure that one or the other will run first, there are some mechanisms like mutexes which will let you achieve that, but unless you use such a mechanism, you must not assume either way.

---

