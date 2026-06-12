---
title: "yeoman v0.90 now published"
date: 2011-04-23
forum: Programming Talk
---

### Post by eckeroo on 2011-04-23
Hello,

I've now published my code:

[http://bazaar.launchpad.net/~eckeroo/+junk/yeoman/files](http://bazaar.launchpad.net/~eckeroo/+junk/yeoman/files)

It's my first published piece of code written in Python and it is 14.1KB in size. Simply copy all the files to one directory. Make that directory the current working directory and type: 'python yeoman_v0_90.py'

The program is a GUI stress calculation manager called yeoman. The version is 0.90 and only one basic module 'simples.py' is available. Proper engineering python modules will be made available for it soon. The application is for stress engineering. I've put this thread up on this forum because I'm still learning Python and I got some excellent help here previously. I'd very much like some feedback on my latest work.

Cheers

eckeroo

The following is an extract from the doc string-

Yeoman GUI Dependencies:
Python v2.6.5-3
wxpython 2.8.11.0-1
wxgtk 2.8.11-1

Module dependencies:
python-numpy 1.4.1-1
python-scipy 0.7.2-1


Program Description:

Manages stress calculation files. Specific calculations are imported as single class Modules from the 
pull down menu. Each instant created by the module is a discrete calculation with its own inputs. All 
instances are managed by a wxpython tree control.

Instructions:

Created instances can be saved and reloaded. Modules can only be loaded from the current working directory.
Double click on a node name to create new component names, add new calcs or delete entire tree nodes.
Double click on an instance name to enter the calculation frame. Input data is stored in the upper frame and
calculated output data appears on the lower frame. Click the 'Calc' button to calculate.

Futher Notes and bugs:

1) yeoman_v0_90 only saves to one file named 'yeo_sav.py' located in the current workind directory.

2) a tree example is contained in the original 'yeo_sav.py'

3) root item name cannot be renamed - segmentation fault error raised

4) upcoming modules will be useful stress calculations including 'bolt group thermal loads', 'section 
properties', 'unit load for point load' and more.

5) line number 235 is set for linux operating systems. Replace '/' with '\' for windows.

---

### Post by Vaphell on 2011-04-23
regarding 5)
you can detect OS and use / or \ depending on the result
[http://stackoverflow.com/questions/1854/python-what-os-am-i-running-on](http://stackoverflow.com/questions/1854/python-what-os-am-i-running-on)

---

### Post by cgroza on 2011-04-23
I thought python takes care of the "/" when dealing with paths.

---

### Post by nvteighen on 2011-04-24
> **cgroza said:**
> I thought python takes care of the "/" when dealing with paths.

You have to use os.path.join for that. That function will return the string in the OS native format.

```

ugi@UGI:~$ python
Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.path.join("some_dir", "some_subdir", "some_file")
'some_dir/some_subdir/some_file'
>>> 

```

In Windows, this would return 'some_dir\some_subdir\some_file' instead.

---

### Post by cgroza on 2011-04-25
That is what I was thinking.

---

