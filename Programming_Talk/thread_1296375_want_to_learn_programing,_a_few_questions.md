---
title: "want to learn programing, a few questions"
date: 2009-10-20
forum: Programming Talk
---

### Post by insanity99 on 2009-10-20
hey i want to learn a programing language so hopefully i can make my own software one day.

i have a few quesations.
1. is Python a suitable language for programing software for linux?
2. what is the best place to learn python
3. is idle a good enough program for me?

thanks.

---

### Post by steeleyuk on 2009-10-20
1. Yes
2. [http://docs.python.org/](http://docs.python.org/)
3. Depends on your needs. I just use a text editor.

---

### Post by insanity99 on 2009-10-20
thanks. is idle used as a complier?

---

### Post by JDShu on 2009-10-20
python does not need to be compiled

---

### Post by insanity99 on 2009-10-20
oh i see now. to make an executable on ubuntu the first line must be "$ chmod +x myscript.py" correct? the tutorial doesn't explain this command though so i dont fully understand it.

---

### Post by XxionxX on 2009-10-20
It depends on what you mean by complied. If you mean compiled like in C(into a .exe) then no python does not need to be compiled Python is an interpreted language, but as explained [here]("http://effbot.org/zone/python-compile.htm") if you need to install python on the clients computer then you will need to bundle it with your program. As far as I know all Linux systems come bundled with python(I could be wrong).

---

### Post by Tony Flury on 2009-10-20
What that command does is as follows : 

```

Chmod : Change Mode - in other words change the permissions

```

```

+x - Add the Executable bit - a signal to Linux that this file can be run

```

```

myscript.py"

```

This is the name of your file (that should be obvious),

For more information on the chmod command, type the command :
```

man chmod

```
at the command line to bring up the manual page for chmod

Your python file should also contain the following line as the very first line :
```

#!/usr/bin/env python

```

This tells linux how to run this script - i.e. to use the python interpreter.

I hope that helps.

---

### Post by insanity99 on 2009-10-20
ah thanks that helps a lot.

---

### Post by insanity99 on 2009-10-20
do you guys reccomend any books? or just use the documentation?

---

### Post by snova on 2009-10-20
> **insanity99 said:**
> do you guys reccomend any books? or just use the documentation?

I find the official tutorial to be a bit heavy in some places, but there is no shortage of ways to learn Python.

[Here's one]("http://www.greenteapress.com/thinkpython/thinkpython.html") that the #python IRC channel suggests in their topic, and I know a few people who use [this one]("http://www.swaroopch.com/notes/Python"). [Searching]("http://www.google.com/search?q=python+tutorial") for them turns up [more]("http://www.diveintopython.org/").

---

### Post by steeleyuk on 2009-10-20
Personally, for Python I use the docs + plenty of Google searching for anything specific or related to modules.

---

### Post by insanity99 on 2009-10-20
> **snova said:**
> I find the official tutorial to be a bit heavy in some places, but there is no shortage of ways to learn Python.

[Here's one]("http://www.greenteapress.com/thinkpython/thinkpython.html") that the #python IRC channel suggests in their topic, and I know a few people who use [this one]("http://www.swaroopch.com/notes/Python"). [Searching]("http://www.google.com/search?q=python+tutorial") for them turns up [more]("http://www.diveintopython.org/").

yeah i agree thew tutorial does seem to throw you in the deep end. thanks.

---

### Post by insanity99 on 2009-10-21
should i have python 3? because i have 2.6.2.

also should this not work when i double click myscript.py?
[PHP]#! $ chmod +x myscript.py 
#!/usr/bin/env python
>>>print 'Hello World!'[/PHP]
or did i do something wrong? when i click it it just opens gedit and displayed the source. and yeah i just call it myscript.py because it's a small test. i saved to desktop.

---

### Post by falconindy on 2009-10-21
> **insanity99 said:**
> should i have python 3? because i have 2.6.2.

also should this not work when i double click myscript.py?
[PHP]#! $ chmod +x myscript.py 
#!/usr/bin/env python
>>>print 'Hello World!'[/PHP]
or did i do something wrong? when i click it it just opens gedit and displayed the source. and yeah i just call it myscript.py because it's a small test. i saved to desktop.
The first line of any script file needs to be the path to the interpreter -- you'll see this referred to as the 'shebang', 'crunchbang', 'hashbang', or other names. The 'chmod' command needs to be executed from the terminal, and not placed in the script.

---

### Post by insanity99 on 2009-10-21
oh. what does the #! mean to terminal?

also is there a way to make my program wait for me to press a button before closing? seems to close instantly.

EDIT i went to the path '/usr/bin/env python ' but it isn't there. is my python installed wrong?

---

### Post by CptPicard on 2009-10-21
> **insanity99 said:**
> oh. what does the #! mean to terminal?

"Feed the rest of the file into this executable's standard input"

> 
EDIT i went to the path '/usr/bin/env python ' but it isn't there. is my python installed wrong?

What that line does is that it runs the command "env" with parameter "python", which locates the actual python installation for you on the specific machine, and then pushes the rest of the file to that. (Try running "/usr/bin/env python" on terminal to see what it gives you)

---

### Post by insanity99 on 2009-10-21
thanks that helped :D

---

### Post by snova on 2009-10-21
> **insanity99 said:**
> should i have python 3? because i have 2.6.2.

No. It's usually best to avoid Python 3 for now, as there is very little third-part support for it yet (it breaks a lot of compatibility). Nice things like Twisted, PyQt/PyGTK, and most everything else are still unavailable.

> also should this not work when i double click myscript.py?

[php]#! $ chmod +x myscript.py 
#!/usr/bin/env python
>>>print 'Hello World!'[/php]

The >>> shouldn't be there, in addition to what others have said. That is just what the interactive interpreter prompts you with.

> **CptPicard said:**
> "Feed the rest of the file into this executable's standard input"

Technically, what it does is run the program with the filename as its argument. For example, try running this script:

```
#!/bin/rm
```

It's self-deleting.

---

### Post by insanity99 on 2009-10-21
thanks. that last command would delete my bin folder would it not?

---

### Post by NoaHall on 2009-10-21
No. It would run the binary for the rm command.

---

### Post by insanity99 on 2009-10-21
ah ok.

the guide i am using is very math heavy. i was trying to avoid it. lol.

example
```
Exercise 2.4 Practice using the Python interpreter as a calculator:
  1. The volume of a sphere with radius r is 4 &#960;r3 . What is the volume of a sphere with radius 5?
                                              3
     Hint: 392.6 is wrong!

```
im like...what?!

---

### Post by The Cog on 2009-10-22
> >>> 4 / 3 * math.pi * 5 * 5 * 5
392.69908169872417
>>> 4.0 / 3 * math.pi * 5 * 5 * 5
523.59877559829886
You need to understand why the answers are so different. The first one is wrong because it does an integer division of 4/3 which gives 1.

---

### Post by insanity99 on 2009-10-23
yeah i think you would need to do 4.0/3.0 coreect?

i also have a hard time with understanding what the math moduel is.

---

### Post by The Cog on 2009-10-24
> **insanity99 said:**
> yeah i think you would need to do 4.0/3.0 coreect?

Actually, 4.0 / 3 does the trick because the result of a calculation involving a floating point number and an integer is always a floating point number. So only the first number actually needs to be a float. You could also re-order like this:
math.pi * 4 / 3 * 5 * 5 * 5
because pi is a float. It might be better practice to specify all your constants as floats though, to avoid confusion later.> 
i also have a hard time with understanding what the math moduel is.
It contains useful mathematical values and functions - a kind of math toolkit. It contains an accurate value of pi for instance, and functions for doing maths calculations. Try these two commands in a python command prompt:
> import math
help(math)
so your formula could have been:
> 
import math
r = 5
print 4.0 / 3.0 * math.pi * math.pow(r, 3)

---

### Post by insanity99 on 2009-10-24
> **The Cog said:**
> Actually, 4.0 / 3 does the trick because the result of a calculation involving a floating point number and an integer is always a floating point number. So only the first number actually needs to be a float. You could also re-order like this:
math.pi * 4 / 3 * 5 * 5 * 5
because pi is a float. It might be better practice to specify all your constants as floats though, to avoid confusion later.
It contains useful mathematical values and functions - a kind of math toolkit. It contains an accurate value of pi for instance, and functions for doing maths calculations. Try these two commands in a python command prompt:

so your formula could have been:

thanks i get it now.

---

