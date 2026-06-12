---
title: "Python Script For Batch Renaming"
date: 2009-11-21
forum: Programming Talk
---

### Post by HalfEmptyHero on 2009-11-21
I'm trying to write a python script for renaming all of my movie files. What I want to use two text files, one with the names of the filenames of the movies and one with what I want the new name to be, that way I can rename them how I want. I want it to take each line from list_one and rename it to the corresponding line in list_two. Here's what I have so far.

```

#!/usr/bin/env python

import os

list_one = open('list_one.txt', 'r');
list_two = open('list_two.txt', 'r');

for line in list_one.readlines():
    new_name = list_two.readlines();
    if os.system('mv ' , line , ' ' + new_name) == 0:
        print line + ' has been rename to ' + new_name;
    else:
        print 'error'
list_one.close()
list_two.close()

```
The error I get is 'cannot concatenate 'str' and 'list' objects.' A google search reveal many ways to convert lists into single strings, which would print out all of my movies at once, but I could not find how to do what I need to do.

After that didn't work, I tried this
```
#!/usr/bin/env python

import os

list_one = open('list_one.txt', 'r');
list_two = open('list_two.txt', 'r');

for line in list_one.readlines():
    new_name = list_two.readlines();
    if os.rename( line , new_name) == 0:
        print line + ' has been rename to ' + new_name;
    else:
        print 'error'
list_one.close()
list_two.close()
```
Here I got the error 'TypeError: coercing to Unicode: need string or buffer, list found
TypeError:: command not found.' From what I read, os.rename() might not be what I want anyways, because if there is an object with the same name (where there might be in my case) it will be removed silently.

Any suggestions?

---

### Post by Can+~ on 2009-11-21
First of all, why you complicate yourself with two files? Why not just:

```
"old name", "new name"
```

Second, "something.readlines()" loads the whole content of the file to memory, therefore, you get that error, what you want to do is

[PHP]for (oldname,newname) in zip(oldfile, newfile):
    ...
    [/PHP]

So you can iterate in both files at the same time, and without having to load everything to memory, just buffering.

---

### Post by Aayu on 2009-11-21
Haven't the foggiest on how to do this in Python.  But in Perl sudo:

```
#!/usr/bin/perl
use warnings;
use strict;
open (MYFILE, 'whatever.text');
while (<MYFILE>) {
chomp;
print "$_\n";
}
close (MYFILE);
Your stuff would
Go
Here
open (MYFILE, 'data.txt');
while (<MYFILE>) {
chomp;
print "$_\n";
close (MYFILE);

```

I think this should be correct..  though, you probably Don't know perl if your working with Python ;)

---

### Post by HalfEmptyHero on 2009-11-21
> **Can+~ said:**
> First of all, why you complicate yourself with two files? Why not just:

```
"old name", "new name"
```Second, "something.readlines()" loads the whole content of the file to memory, therefore, you get that error, what you want to do is

[php]for (oldname,newname) in zip(oldfile, newfile):
    ...
    [/php]So you can iterate in both files at the same time, and without having to load everything to memory, just buffering.

Yeah, I figured out about the readlines() problem, now I have been trying it with readline() instead, and have been having other problems. 

The reason I am using 2 files is because I have a directory with 300+ movies in it, and it is a lot easier for me to list the contents of the directory into a text file and then change the names into something I want since  the movies have no naming convention at all. But I am up for any suggestions, if you have an easier way to do it. 

Sorry for my ignorance, but what does zip() do?

And no, I don't know anything about perl.

---

### Post by HalfEmptyHero on 2009-11-21
I have been trying this:

```
list_one = list_one_f.readline()
list_two = list_two_f.readline()
while True:
    if list_one = '':
        break;
    elif os.system('mv ' + list_one + list_two) == 0:
        print list_one + 'renamed to ' + list_two
        list_one = list_one_f.readline()
        list_two = list_two_f.readline()
    else:
        print 'error...'
        break
```And it is looking like it might work. The only problem is that 'mv ' + list_one + list_two is looking like this

