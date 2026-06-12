---
title: "help! - Python prog works through GEDIT but not through Ubuntu Terminal.."
date: 2010-10-12
forum: Programming Talk
---

### Post by lxnski on 2010-10-12
Dear Ubuntu Forums,

I am new to Python (and Linux) and have been studying from the book "Beginning Python - Using Python 2.6 and Python 3.1)

One of the codes which I have written is the following:
```

age=0
while True:
    how_old=input("Enter your age: ")
    if how_old=="No":
        print ("Dont be ashamed of your age!")
        break
    num=int(how_old)
    age=age+num
    print ("Your age is: ")
    print (age)
    print ("That is old!")


```

When I write and save this as .py through GEDIT everything runs perfectly. However, when I write this in the Ubuntu Python terminal and press enter, the program does not run completely. It prompts me for my age, and when I type "No" it gives me the following error: 

```

Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
  File "<string>", line 1, in <module>
NameError: name 'No' is not defined


```


Why am I getting this error when I run through the Terminal and not when I save as .py through GEDIT and open with the Python GUI??

Thanks in advance.

---

### Post by Blackbug on 2010-10-12
I couldnt get you clearly..when you save your code with <filename>.py
and run with terminal it should work. I tried to run your code, its working
 
I guess you are missing this line at the top of your file
 
#! /usr/bin/env python
 
Try using it..

---

### Post by mo.reina on 2010-10-12
the problem is probably that when you type
```
python <filename>
```

in the terminal, the default python is 2.6

the code you're writing is for python 3.x:

```
how_old=input("Enter your age: ")
```

so either use python 3.x with the code, or modify the code to be compatible with python 2.x:

```
how_old=raw_input("Enter your age: ")
```

---

