---
title: "Compiling Code - Help Please?"
date: 2011-08-01
forum: Programming Talk
---

### Post by Mouse750 on 2011-08-01
I'm following this tutorial:

[https://trac.torproject.org/projects/tor/wiki/doc/PreventingDnsLeaksInTor](https://trac.torproject.org/projects/tor/wiki/doc/PreventingDnsLeaksInTor)

The part I am stuck on is:

> Then compile them because you want to make this read only. Normally python does this when you execute the files. However, when you call compileall, you only compile it to byte-code instead of executing the code. 

 This will recursively compile all python code it finds in that directory.
```
/usr/local/bin/python /usr/local/lib/python2.3/compileall.py dsocks-1.2
```


Now, this tutorial is a little old because I have python2.6, and dsocks-1.7 source code.

Ok, here is my problem:

```
/usr/local/lib/python2.6/compileall.py: No such file or directory
```

I have a python2.6 dir but I have no compileall.py. Where do I get this file from? I'm not sure but I think my Python2.6 came already installed with Ubuntu 10.10.

P.S. What is compiling to byte-code? Never heard of that before.

---

### Post by lisati on 2011-08-01
*Thread moved to **Programming Talk**.*

---

### Post by slavik on 2011-08-01
have you read the stickied threads for relevant information?
have you researched into this elsewhere?

---

### Post by Mouse750 on 2011-08-01
@slavik

I'm new to linux, know nothing about programing, compiling, etc however I am good at following directions.  

I will start sifting through the Stickies as per suggestion however I'm not exactly sure what I'm looking for. Some additional guidance may be necessary.

P.S I also tried sudo

and got the error: 

```
compileall.py: command not found
```

```
python --version
Python 2.6.6
```


I'll be reading some python tutorials in the mean time...



--

---

### Post by Arndt on 2011-08-01
> **Mouse750 said:**
> 
```
/usr/local/lib/python2.6/compileall.py: No such file or directory
```

I have a python2.6 dir but I have no compileall.py. Where do I get this file from? I'm not sure but I think my Python2.6 came already installed with Ubuntu 10.10.

P.S. What is compiling to byte-code? Never heard of that before.

I'm not sure it will help you, but I have a compileall.py in /usr/lib/python2.6. I found it using the 'locate' command.

Byte code is a form of processed source code where it has not been compiled to machine code, as typically happens in many languages (for example C++), but to a platform-independent code where instructions suited to the language take up one byte each. It makes the object code smaller, execution time longer, and helps portability. You may find files named *.pyc after you have used python - those files contain byte code.

---

### Post by Bachstelze on 2011-08-01
```
firas@wakaba ~ % locate compileall.py
/usr/lib/python2.6/compileall.py
/usr/lib/python2.6/compileall.pyc
/usr/lib/python2.7/compileall.py
/usr/lib/python2.7/compileall.pyc
/usr/lib/python3.1/compileall.py
/usr/lib/python3.1/compileall.pyc

```

:)

On Ubuntu you will never find anything in /usr/local, so when a tutorial tells you to look for something there, it is probably in /usr instead.

---

### Post by Mouse750 on 2011-08-01
Thanks for introducing me to the locate command.

```
locate compileall.py
/usr/lib/python2.6/compileall.py
/usr/lib/python2.6/compileall.pyc
```

Ok, now that I know where compileall.py is 

I used:

```
sudo /usr/lib/python2.6/compileall.py dsocks-1.7
```

And again got the error:

> compileall.py: command not found

compileall.py had no execution permisions set, so I set them and tried again. Then I got the error:

: not found
import: unable to read X window image `': Resource temporarily unavailable @ error/xwindow.c/XImportImage/5023.
/usr/lib/python2.6/compileall.py: 19: __all__: not found
/usr/lib/python2.6/compileall.py: 21: Syntax error: "(" unexpected

The tutorial is a tad old and I am using the source code for dsocks1.7 instead of dsocks1.1



--

---

### Post by Bachstelze on 2011-08-01
compileall.py does not have a "shebang" line, so run it like this:

```
sudo python2.6 /usr/lib/python2.6/compileall.py dsocks-1.7
```

---

### Post by Mouse750 on 2011-08-01
Thanks for the help.

---

