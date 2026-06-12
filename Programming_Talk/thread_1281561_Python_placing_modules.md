---
title: "Python placing modules"
date: 2009-10-03
forum: Programming Talk
---

### Post by McWeirdo on 2009-10-03
Hi,
I'm a bit confused as I'm new to python,apparently what's hard for me by "diving into python" is- how it works, and less the syntax(although I had problems at the beginning).
I'm using ubuntu 9.04 have python 2.4\5\6 3.0\3 installed pydev in eclipse and I also have ipython installed.

I've downloaded these examples :[http://examples.oreilly.com/9780596009250/](http://examples.oreilly.com/9780596009250/)
and they wrote there that I need to add the folder into lib/site packages somewhere( they had directions for windows users not linux).

I was searching for it and finally I found the folder in usr/local/lib/python2.5/6/3.0 (the /6/3.0 indicated version number) but I couldn't copy the folder cause it says I have no permission .
I tried to edit the site-packages folder permissions and I couldn't cause It said I'm not the "owner", so how do I change that?
 
and am I doing it right?
 
another thing is the 
#!/usr/bin/python
 
this ^^^^^ thing works ,and some of the python files from the example have this at the beginning , but some have #!/usr/local/bin/python and then when I run it through terminal it doesnt work( I mean i double click and then run in terminal).Is something wrong?
 
 
Thank You , 
MCW

---

### Post by wmcbrine on 2009-10-03
Your issues have less to do with Python, and more to do with Linux.

When the first line of a script starts with "#!", it's telling the system, "run this script with the program at this path". So if you have a /usr/bin/python on your system, but not a /usr/local/bin/python, then it stands to reason that the first would work, and the latter would not. Just edit the line to use the correct path -- or, nowadays, the preferred usage seems to be "#!/usr/bin/env python", which will find the Python interpreter wherever it's installed on the $PATH.

And yeah, you don't have permission to write to /usr/local, since it's owned by "root", and you're not running as root. You do *not* want to change this. Rather, just assume temporary permission, by using the "sudo" command. You prefix this to whatever you're trying to do that needs root permissions:

```
sudo cp whatever /usr/local/bin
```

It will prompt you for your password the first time, or if you haven't done any sudo'ing in a while.

This is basic Ubuntu Linux admin stuff. It sounds like you need to get more familiar with the command line in general, and with the filesystem layout, and permissions.

---

### Post by McWeirdo on 2009-10-03
> **wmcbrine said:**
> Your issues have less to do with Python, and more to do with Linux.

When the first line of a script starts with &quot;#!&quot;, it's telling the system, &quot;run this script with the program at this path&quot;. So if you have a /usr/bin/python on your system, but not a /usr/local/bin/python, then it stands to reason that the first would work, and the latter would not. Just edit the line to use the correct path -- or, nowadays, the preferred usage seems to be &quot;#!/usr/bin/env python&quot;, which will find the Python interpreter wherever it's installed on the $PATH.

And yeah, you don't have permission to write to /usr/local, since it's owned by &quot;root&quot;, and you're not running as root. You do *not* want to change this. Rather, just assume temporary permission, by using the &quot;sudo&quot; command. You prefix this to whatever you're trying to do that needs root permissions:

```
sudo cp whatever /usr/local/bin
```It will prompt you for your password the first time, or if you haven't done any sudo'ing in a while.

This is basic Ubuntu Linux admin stuff. It sounds like you need to get more familiar with the command line in general, and with the filesystem layout, and permissions.

Alright, Thanks, I thought I did get to know linux enough , apparently not. hmmm than I have a question in python: The memorizing operation, aka memo{0:0,1:1} , is it like a dynamic array? while left side is index and right side is the value ?>? thank you!!!

---

