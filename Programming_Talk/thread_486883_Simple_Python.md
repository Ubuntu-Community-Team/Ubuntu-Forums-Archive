---
title: "Simple Python"
date: 2007-06-28
forum: Programming Talk
---

### Post by ktown on 2007-06-28
I'm just starting to program with Python, and it is my first language so I'm not sure how it really works. I'm programming in IDLE, and trying to write an "if" statement. I'm just doing a simple guessing game, where the user tries to guess a number. When i ask for the number, it won't let me do the if statement until, i, as the programmer, enters the number. any ideas?

---

### Post by Siph0n on 2007-06-28
```
correct_num = 5
num = 0
while num != -1:
    num = raw_input("Guess the number please (enter -1 to quit): ")
    if num == correct_num:
        print "YOU ARE A WINNER!!!!!"
        break
```


Try that.... you didnt post any code so i didnt have anything to go off, why yours wasnt working... remember python is space sensitive, you have to indent (use spaces).

---

### Post by Modred on 2007-06-28
I'm guessing that your code is something like this:

```

>>> guess = int(raw_input())

```

Because you're in an interactive session, it will ask you for the input before moving on to the rest of the code.  You could alleviate this by putting the input and if statements inside a loop or [try/except](http://docs.python.org/tut/node10.html) block.  Then it would let you complete the entire block before asking for the input.  Note that the little snippit I did above can raise a ValueError exception if you don't enter an integer.

---

### Post by christhemonkey on 2007-06-28
If your programming in idle, it might actually just be an interactive python prompt.

To start a new python script, you have to go Fie > New in IDLE.

Then you can start coding :)

---

### Post by ktown on 2007-06-28
yeah it works when im not in the interactive python mode. how to i run/test my programs when i ham done with them?

---

### Post by Modred on 2007-06-28
From the command line you can type:

python my_prog.py

(replace my_prog.py with your file, obviously).

You can also put a "shebang" line on the top line of your .py files:

```

#!/usr/bin/env python
...

```

This will allow you to execute a .py file like any other command line program.  EG:

./my_prog.py

---

### Post by christhemonkey on 2007-06-28
If you are using idle,

you can type:
Alt+X

to check your script for errors.


To run it type:
F5

It then runs the script in the interactive python shell in the main window.

---

### Post by pmasiar on 2007-06-28
Go to wiki in my sig - check links for tutorials for complete beginners.

---

