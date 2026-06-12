---
title: "'Clear' for python interpreter??"
date: 2009-03-25
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-25
Just as there is clear and reset which clears the screen of your terminal, is there anything similar for the python interpreter. 
Or do i have to write a script for that also??
I have to keep exiting python and clearing the screen and then reenter.

---

### Post by elCabron on 2009-03-25
In a terminal you could use Ctrl-L to "clear" the screen.

---

### Post by sujoy on 2009-03-25
offtopic, but i will mention it anyways, :P
try out ipython (it got completions )

---

### Post by nvteighen on 2009-03-25
> **i.mehrzad said:**
> Just as there is clear and reset which clears the screen of your terminal, is there anything similar for the python interpreter. 
Or do i have to write a script for that also??
I have to keep exiting python and clearing the screen and then reenter.
What you need is terminal handling. In other words, ncurses...

[http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

---

### Post by Can+~ on 2009-03-25
> **i.mehrzad said:**
> Just as there is clear and reset which clears the screen of your terminal, is there anything similar for the python interpreter. 
Or do i have to write a script for that also??
I have to keep exiting python and clearing the screen and then reenter.

clearing and reenter? Why don't just create a python script file? (.py)

---

### Post by crui-zer on 2009-07-28
A very simple 2 line command
>>> import os - this can also help you call other os / system commands
>>>> os.system('cls')
This should clear the screen for python interpreter started on cmd prompt.

---

### Post by shadowh511 on 2009-07-28
> **crui-zer said:**
> A very simple 2 line command
>>> import os - this can also help you call other os / system commands
>>>> os.system('cls')
This should clear the screen for python interpreter started on cmd prompt.

but if you are on linux, its:

```
>>> os.system("clear")
```

my way of doing it would be

```

def clearScreen():
 import os
 os.system("clear")

```

---

### Post by JordyD on 2009-07-28
> **crui-zer said:**
> A very simple 2 line command
>>> import os - this can also help you call other os / system commands
>>>> os.system('cls')
This should clear the screen for python interpreter started on cmd prompt.

You are obviously not using Ubuntu. 'cls' is a valid command for the Windows command prompt, but this is an Ubuntu forums, so I imagine that the poster is using Ubuntu, and in that case you would use os.system('clear') as someone else mentioned.

But still, that's not portable. You can do something like this:
```
import platform
import os
if platform.system() == 'Windows':
    os.system('cls')
else:
    os.system('clear')
```

or you can do something like this, though it's sort of hack-ish:
```
print '\n' * 100
```

It of course will break if you have a lot of lines in your terminal.

---

### Post by Unixarcade on 2011-05-16
I came to the forum because I was looking for this solution and the code worked thank you for all of your hard work.

---

### Post by cgroza on 2011-05-16
> **shadowh511 said:**
> but if you are on linux, its:

```
>>> os.system("clear")
```my way of doing it would be

```

def clearScreen():
 import os
 os.system("clear")

```

It is not recommended to import modules in a function that you will run several times.
EDIT: Sorry, did not see this thread dates from 2009.

---

### Post by 7raTEYdCql on 2011-05-17
On ipython !clear does the job. Thanks for your responses everyone.

---

