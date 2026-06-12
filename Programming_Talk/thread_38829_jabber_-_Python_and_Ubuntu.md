---
title: "jabber - Python and Ubuntu"
date: 2005-06-02
forum: Programming Talk
---

### Post by i-tech on 2005-06-02
hi i'm trying to write a python program for jabber but jabber library in pyhon which comes with Ubuntu seems not working. When i "import jabber" pyhton quits to console and codes did not execute!

---

### Post by dataw0lf on 2005-06-02
Does it throw off any errors?

It works fine for me (using Python 2.4)

---

### Post by i-tech on 2005-06-02
No errors. program does nothing when it executed like; ```
python jabber.py
``` ad when i try to import it after executing pyhtn interpreter interpreter shuts down??!! i could not figure it out.

---

### Post by thumper on 2005-06-03
[QUOTE=i-tech]No errors. program does nothing when it executed like; ```
python jabber.py
``` ad when i try to import it after executing pyhtn interpreter interpreter shuts down??!! i could not figure it out.[/QUOTE]

What does jabber.py contain?

---

### Post by i-tech on 2005-06-03
it contains  ```
import jabber
``` in the first line when i comment it out script executes with error.

---

### Post by thumper on 2005-06-03
I am guessing here, but is there another jabber python library that you are trying to include?

Python normally has the current working directory in the load path, and your file is called jabber.py, so saying import jabber will try to include itself until it either blows the stack or hits some predefined recursion limit.

Step one: rename your jabber.py to myjabber.py.

Step two: add some type of main block or print statement so you know that your file has been executed.

```
import jabber

print "Have imported jabber"

```

Now what happens?

---

### Post by i-tech on 2005-06-03
i tought of that and renamed the file as echo.py but it didnt changed and also tried print statement but it does nothing. if i comment out import jabber line it prints. I dont have any idea. do you think downloading that library and put the library to the same folder with echo.py will work? I couldnt think something else

---

### Post by thumper on 2005-06-03
[QUOTE=i-tech]i tought of that and renamed the file as echo.py but it didnt changed and also tried print statement but it does nothing. if i comment out import jabber line it prints. I dont have any idea. do you think downloading that library and put the library to the same folder with echo.py will work? I couldnt think something else[/QUOTE]
Where do you expect it to find jabber.py?

I would have thought that if you try to import jabber when it is not available you would get an ImportError.

Assuming that you don't have a file called jabber.py in the current working directory, if you start the python interactive shell and type 
```
import jabber
``` what do you get?

---

### Post by i-tech on 2005-06-03
it dies ,python interactive shell terminates... but when i tried in my friends ubuntu it works ok. I checked synaptic jabber library for python2.4 is installed.

---

### Post by thumper on 2005-06-03
OK, if you are running python 2.4 then you should get something like this when you start the interpreter

```
Python 2.4.1 (#2, Mar 30 2005, 21:51:10)
[GCC 3.3.5 (Debian 1:3.3.5-8ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

jabber.py should be found in /usr/lib/python2.4/site-packages, and my one is this big  ;-) 
```
tim@spike:/usr/lib/python2.4/site-packages$ ll jabber.py
-rw-r--r--  1 root root 51640 2005-01-14 00:08 jabber.py
```

How does that compare with your install?

Tim

---

### Post by i-tech on 2005-06-03
> -rw-r--r--   1 root root  51640 2005-01-14 02:08 jabber.py
-rw-r--r--   1 root root  52987 2005-04-01 00:58 jabber.pyc
-rw-r--r--   1 root root  52987 2005-04-01 00:58 jabber.pyo 

I have three files is it ok?
seem same size :)

---

### Post by thumper on 2005-06-03
Three is fine. 

.py is the source
.pyc is the compiled source
.pyo is the optimised source (I think)

Given that you have jabber.py, and that you are running python 2.4, I have run out of ideas.  

```
import jabber
``` worked fine on my box.

Sorry,
Tim

---

