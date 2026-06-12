---
title: "Python function to read file as a string?"
date: 2007-05-14
forum: Programming Talk
---

### Post by jfinkels on 2007-05-14
Is there a function that allows me to use a file as one long string, so I don't have to go through a file line by line?

---

### Post by JamieC on 2007-05-14
Sure there is (you'll want 'r' as a mode if you're just reading):
```

open(<file>, <mode>)

```

It'll return an object, <object>.read  will read the files contents.

More info [here](http://docs.python.org/tut/node9.html).

---

### Post by bashologist on 2007-05-14
> **jfinkels said:**
> Is there a function that allows me to use a file as one long string, so I don't have to go through a file line by line?

You want the read function/method.
```
[COLOR="Gray"]# Example:[/COLOR]
linestring = open('filename.txt', 'r').read()

[COLOR="Gray"]# Then you can print it:[/COLOR]
print linestring

[COLOR="Gray"]# You can even make a list with it![/COLOR]
print linestring.split('\n')
```

---

### Post by JamieC on 2007-05-14
> **bashologist said:**
> [COLOR="Gray"]# You want the readline function.[/COLOR]
linestring = open('filename.txt', 'r').readline()

Actually, readline() will only return one line (signifed by a new line break) while readlines() returns a list of the lines within the file. The read function will read an entire file.

---

### Post by bashologist on 2007-05-14
> **JamieC said:**
> Actually, readline() will only return one line (signifed by a new line break) while readlines() returns a list of the lines within the file. The read function will read an entire file.

Yes, I know. I did a quick test to make sure then changed my reply in a few seconds(Give people a second to edit).

---

### Post by ghostdog74 on 2007-05-14
open() reads file by default, so there usually no need for 'r', as in open(filename) is just fine.

---

### Post by jfinkels on 2007-05-14
Woops, silly me...totally spacing out on .read()...thank you people! I owe you all a kiss.

---

### Post by jfinkels on 2007-05-15
Here's another question: if I want to open() a file, do I need to escape spaces in the filename? for example, can I open a file at /tmp/foo - bar.ogg like this
```

open('/tmp/foo - bar.ogg',r)

```
or will I have to escape spaces?

---

### Post by b1g4L on 2007-05-15
Use the os module to change to the directory where the file is stored. Here is a quick example. Assume you have a text file called 'test.txt' on your Desktop and your Ubuntu user name is 'user'.

```
import os

os.chdir('/home/user/Desktop')        #Change the directory to the Desktop
inputFile = open('test.txt', 'r')     #Open test.txt file in read mode
print inputFile.read()

inputFile.close()
```

Here is a good link describing the basics of the os module
[http://www.bembry.org/technology/python/notes/lesson_12.php](http://www.bembry.org/technology/python/notes/lesson_12.php)

---

### Post by ghostdog74 on 2007-05-15
> **jfinkels said:**
> Here's another question: if I want to open() a file, do I need to escape spaces in the filename? for example, can I open a file at /tmp/foo - bar.ogg like this
```

open('/tmp/foo - bar.ogg',r)

```
or will I have to escape spaces?

you can define your file with spaces in a variable using os.path.join()
```

filename = os.path.join("/tmp","foo - bar.ogg")
f= open(filename)

```

---

### Post by jfinkels on 2007-05-15
> **ghostdog74 said:**
> you can define your file with spaces in a variable using os.path.join()
```

filename = os.path.join("/tmp","foo - bar.ogg")
f= open(filename)

```

Ah, I see...so the os.path.join() function will take care of the white spaces in the filename (and path, too) if necessary?

---

### Post by ghostdog74 on 2007-05-16
> **jfinkels said:**
> Ah, I see...so the os.path.join() function will take care of the white spaces in the filename (and path, too) if necessary?

you can just try it out on your interpreter
```

>>> fi = os.path.join(os.getcwd(),"test file .gg")
>>> print fi
/home/test file .gg
>>> f = open(fi)
>>> f.readlines()
['sdfsdfds\n']

```
if os.path.join does not work, then the open() will give you an error.

---

### Post by jfinkels on 2007-05-16
> **ghostdog74 said:**
> you can just try it out on your interpreter
```

>>> fi = os.path.join(os.getcwd(),"test file .gg")
>>> print fi
/home/test file .gg
>>> f = open(fi)
>>> f.readlines()
['sdfsdfds\n']

```
if os.path.join does not work, then the open() will give you an error.

Thanks for the help. I may be coming back to ask more questions :P

---

