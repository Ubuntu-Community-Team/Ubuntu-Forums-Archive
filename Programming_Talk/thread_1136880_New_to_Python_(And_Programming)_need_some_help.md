---
title: "New to Python (And Programming) need some help"
date: 2009-04-25
forum: Programming Talk
---

### Post by RichardLinx on 2009-04-25
Hello, I started learning Python about an hour ago (sort of) and I'm having some trouble with the very basics. I wrote this program while following a tutorial:

```

# Filename : var.py

i = 5
print i
1 = 1 +1
print i

s = '''This is a multi-line string.
This is the second line.'''
print s

```

I saved it as "var.py" in a folder called "Python" which is located on my desktop. When I try to run the program I get this error message:

> 
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'var' is not defined
>>> 

I figure I've done something wrong or I'm not doing something I'm supposed to be doing. I'm a complete beginner though and am at a loss. I took a screen shot to if it will be of any help to you, to help me. :)

[[img=http://img528.imageshack.us/img528/8725/pythonhelp.th.jpg]](http://img528.imageshack.us/my.php?image=pythonhelp.jpg)

Cheers!

---

### Post by poisonkiller on 2009-04-25
If you want to run a program with Python, you have to write "python file.py" (without quotes) into Terminal.

---

### Post by simeon87 on 2009-04-25
You need to run with the following command:

```

python var.py

```

---

### Post by RichardLinx on 2009-04-25
Thanks guys! I got the output: ```
[Richard@localhost ~]$ python var.py
  File "var.py", line 5
    1 = 1 +1
SyntaxError: can't assign to literal

```
Which is something, finally! It's late now so I'll get back to this tomorrow. Thanks again! :)

---

### Post by Nevon on 2009-04-25
> **RichardLinx said:**
>   File "var.py", line 5
    1 = 1 +1
SyntaxError: can't assign to literal
[/code]

What is it that you're trying to accomplish here? 1 equals 1 plus 1 doesn't really make any sense.

---

### Post by Volt9000 on 2009-04-25
Based on the context of the program, I think that maybe the line

```

1 = 1 +1

```

Should be

```

i = i + 1

```

---

### Post by amingv on 2009-04-25
Check the tutorial example again, I think what you must write is:

```
i = 5
print i
i = i + 1 #notice the first two are 'i' and not the number 1 (one).
print i
```

You can't assign values to numbers as all numbers are constants

EDIT:
Yes, like Volt9000 said...

---

### Post by andyhumphries on 2009-04-26
As an aside, you can run a Python script as ./script.py if you include the following at the head of your source file:

```
#!/usr/bin/python
```Where /usr/bin/python is the path to your Python interpreter executable (this is the default path on Ubuntu).

You will also need to:

```
chmod 777 script.py
```in order to allow the script to execute.

Possibly a little too advanced for now, but hey - knowledge is power. ;)

---

### Post by Arndt on 2009-04-26
> **andyhumphries said:**
> As an aside, you can run a Python script as ./script.py if you include the following at the head of your source file:

```
#!/usr/bin/python
```Where /usr/bin/python is the path to your Python interpreter executable (this is the default path on Ubuntu).

You will also need to:

```
chmod 777 script.py
```in order to allow the script to execute.



777 does set the execution permissions, but it also sets all other permissions. For example, anyone will be able to write to the file. If you're the only user on the computer, that's of course not a problem.

(To those who don't know: the magic number 777 should be read as an octal number; i.e., it consists of three groups of three 'true' bits each.)

To just set the execution bits, do

```
chmod +x script.py
```

---

### Post by benj1 on 2009-04-27
for just small things like this you might like the python shell,
just type 'python' into a terminal, (im sure your book/tutorial says something about it) then you can try if things work straight away.

---

