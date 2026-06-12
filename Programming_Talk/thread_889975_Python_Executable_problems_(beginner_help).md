---
title: "Python Executable problems (beginner help)"
date: 2008-08-14
forum: Programming Talk
---

### Post by ZachS on 2008-08-14
Hi I'm currently trying to learn python and I'm using a book. The book says that to make an executable script you can run at the shell you put a hash-bang, or this: (this is their example)

#!/usr/bin/python #the path to the python interpretor
print 'The Bright Side of Life...'

and then it says to save it as brian.py. Then you go to the shell and chmod +x to brian.py.

So I did all of that but when I type brian into the shell it says brian: command not found. What I am doing wrong that's not making brian.py an executable?

---

### Post by Kadrus on 2008-08-14
Have you tried ruinning : ./brian.py

---

### Post by Bachstelze on 2008-08-14
> **Kadrus said:**
> Have you tried ruinning : ./brian.py

Ditto.

Also, you should use [FONT="Courier New"]#!/usr/bin/env python[/FONT] instead of [FONT="Courier New"]#!/usr/bin/python[/FONT] to make sure your script runs on all platforms.

---

### Post by rlameiro on 2008-08-14
> **ZachS said:**
> Hi I'm currently trying to learn python and I'm using a book. The book says that to make an executable script you can run at the shell you put a hash-bang, or this: (this is their example)

#!/usr/bin/python #the path to the python interpretor
print 'The Bright Side of Life...'

and then it says to save it as brian.py. Then you go to the shell and chmod +x to brian.py.

So I did all of that but when I type brian into the shell it says brian: command not found. What I am doing wrong that's not making brian.py an executable?

> **Kadrus said:**
> Have you tried ruinning : ./brian.py

You use the "./" before the name of the script to "say" to the shell to search the executable file in the directory you are, or else the shell will search the command or program in the environmental folders like /bin.

---

