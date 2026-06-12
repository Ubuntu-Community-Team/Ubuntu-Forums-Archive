---
title: "[SOLVED] [Python] Script Involving Directories"
date: 2008-08-13
forum: Programming Talk
---

### Post by TreeFinger on 2008-08-13
I am trying to right a script that will print last access times of all files in a directory and also sub directories. It works fine for all the files in the current directory, but when going into the sub dirs, for some reason, the program does not go into the if statement if a file is found to be a file.

The program will only print the information about the first dir, nothing in the sub dirs. I am very confused because the program gets the list of files in a subdir but never goes into if statement for these files!

[php]
import os, time, os.path, stat

def last_access(dir):
	directory = dir
	dir_files = os.listdir(directory)
	for file in dir_files:
		if os.path.isdir(file):
			last_access(os.path.abspath(file))
		elif os.path.isfile(file):
			stats = os.stat(file)
			last_time = time.strftime("%m/%d/%Y",time.localtime(stats[stat.ST_ATIME]))
			print file, "\t\t Last Accessed: ", last_time
		else:
			continue

last_access('.')
[/php]

---

### Post by ghostdog74 on 2008-08-13
you don't have to create your own recurse directory routine. Use os.walk().
See the doc for example on how to use it.

---

### Post by TreeFinger on 2008-08-13
> **ghostdog74 said:**
> you don't have to create your own recurse directory routine. Use os.walk().
See the doc for example on how to use it.

Thanks for that tip. Although, I am still curious as to why my function didn't work.

---

### Post by tamoneya on 2008-08-13
> **TreeFinger said:**
> Thanks for that tip. Although, I am still curious as to why my function didn't work.

I think it is because you need the absolute path.

```
if os.path.isdir(os.path.abspath(file)):
```

---

### Post by samjh on 2008-08-13
> **tamoneya said:**
> I think it is because you need the absolute path.

```
if os.path.isdir(os.path.abspath(file)):
```

Nope.  I just substituted your suggestion into his script.  It made no difference.

I'm puzzled about it myself. :confused:

---

### Post by TreeFinger on 2008-08-13
I am having the same problem with os.walk() but it may be due to my code. 

Had code posted but I would like to play with it a little more.

---

### Post by Bachstelze on 2008-08-13
Your problem comes from the fact that the list returned by os.listdir() contains only the names of the files in the directory, so when you have a subdirectory, os.path.isfile() won't find them because those files are not in the current directory.

So the string you pass to os.path.isfile() must also contain the directory name:

```
firas@nobue NALG % cat test.py 
import os, time, stat          

def last_access(dir):
    directory = dir  
    dir_files = os.listdir(directory)
    for file in dir_files:           
        relPath = os.path.join(dir, file)
        if os.path.isdir(relPath):       
            last_access(relPath)         
        elif os.path.isfile(relPath):    
            stats = os.stat(relPath)     
            last_time = time.strftime("%m/%d/%Y",time.localtime(stats[stat.ST_ATIME]))
            print relPath, "\t\t Last Accessed: ", last_time                          
        else:                                                                         
            continue

last_access('.')
firas@nobue NALG % ls -lR .
.:
total 20440
-rw-r--r-- 1 firas firas  1614131 2008-08-12 20:20 03 Great Fairy's Harp Theme.mp4
-rwxr-x--- 1 firas firas  2162159 2008-08-08 20:53 03 Great Fairy's Harp Theme.ogg
-rw-r--r-- 1 firas firas 15484204 2008-08-08 20:59 03 Great Fairy's Harp Theme.wav
-rw-r--r-- 1 firas firas    10196 2008-08-13 00:49 NALG-0.1rc1.tar.bz2
-rw-r--r-- 1 firas firas    10196 2008-08-13 00:49 NALG-0.1rc1.tar.gz
drwxr-xr-x 2 firas firas       51 2008-08-13 02:21 NALG-0.1rc2
-rw-r--r-- 1 firas firas    10409 2008-08-13 02:22 NALG-0.1rc2.tar.gz
lrwxrwxrwx 1 firas firas       53 2008-08-08 23:21 neroAacEnc -> /data/software/nero/NeroDigitalAudio/linux/neroAacEnc
-rw-r--r-- 1 firas firas      605 2008-08-10 04:58 neroAac.log
-rw-r--r-- 1 firas firas  1614131 2008-08-10 04:32 test.mp4
-rw-r--r-- 1 firas firas      518 2008-08-13 17:29 test.py

./NALG-0.1rc2:
total 44
-rwxr-xr-x 1 firas firas 29741 2008-08-13 02:18 NALG.py
-rw-r--r-- 1 firas firas     0 2008-08-13 02:14 neroAac.log
-rwxr-xr-x 1 firas firas 11114 2008-08-13 02:21 README
firas@nobue NALG % python test.py
./03 Great Fairy's Harp Theme.mp4                Last Accessed:  08/10/2008
./NALG-0.1rc1.tar.bz2            Last Accessed:  08/13/2008
./NALG-0.1rc2.tar.gz             Last Accessed:  08/13/2008
./03 Great Fairy's Harp Theme.ogg                Last Accessed:  08/08/2008
./03 Great Fairy's Harp Theme.wav                Last Accessed:  08/08/2008
./test.mp4               Last Accessed:  08/08/2008
./neroAacEnc             Last Accessed:  08/06/2007
./test.py                Last Accessed:  08/13/2008
./neroAac.log            Last Accessed:  08/10/2008
./NALG-0.1rc1.tar.gz             Last Accessed:  08/13/2008
./NALG-0.1rc2/neroAac.log                Last Accessed:  08/13/2008
./NALG-0.1rc2/NALG.py            Last Accessed:  08/13/2008
./NALG-0.1rc2/README             Last Accessed:  08/13/2008

```

Another approach would be to use os.chdir() to change to the subdirectories before dirlist'ing them.

---

### Post by ghostdog74 on 2008-08-13
use print to print debug statements inside you "if" portion. Then you will know whether it reaches your "if" block.

---

