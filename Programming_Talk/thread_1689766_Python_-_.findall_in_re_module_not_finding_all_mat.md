---
title: "Python - .findall in re module not finding all matches"
date: 2011-02-17
forum: Programming Talk
---

### Post by Nico-dk on 2011-02-17
On day 5 of teaching myself python, so far so good, but please keep my newbieness in mind when replying ;)

I'm currently mocking about in re module, trying to return all lines in a textfile containing my pattern.

```
#!/usr/bin/env python

import re

def search():
    myfile = "test"
    rfile = open(myfile, "r")
    regex = re.compile('abc')
    linecount = 0

    for line in myfile:
        linecount = linecount +1
        output = rfile.readline()
        mat = regex.findall(output)

        if mat == ['abc']:
            print "match found in line " + str(linecount), mat
            print output

    rfile.close
   
search()
```

So far so good. I'm sure there are more effective ways to do this, but so far this works ... well sort.

I've created a file: test that contains my search pattern in lines 1, 4, 6 and 9. Problem is the output from the script is as follows:

```
match found in line 1 ['abc']
abc defghijk

match found in line 4 ['abc']
abababab abc
```

I did add a print linecount right before the first if statement. This count never goes above 4

**Why aren't line 6 and 9 found as matches?**
I'm sure it must be something, I'm doing wrong, but i can't for the life of me figure out what.

Any help greatly appreciated :)

---

### Post by Nico-dk on 2011-02-17
Just realized something

```
myfile = "test"

for line in myfile:
```
It looks like the script only reads the first 4 lines of the file 'test' because that's the length of the filename.

Something for me to pursue

---

### Post by Nico-dk on 2011-02-17
Triple post, sorry about that, but I figured it out, and thought someone else might eventually like know the solution.

Turns out I was right about the 'test' argument in the for loop. So after a little research, I found a way to count all the lines in the file before iterating over them.

Feedback on this solution would still be appreciated, since I'm sure the script below is full of newbie mistakes (missing doc string for one)

Final script 

```
#!/usr/bin/env python
import re

def search():
    myfile = "test"
    regex = re.compile('abc')
    
    rfile = open(myfile, "r")
    linecount = len(open(myfile, "r").readlines()) +1
    print "lines in file: ", linecount

    lncounter = 0

    for line in range(linecount):
        lncounter = lncounter +1
        output = rfile.readline()
        mat = regex.findall(output)

        if mat == ['abc']:
            print "match found in line " + str(lncounter), mat
            print output

    rfile.close
   
search()
```

---

### Post by Arndt on 2011-02-17
> **Nico-dk said:**
> Triple post, sorry about that, but I figured it out, and thought someone else might eventually like know the solution.

Turns out I was right about the 'test' argument in the for loop. So after a little research, I found a way to count all the lines in the file before iterating over them.

Feedback on this solution would still be appreciated, since I'm sure the script below is full of newbie mistakes (missing doc string for one)



How about this:

```
#!/usr/bin/env python

import re

def search():
    myfile = "test"
    rfile = open(myfile, "r")
    regex = re.compile('abc')
    linecount = 0

    for line in rfile:
        linecount = linecount +1
        mat = regex.findall(line)

        if mat == ['abc']:
            print "match found in line " + str(linecount), mat
            print line

    rfile.close
   
search()

```

---

### Post by wmcbrine on 2011-02-17
"close" is a method:

```
rfile.close()
```

---

### Post by Nico-dk on 2011-02-17
Aaah, I see how you condensed it.
I knew there was room for imporvement, ut I vcould'nt quite figure out what variables to reuse. Reusing rfile and line was the key.

Thanks,

---

