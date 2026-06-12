---
title: "[SOLVED] Python code does not work. Why?"
date: 2008-11-15
forum: Programming Talk
---

### Post by L-mental on 2008-11-15
Now this is really driving me mad. Is frustrating. I'm learning Python. I'm using the Game Development book from McGugan. It turns out the Apress books have no support -nice teaching for someone learning to write software!!-. Well, then I have to solve and figure things out by myself.
I'm using SciTE and python 2.5.2.
The piece of code that does not work is:

```
from tank import Tank

tanks = { "a":Tank("Alice"), "b":Tank("Bob"), "c":Tank("Carol") }
alive_tanks = len(tanks)

while alive_tanks > 1:
	
	print 
	for tank_name in sorted( tanks.keys() ):
		print tank_name, tanks[tank_name]
		
	first = raw_input('Who fires? ').lower()
..it continues...

```
then when executing, it goes:

> >python -u "tankgame.py"

a Alice (60 armor, 5 shells)
b Bob (60 armor, 5 shells)
c Carol (60 armor, 5 shells)
Who fires? Traceback (most recent call last):
  File "tankgame.py", line 12, in <module>
    first = raw_input('Who fires? ')
IOError: [Errno 9] Bad file descriptor
>Exit code: 1


I can't see where's wrong. If I put just the 12th line in the python prompt, it works:

> >>> first = raw_input('Who fires? ').lower()
Who fires? a
>>> print first
a
>>> 

so, where am I making the stupid error?
and why would you write a programming book with non-working sourcecode?

---

### Post by days_of_ruin on 2008-11-15
> **L-mental said:**
> Now this is really driving me mad. Is frustrating. I'm learning Python. I'm using the Game Development book from McGugan. It turns out the Apress books have no support -nice teaching for someone learning to write software!!-. Well, then I have to solve and figure things out by myself.
I'm using SciTE and python 2.5.2.
The piece of code that does not work is:

```
from tank import Tank

tanks = { "a":Tank("Alice"), "b":Tank("Bob"), "c":Tank("Carol") }
alive_tanks = len(tanks)

while alive_tanks > 1:
	
	**print **
	for tank_name in sorted( tanks.keys() ):
		print tank_name, tanks[tank_name]
		
	first = raw_input('Who fires? ').lower()
..it continues...

```


Whats with that print statement?Try removing that.

---

### Post by indecisive on 2008-11-15
No, the print statement alone just prints a blank line; that should not cause the problem.

---

### Post by nvteighen on 2008-11-15
My hypotheses:

1. The error is in line 13 (or the next one with code)... How does the code continue?

OR

2. That you're using unbuffered mode (python -u), try executing the file just using 

```

python tankgame.py

```

OR

3. (but very unprobable) A bug in Ubuntu. This is the second stdin-related issue we had today; now in Python. The first one was in Perl: [http://ubuntuforums.org/showthread.php?t=982827](http://ubuntuforums.org/showthread.php?t=982827)

---

### Post by L-mental on 2008-11-15
SciTE...
python.properties...
```
if PLAT_GTK
	command.go.*.py=python -u "$(FileNameExt)"
	command.build.SConscript=scons --up .
	command.build.SConstruct=scons .
```

I don't know why they're calling it unbuffered
And this is the SciTE as you download it, no changes has been made.

So, in short, solved. It was a stupid error, as I thought it was. SciTE running the script unbuffered under Linux is the problem.

I was not looking at that, as you run the script with F5 instead of getting to the prompt. Once again, doing things by hand on the prompt should be the way to go.

Thx, solved!

---

### Post by nvteighen on 2008-11-15
(pst... mark the thread as solved)

---

