---
title: "Help python search"
date: 2009-08-07
forum: Programming Talk
---

### Post by avandy9 on 2009-08-07
i'm trying to  find a text file on my compter what I have now works but it will not find files I know are in the Project_files forder it just prints file not found 
 
```
from os.path import exists, join, abspath
from os import pathsep
from string import split
def search_file(filename, search_path):
    """Given a search path, find file
    """
    file_found = 0
    paths = split(search_path, pathsep)
    for path in paths:
        if exists(join(path, filename)):
            file_found = 1
            break
        if file_found:
            return abspath(join(path, filename))
        else:
            return None
x=1
if x == 1:
    path_1 = 'C:/Project_Files' 
    find_file = search_file('a' ,path_1)
    if find_file:
        print "file found at %s" % find_file
    else:
        print "file not found"
        

```

---

### Post by Can+~ on 2009-08-07
You should take a look at [FONT="Courier New"]os.walk[/FONT]

[PHP]#!/usr/bin/env python

import os

def search_file(searchfolder, searchfilename):
	
	for root, dirs, files in os.walk(searchfolder):
		
		if searchfilename in files:
			print "File found: %s" % root
			break[/PHP]

---

### Post by avandy9 on 2009-08-07
could you give me a link?

---

### Post by Can+~ on 2009-08-07
> **avandy9 said:**
> could you give me a link?

Python doc pages are running slow lately, but do

[PHP]>>> import os
>>> help(os.walk)[/PHP]

in the interactive python shell.

---

