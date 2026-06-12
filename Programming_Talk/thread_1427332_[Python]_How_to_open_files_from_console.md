---
title: "[Python] How to open files from console?"
date: 2010-03-11
forum: Programming Talk
---

### Post by carlosgs91 on 2010-03-11
.

---

### Post by schauerlich on 2010-03-11
I'm not sure what you're trying to do. Are you trying to open a file to use in a python program?

```
fileobject = open("filename.txt", "r")
```

Will open the file read-only. You can also open it as read-write or binary.

Once it's open, you can read in a line like this:

```
line = fileobject.readline()
```

And go from there. See [here](http://www.penzilla.net/tutorials/python/fileio/) for details.

> The problem is that I'm on my ipod touch and if I try to open a .py file that way I get an error, I need to open it from the python console, not from the Terminal, so how can I?
Unless your iPod is jailbroken, I don't think you're going to be running python apps on there.

---

### Post by schauerlich on 2010-03-11
If you're trying to execute a python program from the python interpreter, you can use an exec statement. First, you have to open up the file you want to execute.

```
try:
    file = open("script.py", "r")
    exec file
    file.close()
except IOError:
    print "File couldn't be opened"
```

---

### Post by carlosgs91 on 2010-03-12
.

---

### Post by schauerlich on 2010-03-12
> **carlosgs91 said:**
> Thanks, but it wasn't that. I've solved the problem, I've done this:

```
cd somedir
python file.py
```

That's from the terminal, didn't you say you needed to do it from the Python interpreter...? Anyways, glad you figured it out.

---

### Post by carlosgs91 on 2010-03-12
.

---

### Post by Purple Penguin on 2013-02-26
> **schauerlich said:**
> That's from the terminal, didn't you say you needed to do it from the Python interpreter...? Anyways, glad you figured it out.

Thank you :D I've been trying to find out how to open a python file! Your trick did it. \\:D/

---

