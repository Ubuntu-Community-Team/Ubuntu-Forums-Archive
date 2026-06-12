---
title: "Good Place To Start ?"
date: 2006-11-15
forum: Programming Talk
---

### Post by jessewryan on 2006-11-15
Sorry for a basic newbie question but I am very interested in learning how to program, and too broke to go to college for it. Does anyone have any idea on a good place for me to start ? I downloaded Python but I have no idea where to begin. If anyone has any suggestions for me that would be great. Also, if there is a small basic program I could write to learn the ropes, maybe a calculator or something like that for a place to start. This would be great if someone could help me out. Thanks so much I appreciate it, and I appreciate this forum. Good stuff people. Keep it up !

---

### Post by po0f on 2006-11-15
jessewryan,

Python is a good first language to learn, if only for the interactive interpreter it has.  Try just typing `python` at a terminal and hit enter.  Anything you type should be Python code, and will get executed right away:
```
$ python<hit enter>
>>> print "Hello world!"<hit enter>
Hello world!
>>>
```

To exit the interpreter, hit Ctrl-D. (The dollar sign represents your prompt.)

A good place to start would be the [official docs](http://www.python.org/doc/2.4.4/).  I also found [A Byte of Python](http://www.ibiblio.org/g2swap/byteofpython/read/) very newb-friendly.

---

### Post by encompass on 2006-11-15
I agree... python is easy, structured, and powerful.  Ask cononical they are nuts about it.
I learned alot of it this summer.  I like it alot.  And if you read the instructions and try the work, and have problems... don't be scared to go to the IRC channels to find help too.

---

### Post by jessewryan on 2006-11-15
You guys are killer thanks. So I got the reply started the Python in GUI mode and typed python. And got:
[B]Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    python
NameError: name 'python' is not defined[/B]

Everytime I get an error like this I keep getting discouraged. Any more suggestions on what exactly I should do to get started ? Sorry for boggin you down with newbie questions, I am just starting to get frusterated and im on DIALUP so its hard for me to download tutuorials and such. Thanks in advance I really appreciate the help. It means alot.

---

### Post by jessewryan on 2006-11-15
Oh one more thing. I know im getting ahead of myself being that I dont know the language but to avoid tons of questions once I get a basic code layout and I want to try it in an EXE file how to I pack the code ? Using a basic EXE Compiler ? Sorry again. And Thanks.

---

### Post by jessewryan on 2006-11-15
Oh ya sorry im using Python 2.5 incase that makes a difference.

---

### Post by po0f on 2006-11-15
jessewryan,

Typing "python" while in the interactive interpreter will give you that error.  Try navigating to Applications->Accessories->Terminal.  Now type just `python2.5` and hit enter.  You should see something similar to the following:
```
$ python2.5<hit enter>
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02)
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Note: this is from a default Edgy install with the default Python 2.4.4, your output will be different with Python 2.5.

When you actually get a script or program hacked together, you can put it in /usr/local/bin, chmod it to give it execute permission, and you should be able to run it like a regular command, provided that the first line of the script is `#!/usr/bin/python2.5`:
```
$ gedit myscript.py  (write your script, make sure first line is "#!/usr/bin/python2.5")
$ sudo mv myscript.py /usr/local/bin
$ sudo chmod +x /usr/local/bin/myscript.py
$ myscript.py
```

---

### Post by encompass on 2006-11-16
another nice program for python is idle... it is nice...

---

### Post by glickboy on 2006-11-16
Python is a fantastic language.  Im a computer engineer and have experience in C, C++, Java, and Assembly, and my favorite language by far is python.  Its elegant, easy to learn, and very powerful.  Learning to program is not really about learning a particular language.  Learning how to program is learning how to break apart problems into algorithems.  And you can do that with a pen and paper.  Designing Algorithms is basically what programming is all about.  Python is a great tool to use to learn about designing algorithms .  A great book that is a good introduction to programming and the python programming language is the book "How to Think Like a Computer Scientist using Python"
The book is available for free online in pdf format from greentree press.
A simple google search will take you to the link

---

### Post by 23meg on 2006-11-16
*Dive Into Python* is another good Python book. It's in the repositories.

---

