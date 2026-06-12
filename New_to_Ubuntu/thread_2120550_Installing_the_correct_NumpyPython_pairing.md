---
title: "Installing the correct Numpy/Python pairing"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by Piano man on 2013-02-26
Hi everyone,

I would really appreciate some help on this problem. I have been working on it for a whole day and keep reaching impasse after impasse. I am trying to run Python (with Numpy, Scipy and Matplotlib). I spent hours trying to get it to work on Windows in Visual Studio before eventually giving up and downloading Ubuntu in a virtual machine. I am a bit more familiar with the UNIX command line and there seems to be a lot more help out there.

So, I have downloaded Python 2.7.3 and installed it. It seems to be working fine.
I also downloaded Numpy 1.7 and installed it, but I could not import it into Python (No module named Numpy). So after searching for a solution, I noticed that Numpy 1.6 is usually paired with Python 2.7. So I downloaded that, and tried to install it, but because I had already run the 'sudo apt-get install python-numpy' command, I was told that the latest version had already been installed. So I tried uninstalling Numpy 1.7 and deleted it from my folders. But now when I run the above command, I still get the same response. How do I go about setting up Numpy 1.6 to work with Python 2.7?
Or is there anything else that could be the problem?

Thank you for any help.

---

### Post by cariboo on 2013-02-27
You may not have much luck if you manually removed the numpy directories, but tyr:

```
sudo apt-get purge numpy
```

From man apt-get:

```
purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).
```

---

### Post by Vaphell on 2013-02-27
care to explain why you install stuff manually?
shouldn't you use the stock python (2.7.3 in ubuntu 12.10) and scipy, numpy that are tailored for it, available in the official repos?

```
$ python --version
Python 2.7.3
$ apt-cache search '^python-(sci|num)py'
python-numpy - Numerical Python adds a fast array facility to the Python language
python-numpy-dbg - Fast array facility to the Python language (debug extension)
python-numpy-doc - NumPy documentation
python-scipy - scientific tools for Python
python-scipy-dbg - scientific tools for Python - debugging symbols
```

---

### Post by Piano man on 2013-02-27
Thanks for the replies.
Cariboo907: I followed your advice and purged numpy
'sudo apt-get purge python-numpy'
and then I reinstalled it
'sudo apt-get install python-numpy'
and I got the same result - 'No module named numpy'

Vaphell: The reason I downloaded them externally is because when I originally set up Ubuntu in the virtual machine, version 12 wouldn't boot because of something to do with PAE, so I booted an earlier version 10, which didn't have the packages in the repos. I only remembered to update Ubuntu after I had downloaded all the packages. So I'm now running Ubuntu 12.
I tried installing the packages you listed, but only the numpy and scipy packages worked, not the dbg and doc ones.
When I open Python and type 'import numpy', I get 'No module named numpy'.

Any other ideas?

Thanks.

---

### Post by Vaphell on 2013-02-27
this is what i get in virtualized 12.10
```
$ python
Python 2.7.3 (default, Sep 26 2012, 21:53:58) 
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import scipy
>>> import numpy
>>> import some_junk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named some_junk
```


i use 10.04 as my main system and it's a similar story: stock python 2.6.5, scipy/numpy tailored for it
```
$ python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:04:36) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
>>> import scipy
>>> import some_junk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named some_junk
```

long story short - try to stick to official repos :) without knowing what you did exactly it's hard to tell why modules are not being picked up by python


btw i'd suggest not using unity environment. If there is no hardware accel available it emulates bling in software mode which can make the system dog slow.

btw #2. Learn to use the second part of the number too when you describe your setup. It's not a minor thing like a meaningless tertiary number of some v0.99.1111, it's YEAR.MONTH. 6 months can make a big difference, just ask people who hated 11.10->12.04 transition with a passion :)

---

