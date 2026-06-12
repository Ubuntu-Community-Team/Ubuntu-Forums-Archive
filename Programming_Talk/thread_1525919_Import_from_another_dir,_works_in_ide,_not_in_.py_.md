---
title: "Import from another dir, works in ide, not in .py script."
date: 2010-07-07
forum: Programming Talk
---

### Post by MadnessRed on 2010-07-07
Here is my code:

```
#Basic
import os

#Current cwd
cwd = os.getcwd()

#Move in to folder
newcwd = '/home/madnessred/Python/FM/folder_views'
#newcwd = os.path.join(os.path.split(repr(__file__))[0][1:], 'folder_views')

#Set as cwd
os.chdir(newcwd)

#Dictionary to hold folderviews
folder_views = {}

#For each file
for view in os.listdir(os.getcwd()):

	#Is it as expected
	if view.split('.')[1] == 'py' and len(view.split('.')) == 2:

		#Import it
		folder_views[view.split('.')[0]] = __import__(view.split('.')[0], globals(), locals(), ['view'])

#Go back to original dir
os.chdir(cwd)

#Output
print folder_views
```

If I run that file, I get:
```
madnessred@Anthony-PC:~$ python ./Python/FM/folder.py
Traceback (most recent call last):
  File "./Python/FM/folder.py", line 24, in <module>
    folder_views[view.split('.')[0]] = __import__(view.split('.')[0], globals(), locals(), ['view'])
ImportError: No module named icons

```


Whereas, if I do, exactly the same thing in the ide.

```
madnessred@Anthony-PC:~$ python
Python 2.6.5 (r265:79063, Mar 20 2010, 14:41:07) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> cwd = os.getcwd()
>>> newcwd = '/home/madnessred/Python/FM/folder_views'
>>> os.chdir(newcwd)
>>> folder_views = {}
>>> for view in os.listdir(os.getcwd()):
...     if view.split('.')[1] == 'py' and len(view.split('.')) == 2:
...             folder_views[view.split('.')[0]] = __import__(view.split('.')[0], globals(), locals(), ['view'])
... 
>>> os.chdir(cwd)
>>> print folder_views
{'icons': <module 'icons' from 'icons.pyc'>}
>>> 

```

It works fine in the ide, (the terminal one), but when i try and run the .py file it comes up with that error.
I have tried renaming the modules, I have checked os.getcwd() where it is importing and that is right.

Could someone please show me where I have gone wrong, or suggest a better way of doing it.

MadnessRed

---

### Post by DaithiF on 2010-07-07
Hi, when running non-interactively, python will look for modules in the directory where the script itself is located, not the current working directory.  you could add newcwd to sys.path to achieve what you want, e.g.:

import sys
if newcwd not in sys.path:
    sys.path.append(newcwd)

---

### Post by MadnessRed on 2010-07-07
> **DaithiF said:**
> Hi, when running non-interactively, python will look for modules in the directory where the script itself is located, not the current working directory.  you could add newcwd to sys.path to achieve what you want, e.g.:

import sys
if newcwd not in sys.path:
    sys.path.append(newcwd)

Perfect, that works :)
```
#Basic
import os, sys

#Look in
newcwd = os.path.join(os.path.split(repr(__file__))[0][1:], 'folder_views')
if newcwd not in sys.path:
	sys.path.append(newcwd)

#Dictionary to hold folderviews
folder_views = {}

#For each file
for view in os.listdir(newcwd):

	#Is it as expected
	if view.split('.')[1] == 'py' and len(view.split('.')) == 2:

		#Import it
		folder_views[view.split('.')[0]] = __import__(view.split('.')[0])
		#folder_views[view.split('.')[0]] = __import__(view.split('.')[0], globals(), locals(), ['view'])

#Output
def test(a=1,b=1,c=1,d=1,e=1):
	print 'h'
print folder_views['icons'].view('/',test)
```

Many thanks, it imports fine now.

---

