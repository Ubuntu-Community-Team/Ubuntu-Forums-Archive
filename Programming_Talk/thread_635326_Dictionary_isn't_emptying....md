---
title: "Dictionary isn't emptying..."
date: 2007-12-08
forum: Programming Talk
---

### Post by mikeserv on 2007-12-08
I've been reading a few Python books for the past week or so and I'm trying to gain some simple programming skills.  I've written a program that will recursively scan through a folder and remember all of the files inside of it.

I think I will eventually use the script to sync my Rockbox iPod, but for now it's just an excercise.

Here's the code:
```
#!/usr/bin/python
#Filename : Beginnings.py

modules = {}
import sys
import os
import time
import cPickle as p

def mp3_dict(path, mp3_list = {}):
    """Scans a path for all .mp3 files.  Returns dictionary 'path:file;file;file"""
    folder = []	#defines folder as list
    for item in os.listdir(path):  #scans path for all files and folders
        if item[0] == ".":	#ignores hidden files
            pass
        elif os.path.isfile(path + item) and item[-3:] == "mp3": #checks if item is mp3 file
            try:	#checks if mp3 is first in folder and adds to value list
                mp3_list[path] = mp3_list[path] + ";" + item
            except:
                mp3_list[path] = item
        elif os.path.isdir(path + item + "/"): #checks if item is folder, and adds it to sub
            folder.append(path + item + "/") #folder list
    [mp3_dict(item, mp3_list) for item in folder] #recursively scans subfolder list
    return mp3_list
    
def dat_write(dat_path, f_name):  
	"""Pickles return of mp3_dict for dat_path to file f_name"""	
	f = open(dat_path + f_name, 'w')
	p.dump(mp3_dict(dat_path), f)
	f.close()

def dat_read(path):
    """Unpickles and returns path."""
    f = file(path)
    dat = p.load(f)
    f.close()
    return dat
 	
def dat_print(mp3l, path):
    """Parses out dictionary in format path:file;file;file 
    and prints readable output."""
    print path + ":\n" #prints original search path
    for row in mp3l:
        print row[len(path):] + ": ", #prints subfolder name
        for item in mp3l[row].split(";"): #splits dictionary values into filenames
            if item == mp3l[row].split(";")[-1]: #checks if file is last in folder
                print "%s\n" %(item) #prints last file and starts new line
            else:
                print "%s, " %(item), #prints files in subfolder in comma sep list

ipath = '/media/ipod/PodCasts/'
hpath = '/home/mhodgin/PodCasts/'
sfile = 'mp3_list.dat'

dat_print(mp3_dict(ipath), ipath)
dat_print(mp3_dict(hpath), hpath)

#dat_write(hpath, sfile)
#dat_write(ipath, sfile)
#dat_print(dat_read(hpath + sfile), hpath)
#dat_print(dat_read(ipath + sfile), ipath)

```

The problem I'm having is this: the first (and main) function mp3_dict() scans some folders and saves its files to the dictionary fine, but for some reason it doesn't clear the dictionary afterwards.  So when I run it the second time, it returns a compounded list, and this is frustrating.  Why isn't the variable clearing?

-Mike

---

### Post by pmasiar on 2007-12-08
Without even trying, you invented advanced trick by declaring mp3_list as static variable. Why you need to pass it in? Instead, don't try to be clever, declare it as local variable inside function (and not as default parameter). And read about how you can update dictionary with another dictionary.

Consider also more flexible data structures, like dict which values are lists (instead of string with ';' as separator).

Nitpicking about naming: 
- variable mp3_list is a dictionary. WTF? 
- functions are more natural with verb-based name: make_mp3s (returns list or dict of something)

---

### Post by mikeserv on 2007-12-08
Ok, I've taken your advice about the naming and making the dictionary values a list, but that doesn't fix my original problem.  How did I declare the variable static?  Why doesn't it clear when the function is called without the mp3_dict argument?  Without that argument, shouldn't the variable be equal to {}?

