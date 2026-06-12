---
title: "read multiple files in Python omitting certain characters from the filenames"
date: 2012-08-30
forum: Programming Talk
---

### Post by flucoe on 2012-08-30
Hi,

I have a folder with hundreds of text files with filenames of the form hhmmSkz.txt were hh and mm correspond to the hour and minute in which the file was generated and S is the string part of the name that has elements k and z that change from file to file.

I need to put together all the files that correspond to the same hour. In a previous part of this work I was generating these files once per hour so I have the code to open files with different S. However, now I need to open the files with the same component hh, no matter what mm is, and I really have no idea how to do it. 

In the previous part S had some numerical elements so I was doing the following

for k in range(1,16):
       for z in range(1,7):
		for line in open('R/S'+str(k)+'-'+str(z)+'.txt','r'):

If I'm interested in something such as hh being 05 I would like to have something such as the code above but that doesn't consider the mm part of the filename.

Any ideas? Thanks!

---

### Post by lykwydchykyn on 2012-08-30
Can you just use [glob](http://docs.python.org/library/glob.html)?

---

### Post by flucoe on 2012-08-30
Sorry, I'm not sure how I would use it taking into account the for structure.

---

### Post by Erdaron on 2012-08-30
Seems like a good application for regular expressions.

Without using regex, you could do something like this:

```
hh = '01' #set the hour, as string
flist = os.listdir(os.getcwd()) #get the list of files
for f in flist:
    if f[:2] == hh:
        #open the file, do stuff
```

You could also use string formatting to convert an integer into the two-digit string with the leading zero: '%02d' % (x), where x is an int. This may make it easier to iterate over hour values.

---

### Post by juancarlospaco on 2012-08-30
```


import os

for indx, fle in enumerate([ unicode(f) for f in os.listdir(os.getcwd()) if os.path.isfile(f) and unicode(f).lower().startswith('r') and unicode(f).lower().endswith('.txt') and f[:2] == '05' ]):
     line = open(fle, 'r').read()
     print(line)  # debug


```

List Comprehension method  :)



Explained step by step:

```
for indx, fle in enumerate( ... )
```

for index, file in enumerate of the inner list


```
[ unicode(f) ... ]
```

A list containing the string of f variable

```
 for f in os.listdir(os.getcwd()) 
```

for f in the listing of the current directory

```
 
if os.path.isfile(f) and unicode(f).lower().startswith('r') and unicode(f).lower().endswith('.txt') and f[:2] == '05'

```

But only if is a file, 
leaving out directories with same name as files to prevent errors,
and if f on lower cased starts with 'r' to prevent errors,
and if f on lower cased ends with '.txt' to prevent errors,
and f has '05' on the string as you requested to prevent errors,
if that all conditionals are passed ok add it to f list.


```
line = open(fle, 'r').read()
```

read the file, its done. Its also safe.

---

