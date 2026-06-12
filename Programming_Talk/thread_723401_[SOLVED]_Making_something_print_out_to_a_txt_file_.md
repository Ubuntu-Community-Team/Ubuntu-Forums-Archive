---
title: "[SOLVED] Making something print out to a txt file using python"
date: 2008-03-13
forum: Programming Talk
---

### Post by blithen on 2008-03-13
I know it's like..
sys.stdout
But that's all I know.
I have a python for dummies book but it just describes very briefly what stdout DOES not how to USE it.
Can anyone help me out?

---

### Post by days_of_ruin on 2008-03-13
dont know but this probably should have been posted in the programming board.
I think "a byte of python" says something about that.
[http://www.swaroopch.com/byteofpython/](http://www.swaroopch.com/byteofpython/)

---

### Post by blithen on 2008-03-13
I was thinking about posting it in the programming board but isn't that mostly for programming to help the new release of Ubuntu?

---

### Post by bapoumba on 2008-03-13
Moved to "Programming Talk".

---

### Post by pmasiar on 2008-03-13
process a file line by line:

[PHP]for line in file('file.name'):
   parts = line.split('delim')
   # process parts[/PHP]

is a start :-)

---

### Post by WW on 2008-03-13
blithen, I don't understand your question.  Could you say a little more about what you are trying to do?

---

### Post by Martin Witte on 2008-03-13
if your file is a text file you could print it with 

[PHP]import sys
for line in file('.profile'):
    sys.stdout.write(line)
 
[/PHP]

if you use 

[PHP]for line in file('.profile'):
    print line
[/PHP]

you get interlining, as print adds a newline after each  argument

---

### Post by dwblas on 2008-03-13
> Making something print out to a txt file using pythonIf you mean that you want to put something into a text file see the following.  You want to look for "file write" not sys.stdout which sends the string to stdout=terminal usually.```
fp=open("test.txt", "w")     ## "w" means write to a new file / overwrite if file exists
fp.write("test line #1\n")
fp.write("test line #2\n")
fp.close()

## add to an existing file
fp=open("test.txt", "a")     ## "a" means append/add to an existing file
fp.write("test line #3\n")
fp.write("test line #4\n")
fp.close()
```

---

### Post by blithen on 2008-03-13
> **dwblas said:**
> If you mean that you want to put something into a text file see the following.  You want to look for "file write" not sys.stdout which sends the string to stdout=terminal usually.```
fp=open("test.txt", "w")     ## "w" means write to a new file / overwrite if file exists
fp.write("test line #1\n")
fp.write("test line #2\n")
fp.close()

## add to an existing file
fp=open("test.txt", "a")     ## "a" means append/add to an existing file
fp.write("test line #3\n")
fp.write("test line #4\n")
fp.close()
```
Thank you!
It even has a page about this in my Python for Dummies book.:guitar:

---