```
#!/usr/bin/python
#Filename : Beginnings.py

modules = {}
import sys
import os
import time
import cPickle as p

def make_mp3_dict(path, mp3_dict = {}):
    """Scans a path for all .mp3 files.  Returns dictionary 'path:file;file;file"""
    folder = []	#defines folder as list
    flist = []
    for item in os.listdir(path):  #scans path for all files and folders
        if item[0] == ".":	#ignores hidden files
            pass
        elif os.path.isfile(path + item) and item[-3:] == "mp3": #checks if item is mp3 file
            flist.append(item)
        elif os.path.isdir(path + item + "/"): #checks if item is folder, and adds it to sub
            folder.append(path + item + "/") #folder list
    if flist != []:
        mp3_dict[path] = flist
    [make_mp3_dict(item, mp3_dict) for item in folder] #recursively scans subfolder list
    return mp3_dict
    
def dat_write(dat_path, f_name):  
	"""Pickles return of mp3_dict for dat_path to file f_name"""	
	f = open(dat_path + f_name, 'w')
	p.dump(make_mp3_dict(dat_path), f)
	f.close()

def dat_read(path):
    """Unpickles and returns path."""
    f = file(path)
    dat = p.load(f)
    f.close()
    return dat
 	
def dat_print(mp3l, path):
    """Parses out dictionary in format path:file;file;file 
    and prints readable output."""
    print path + ":\n" #prints original search path
    for row in mp3l:
        print row[len(path):] + ": ", #prints subfolder name
        for item in mp3l[row]: #splits dictionary values into filenames
            if item == mp3l[row][-1]: #checks if file is last in folder
                print "%s\n" %(item) #prints last file and starts new line
            else:
                print "%s, " %(item), #prints files in subfolder in comma sep list

ipath = '/media/ipod/PodCasts/'
hpath = '/home/mhodgin/PodCasts/'
sfile = 'mp3_dict.dat'

dat_print(make_mp3_dict(ipath), ipath)
dat_print(make_mp3_dict(hpath), hpath)

#dat_write(hpath, sfile)
#dat_write(ipath, sfile)
#dat_print(dat_read(hpath + sfile), hpath)
#dat_print(dat_read(ipath + sfile), ipath)

```

-Mike

---

### Post by mikeserv on 2007-12-08
A guy at python-forum.org took a look at the code and gave me this link: [http://www.python.org/doc/faq/general/#why-are-default-values-shared-between-objects]("http://www.python.org/doc/faq/general/#why-are-default-values-shared-between-objects")

My code now looks like this (and it works correctly):
```

#!/usr/bin/python
#Filename : Beginnings.py

modules = {}
import sys
import os
import time
import cPickle as p

def make_mp3_dict(path, mp3_dict = None):
    """Scans a path for all .mp3 files.  Returns dictionary 'path:filelist"""
    folder = []	#defines folder as list
    flist = []
    if mp3_dict == None:
        mp3_dict = {}
    for item in os.listdir(path):  #scans path for all files and folders
        if item[0] == ".":	#ignores hidden files
            pass
        elif os.path.isfile(path + item) and item[-3:] == "mp3": #checks if item is mp3 file
            flist.append(item)#adds file to filelist
        elif os.path.isdir(path + item + "/"): #checks if item is folder, and adds it to sub
            folder.append(path + item + "/") #folder list
    if flist != []:#only adds folders containing .mp3's to mp3_dict
        mp3_dict[path] = flist  
    [make_mp3_dict(item, mp3_dict) for item in folder] #recursively scans subfolder list
    return mp3_dict
    
    
def dat_write(dat_path, f_name):  
	"""Pickles return of mp3_dict for dat_path to file f_name"""	
	f = open(dat_path + f_name, 'w')
	p.dump(make_mp3_dict(dat_path), f)
	f.close()

def dat_read(path):
    """Unpickles and returns path."""
    f = file(path)
    dat = p.load(f)
    f.close()
    return dat
 	
def dat_print(mp3l, path):
    """Parses out dictionary in format path:filelist 
    and prints readable output."""
    print path + ":\n" #prints original search path
    for row in mp3l:
        print row[len(path):] + ": ", #prints subfolder name
        for item in mp3l[row]: #splits dictionary value lists
            if item == mp3l[row][-1]: #checks if file is last in folder
                print "%s\n" %(item) #prints last file and starts new line
            else:
                print "%s, " %(item), #prints files in subfolder in comma sep list

ipath = '/media/ipod/PodCasts/'
hpath = '/home/mhodgin/PodCasts/'
sfile = 'mp3_dict.dat'

dat_write(hpath, sfile)
dat_write(ipath, sfile)
dat_print(dat_read(hpath + sfile), hpath)
dat_print(dat_read(ipath + sfile), ipath)

```

-Mike

---

