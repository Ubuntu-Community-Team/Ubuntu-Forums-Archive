---
title: "Does this look right? (Python)"
date: 2010-11-17
forum: Programming Talk
---

### Post by sysop on 2010-11-17
Does this code look right? Am I missing something? I'm fairly new to Python but need a quick script to parse matching text patterns line by line in a text based log file. This does not seem to work though? :confused:

```
import os #import os module

f = open('101111.LOG','r') #open log file for reading
line_num = 0 #set line number variable to 0

for line in f: #for each line in file do below
    line_num = line_num + 1 #add 1 count to line_num variable
    if "oins" in line: #look for oins text pattern in line
        print(line) #if found print the line
    else: #otherwise if not found
        print('Line Number: ' + str(line_num)) #print line number

f.close()#close the file
SystemExit #exit script
```

Any suggestions? Thanks in advance.

---

### Post by Arndt on 2010-11-17
> **sysop said:**
> Does this code look right? Am I missing something? I'm fairly new to Python but need a quick script to parse matching text patterns line by line in a text based log file. This does not seem to work though? :confused:

```
import os #import os module

f = open('101111.LOG','r') #open log file for reading
line_num = 0 #set line number variable to 0

for line in f: #for each line in file do below
    line_num = line_num + 1 #add 1 count to line_num variable
    if "oins" in line: #look for oins text pattern in line
        print(line) #if found print the line
    else: #otherwise if not found
        print('Line Number: ' + str(line_num)) #print line number

f.close()#close the file
SystemExit #exit script
```

Any suggestions? Thanks in advance.

I think 'in' is only for list membership (or hash tables, etc.). "oins" will not be a member of 'line' in that sense. Look up the functions that are specific to strings.

---

### Post by robots.jpg on 2010-11-17
I don't see why it wouldn't work ('in' can test for substrings).  Please be more specific when you say it's not working.  Are you sure that lowercase "oins" appears in your file?

---

### Post by Arndt on 2010-11-17
> **robots.jpg said:**
> I don't see why it wouldn't work ('in' can test for substrings).  Please be more specific when you say it's not working.  Are you sure that lowercase "oins" appears in your file?

Sorry for being misleading. I tried the program but made an error in the input, so I drew the wrong conclusion about 'in'. As you say, the OP will have to get back with more information about how it doesn't work.

---

### Post by mo.reina on 2010-11-17
> **sysop said:**
> Does this code look right? Am I missing something? I'm fairly new to Python but need a quick script to parse matching text patterns line by line in a text based log file. This does not seem to work though? :confused:

```
import os #import os module

f = open('101111.LOG','r') #open log file for reading
line_num = 0 #set line number variable to 0

for line in f: #for each line in file do below
    line_num = line_num + 1 #add 1 count to line_num variable
    if "oins" in line: #look for oins text pattern in line
        print(line) #if found print the line
    else: #otherwise if not found
        print('Line Number: ' + str(line_num)) #print line number

f.close()#close the file
SystemExit #exit script
```

Any suggestions? Thanks in advance.

it seems to work, at least on my system.

i would re-write your script like this, to make it a bit shorter, thus easier to maintain in the future:

```
import os

with open('test.txt') as f:
    for index, line in enumerate(f):
        if "oins" in line:
            print(line)
        else:
            print('Line Number:' + str(index + 1))
```

test:
```
mo@mo-F8P:~$ cat test.txt 
oins in my file
not here
oins in the next line

```

running the script:
```
>>> oins in my file

Line Number:2
oins in the next line

>>> 
```

---

### Post by DaithiF on 2010-11-17
and a couple of slight variations on mo.reina's solution:

```
with open('test.txt') as f:
    for index, line in enumerate(f, start=1):
        line = line.rstrip('\r\n')
        if "oins" in line:
            print(line)
        else:
            print('Line Number: %d' % index)

```

output:
```
oins in my file
Line Number: 2
oins in the next line

```

---

### Post by StephenF on 2010-11-17
```

print("Line number:", index)

```

---

### Post by sysop on 2010-11-18
> **Arndt said:**
> Sorry for being misleading. I tried the program but made an error in the input, so I drew the wrong conclusion about 'in'. As you say, the OP will have to get back with more information about how it doesn't work.

By not working I mean it does not find the substring "oins" in the file and print the line, even though I can see it in the text based log file many times. I just needed the script to print only the lines with the substring "oins" from the file to help me visually separate those lines from the others to quickly assess certain things.

---

### Post by sysop on 2010-11-18
> **DaithiF said:**
> and a couple of slight variations on mo.reina's solution:

```
with open('test.txt') as f:
    for index, line in enumerate(f, start=1):
        line = line.rstrip('\r\n')
        if "oins" in line:
            print(line)
        else:
            print('Line Number: %d' % index)

```

output:
```
oins in my file
Line Number: 2
oins in the next line

```

Thanks DaithiF and mo.reina for the code clean up. That looks much easier to maintain. I tried these code examples and finally got some results, but it still seems to be missing lines that do contain "oins" occasionally? I'm starting to think it might be something with the formatting of the log file itself? Thanks for everyone's replies!

Well, it does appear to be a formatting issue. I created a seperate file and the script worked nicely. Now I guess I need to delve into creating a script to reformat the file first. ;) More fun with Python. Thanks everyone for helping me realize what was actually happening and for showing me how to better clean up my code.

---

