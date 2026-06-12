---
title: "working with Python"
date: 2010-04-21
forum: Programming Talk
---

### Post by BlackRat90 on 2010-04-21
So im kind of new to Ubuntu and i was hoping to do some programming in Python. now i figured out that if i make a simple text document and put .py at the end it makes it a python file, and i have it set to be an executable file, but every time i run it it just blinks the terminal at me even though in the program it should be waiting for my input...Any help? Am i doing something wrong?

---

### Post by xander98989 on 2010-04-21
You should add
```
#! /usr/bin/env python
```
to the very first line of your script. Next you need to make the file executable by typing
```
chmod +x ./example.py
```
at the command line. After that you should be good to go. Also, if you'd like an IDE I can recommend Geany or IDLE. Just make sure the IDLE version matches your Python version.

---

### Post by Miljet on 2010-04-21
If you post the code you are trying to run, someone will be able to point out any errors. Otherwise, we are just guessing.

---

### Post by BlackRat90 on 2010-04-21
the problem is the program is executing but not working right.

---

### Post by BlackRat90 on 2010-04-21
> **Miljet said:**
> If you post the code you are trying to run, someone will be able to point out any errors. Otherwise, we are just guessing.

My bad!! of course!

```
print "hello world"
blah = raw_input()
```

that adding the 
```
#! /usr/bin/env python
```
fixed it, though to be honest i dont get why.

---

### Post by xander98989 on 2010-04-22
Since you are outside the Python shell you need to let Bash (or whichever) know you want to use a different type of shell to run your script. It's no coincidence that comments begin with a # in both Python and Bash. Even though this line is ignored by the Python interpreter Bash recognizes the #! as a directive. 

To avoid having to specify the shell in your script (or to keep the Python shell open after you're program is finished) you can always start Python with the script file as an argument.
```
python /path/example.py
```

I could be mistaken but it is my understanding that from the beginning Unix and GNU avoided relying on filename extensions for information, such as the *.exe in Windows, due to security and stability reasons.

---

