---
title: "read dir contents and print them"
date: 2007-05-19
forum: Programming Talk
---

### Post by nix4me on 2007-05-19
I'm trying to find a way to make a script that reads the contents of a system dir and prints the contents.

Secondly I would like it to only list the contents of new dirs based on a set dir creation date.  Such as, if i want to see all dirs in a path that have been created in the last 5 days.

It looks like I might be able to use the dircache.listdir() function but i'm not having any luck.

nix4me

---

### Post by ghostdog74 on 2007-05-19
> **nix4me said:**
> I'm trying to find a way to make a script that reads the contents of a system dir and prints the contents.

you are using Python i assume? and have you started to code yet?
some of the methods you can use from the os module is listdir, walk() or even glob for wildcard pattern matching...  pls have a look at the docs

> 
Secondly I would like it to only list the contents of new dirs based on a set dir creation date.  Such as, if i want to see all dirs in a path that have been created in the last 5 days.

you can make use of getctime/getatime/getmtime from os.path module .  also related is the time module, stat() from os module .( pls see the docs for more details ) 


> 
It looks like I might be able to use the dircache.listdir() function but i'm not having any luck.

you had errors?

---

### Post by nix4me on 2007-05-19
Well, this is a start:

>>> import dircache
>>> a=dircache.listdir('/mnt/fileserver/uploads')
>>> a=a[:]
>>> a

This prints all of the directories in one long line.  I would like to break this into 1 dir per line.

Then I will reasearch how to only get certain dirs based on date.

I am using python and I am mostly new to programming, however I have been able to hack things together pretty quickly.  Python is very nice, easy to learn.

Any help would be greatly appreciated.

nix4me

---

### Post by seamless on 2007-05-19
```
>>> a=a[:]
```
That is not needed. You already have a and don't need to put the contents of it back into it.

```
>>> a
```
a is an array of all the directories. Above you are just dumping this list. To print it on one line you need to loop though the array and print each item in it. Here is an example of how to do this:
```
#!/usr/bin/env python

import dircache
a=dircache.listdir('/mnt/fileserver/uploads')
for s in a:
        print s
```

---

### Post by nix4me on 2007-05-19
Excellent, that works nicely.

Now off to figure out how to shorten the list based on file dates.

nix4me

---

### Post by slavik on 2007-05-20
umm, if I was using perl, I'd get output of ls -la and then parse the output ...

example:
@dirs = `ls -la /some/dir/`; #array of lines
for(@dirs) { # for each line of output
  @fields = split /\s/, $_; #split the line on spaces
  #there are function to convert time and such, and you need only 1 field in the @fields array
}

the pseudo code is there, just finish it :)

---

### Post by ghostdog74 on 2007-05-20
> **slavik said:**
> umm, if I was using perl, I'd get output of ls -la and then parse the output ...

example:
@dirs = `ls -la /some/dir/`; #array of lines
for(@dirs) { # for each line of output
  @fields = split /\s/, $_; #split the line on spaces
  #there are function to convert time and such, and you need only 1 field in the @fields array
}

the pseudo code is there, just finish it :)

IMO, that's not a "portable" way to code as you are shelling out from perl to call an OS specific command. there is a readdir you can use.

---

### Post by nix4me on 2007-05-20
Well i appreciate the perl response, but i am trying to do it in python.  So far, i have not figured out a way to sort/split based on the file dates.

nix4me

---

### Post by ghostdog74 on 2007-05-20
> **nix4me said:**
> .. sort/split based on the file dates.
what actually are you trying to do? the file dates you mentioned, do you want to find last modified date? creation date? or accessed date? pls check out the os module i mentioned. you should be able to get the timestamp of the files in seconds. then you can store them in lists and use the sorted() method or sort() to sort the list...
```

print sorted([ (os.path.getmtime(files),files) for files in os.listdir(os.getcwd()) ])

```

---

### Post by slavik on 2007-05-20
> **ghostdog74 said:**
> IMO, that's not a "portable" way to code as you are shelling out from perl to call an OS specific command. there is a readdir you can use.

platform independent was not in OP :P

---

### Post by nix4me on 2007-05-20
> **ghostdog74 said:**
> what actually are you trying to do? the file dates you mentioned, do you want to find last modified date? creation date? or accessed date? pls check out the os module i mentioned. you should be able to get the timestamp of the files in seconds. then you can store them in lists and use the sorted() method or sort() to sort the list...
```

print sorted([ (os.path.getmtime(files),files) for files in os.listdir(os.getcwd()) ])

```

Im trying to get the script to get the dir listing, evaluate all of the folders in that dir and print only the dirs that are 1 week old or less, 1 per line.

So far, here is the code I am working with:

```
#!/usr/bin/env python

import dircache
a=dircache.listdir('/mnt/fileserver/uploads')
for s in a:
        print s
```

nix4me

---

### Post by slavik on 2007-05-20
in C (sorry, it's the only way I know how to do it), there is opendir() which opens the directory file and reads the entries, then there is stat() which actually reads the information about a file. you need the equivalent of stat :)

---

### Post by ghostdog74 on 2007-05-20
> **nix4me said:**
> Im trying to get the script to get the dir listing, evaluate all of the folders in that dir and print only the dirs that are 1 week old or less, 1 per line.


i have showed you a snippet of how it can be done. 
use os.path.getmtime (or ctime, or atime depending on your requirements).
eg 
```

>>> import time,os
>>> today=time.time()
>>> filetime = os.path.getmtime("file")
1179703606

```
you get seconds. 1 week is roughly equivalent to 24 * 60 * 60 * 7 =  
604800 seconds, so you subtract today's time with 604800 and that is the time 
one week ago.Store it in a variable then in your script you can check whether filetime is less than one week and
print it.

---

### Post by slash2314 on 2007-05-20
```

import os
import time
for file in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
	print file

```

---

### Post by nix4me on 2007-05-21
Perfect.  Thanks so much, i was having trouble getting the date.date portion working.  It's working great.  I've managed to tweak it accordingly to work with the individual directories that i want.

Thanks again,
nix4me

---

