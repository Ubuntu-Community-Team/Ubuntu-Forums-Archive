---
title: "python executables"
date: 2007-02-13
forum: Programming Talk
---

### Post by taxonrath on 2007-02-13
Im using IDLE and i was wondering how to make an executable with it. I havent found anything  about it using google. Can I even do it with IDLE? or am I just not looking hard enough?

---

### Post by Mirrorball on 2007-02-13
Just save your script as a text file with a .py extension and run it like this:
```
python whatever.py
```
Python executables are just ordinary text files.

---

### Post by kthakore on 2007-02-13
if you put:

```
#!/usr/bin/python

```
put this int he 1st line of you .py file, and then make it an executable, by either 
```
chmod 0777 yourfile.py 
```

then when you double click on yourfile.py it will open up. If it is a console app open it in a terminal.

---

