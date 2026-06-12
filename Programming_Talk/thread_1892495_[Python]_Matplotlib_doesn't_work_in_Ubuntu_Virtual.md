---
title: "[Python] Matplotlib doesn't work in Ubuntu Virtualbox install?"
date: 2011-12-08
forum: Programming Talk
---

### Post by kramer65 on 2011-12-08
Hello,

I've got an Ubuntu 10.04 system on which I have Virtualbox installed with an identical Ubuntu 10.04 guest system. This is because I like to test some scripts in the "sandboxed" Virtualbox environment. I now have an odd situation though.

I like to create some graphs using matplotlib. I therefore opened the software center and added python-matplotlib and python-matplotlib-data. I did this in both the guest-system, AND the host-system. I then tested the example script from [this matplotlib-page](http://matplotlib.sourceforge.net/users/pyplot_tutorial.html):
```
import matplotlib.pyplot as plt
plt.plot([1,2,3,4])
plt.ylabel('some numbers')
plt.show()
```

The strange thing is now that on my host-system this works perfectly well, but on my guest-system it says: *ImportError: No module named pyplot*.

As said, both systems run Ubuntu 10.04 with matplotlib installed. They both have the same version of Python (2.6.5) and are nearly identical.

Does anybody have any idea why matplotlib wouldn't work in the Virtualbox guest system?

---

### Post by lukeiamyourfather on 2011-12-08
Open Python on the guest and have it list the available modules (example below, from a Mac since I'm on one now but it'll work in Ubuntu as well).

```

$ python
Python 2.6.1 (r261:67515, Jun 24 2010, 21:47:49) 
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> help('modules')

Please wait a moment while I gather a list of all available modules...

```

If you don't see that module then it might not have been installed properly.

---

### Post by kramer65 on 2011-12-08
Alright, I tried your command *help('modules')* and it lead to some varying results. The first time it ended in an endless loop about a thing called a "Speech Dispatcher" so I had to kill the process.

The second time it did print a lot of things. After first some more "Speech Dispatcher" nonense it listed a large list of modules. In it is matplotlib, but not pyplot.

I then tried it on my host-system and there it results in an error saying "*OSError: [Errno 13] Permission denied: '/home/kramer65/Desktop'*". This is obvious since I have a system in Dutch and my desktop-folder is by default '/home/kramer65/Bureaublad'. The weird thing is that the guest Ubuntu system is also in Dutch, so I wouldn't know why that doesn't result in an error. Maybe it has something to do with the fact that I have my home folder encrypted?

Anyway. So matplotlib is there, but not pyplot. Since I call for "matplotlib.pyplot" I don't know whether pyplot is some kind of "sub-module" which should be included with matplotlib or that I have to install it separately ( I am fairly new to python)?
I searched in the softwarecenter and there it doesn't list anything when I type pyplot.

Any other tips or hints? :o

---

### Post by MadCow108 on 2011-12-08
try importing it when starting python with -v and see if that gives any clue.

the module should be installed in /usr/lib/pymodules/python2.7/matplotlib/pyplot.pyc -> /usr/share/pyshared/matplotlib/pyplot.py

---

### Post by kramer65 on 2011-12-15
Ok, a few days later I "kind of" found out what's wrong. It seems to have "something" to do with the location or the permissions or something.

This is what I see happening. When I move the file from the folder it is in now (/home/kramer65/Desktop/python/Zrommelen/matplottest.py) to the Desktop it has no trouble executing. When I move it back it fails again. When I then give the python folder on the desktop another name and create another two folders on the Desktop: python/Zrommelen (same names as before) and move the matplottest.py in it the script executes as well. When I look at the permissions, the files that executes well and the one that doesn't have the exact same permissions: -rw-r--r--
Even though the file exectues on other locations fine with these permissions I changed the permission of the file that refuses to execute to -rwxr-xr-x. The folder in which the files are also all have the same permissions: drwxr-xr-x. I tried changing the names of the folders around, but this also has no effect.

Although I have some kind of a solution to get the file working (move the file to another folder) I still don't understand a thing of this. I am really completely lost here. :confused:

Does anybody have any other idea maybe?

---

### Post by kramer65 on 2011-12-15
NEVERMIND!!

I found the answer. At one point I had created another file in the same folder called matplotlib.py (to do some more tests with matplotlib). Within the folder also a new file had appeared called  matplotlib.pyc (is that the matplotlib.py compiled or something?). I guess matplottest.py somehow takes the matplotlib.pyc file when I import matplotlib, instead of taking the normal matplotlib.

So I deleted the matplotlib.py and matplotlib.pyc files and now it works like a charm again.. :-)

So as usual it was my own stupid mistake. #-o

Thanks for your attention anyway!

---

