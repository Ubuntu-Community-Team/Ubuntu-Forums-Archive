---
title: "Merge Path and File Together for os.remove() in Python?"
date: 2009-05-03
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-03
Yo, so I used os.walk() to walk through my code and find the files I needed to delete. I wanted it to first search through for all the files and then list them and ask for deletion. I have done everything but the deletion part which I think is a bit tricky. 

I made a list that holds instances of a class that has a value for path and another value for the filename. When removing I need to specify the path as well as the file, but when I specify 2 arguments in os.remove() the interpreter complains that os.remove only takes one argument, so how would I go about deleting these files?

Here is the relevant code:
```

#!/usr/bin/python

import os, tarfile

pathfileList = []

class pathAndFile(object):
	path = None
	fname = None
	def __init__(self, p, f):
		self.path = p
		self.fname = f

def del_nfo_sfv_txt_m3u_files():
#	global pathfileList
#	pathfileList = []
	for r,d,f in os.walk("."):
		i = 0
		for filename in f:
			splitup = os.path.splitext(filename)
			if splitup[1] == ".nfo" or splitup[1] == ".sfv" \
			or splitup[1] == ".txt" or splitup[1] == ".m3u":
				#pathfileList = []
				pathfileList.append(pathAndFile(r,filename))
	print len(pathfileList)
	stop = len(pathfileList)
	for i in range(stop):
		print pathfileList[i].path, pathfileList[i].fname
	yn = raw_input("Delete all?(Y/N)")
	if yn == 'Y' or yn == 'y':
		for i in range(len(pathfileList)):
			os.remove(pathfileList[i].path,pathfileList[i].fname)
			print "Removed",pathfileList[i].path,pathfileList[i].fname
		#os.remove(filename)
		print "Files removed."


```

This is what I get:
```

----------------MENU-----------------
3.Printer
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
7
. megaZORD.sfv
. meta.txt
. bombackaz.nfo
./chaat test.nfo
./chaat mastaz.m3u
./chaat killz.m3u
./chaat/chutney brazton.m3u
Delete all?(Y/N)y
Traceback (most recent call last):
  File "cleaner5-3-09_1.py", line 116, in <module>
    del_nfo_sfv_txt_m3u_files()
  File "cleaner5-3-09_1.py", line 32, in del_nfo_sfv_txt_m3u_files
    os.remove(pathfileList[i].path,pathfileList[i].fname)
TypeError: remove() takes exactly 1 argument (2 given)

```
Thanks!

---

### Post by Martin Witte on 2009-05-03
[os.remove]("http://docs.python.org/library/os.html#files-and-directories") takes one parameter, take a look at [os.path.join]("http://docs.python.org/library/os.path.html") on how to join directorynames and filenames

---

### Post by StunnerAlpha on 2009-05-03
> **Martin Witte said:**
> [os.remove]("http://docs.python.org/library/os.html#files-and-directories") takes one parameter, take a look at [os.path.join]("http://docs.python.org/library/os.path.html") on how to join directorynames and filenames
Awesome! Os.path.join was just what I needed, thank you very much kind sir.

---