```
python renamer.py 
mv file_one.txt
 file_1.txt

Done.

```So the mv command is not working. Any way to remove the new line that seems to be tacked onto it?

---

### Post by days_of_ruin on 2009-11-21
> **HalfEmptyHero said:**
> I have been trying this:

```
list_one = list_one_f.readline()
list_one.strip()
list_two = list_two_f.readline()
list_two.strip()
while True:
    if list_one = '':
        break;
    elif os.system('mv ' + list_one +" "+ list_two) == 0:
        print list_one + 'renamed to ' + list_two
        list_one = list_one_f.readline()
        list_two = list_two_f.readline()
    else:
        print 'error...'
        break
```And it is looking like it might work. The only problem is that 'mv ' + list_one + list_two is looking like this

```
python renamer.py 
mv file_one.txt
 file_1.txt

Done.

```So the mv command is not working. Any way to remove the new line that seems to be tacked onto it?

Fix'd

---

### Post by HalfEmptyHero on 2009-11-21
Excellent, that is exactly what I needed. As of right now, the script works. The only problem is, after it is done renaming the files it doesn't end, i'm not sure if it is doing anything or not (it isn't renaming files though).

```

#!/usr/bin/env python

import os

list_one_f = open('list_one.txt', 'r');
list_two_f = open('list_two.txt', 'r');

list_one = list_one_f.readline()
list_one = list_one.strip()
list_two = list_two_f.readline()
list_two = list_two.strip()

while True:
    if list_one == list_two:
        list_one = list_one_f.readline()
        list_one = list_one.strip()
        list_two = list_two_f.readline()
        list_two = list_two.strip()
    elif os.rename( list_one , list_two) == 0:
        print list_one + ' renamed to ' + list_two
        list_one = list_one_f.readline()
        list_one = list_one.strip()
        list_two = list_two_f.readline()
        list_two = list_two.strip()
    else:
        print 'error...'
        break

print 'Done.'
list_one_f.close()
list_two_f.close()

```Any way to make it know when to stop, like when it gets to the end of the file?

Edit: As I thought, the script keeps comparing the lines on list_one to list_two.

---

### Post by Can+~ on 2009-11-21
Instead of calling mv directly, use "[FONT="Courier New"]os.rename[/FONT]"

> Sorry for my ignorance, but what does zip() do?

It joins iterable elements into a main iterable of tuples.

[PHP]>>> a = [1, 2, 3, 4]
>>> b = "abcd"
>>> zip(a, b)
[(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]
[/PHP]

In fact, you can make a dictionary from this:

[PHP]>>> dict(zip(a, b))
{1: 'a', 2: 'b', 3: 'c', 4: 'd'}[/PHP]

---

### Post by ib.lundgren on 2009-11-21
Problem is that you are trying to iterate through one line at a time for infinity (while True) and not stopping it anywhere. When readline() finds the end of the file an empty string is returned (""), you could use that to check whether or not you have reached the end. Then break out of the while loop if a "" is found.

Consider this quickly baked code snippet for an alternative way to make your batch renamer using the zip method mentioned by Can+~ before.

If you call the script from command line like this. Assuming it is saved as "renamer" (without .py) and made executable in your current working dir.

[PHP]$ ./renamer old_filenames.txt new_filenames.txt[/PHP]

[PHP]#!/usr/bin/env python
import os, sys

if __name__ == "__main__":
	
   if not os.path.exists(sys.argv[1]) or not os.path.exists(sys.argv[2]):
       print "Invalid file arguments given."
       print "Usage: renamer old_file_list new_file_list."
       sys.exit(1)
	
   old_names = open(sys.argv[1], "r").readlines()
   new_names = open(sys.argv[2], "r").readlines()
	
   for (oldname, newname) in zip(old_names, new_names):		
      real_oldname = os.path.abspath(oldname.strip())
      real_newname = os.path.abspath(newname.strip())  
      os.rename(real_oldname, real_newname)[/PHP]

---

### Post by HalfEmptyHero on 2009-11-22
Excellent, thanks for all the help.

---

