---
title: "Requesting a bit of help troubleshooting a python interpreter error."
date: 2010-03-09
forum: Programming Talk
---

### Post by Stev0 on 2010-03-09
Working with a piece of python 3.1 code that's throwing an error when I attempt to run it. Not quite sure where I made the mistake, wondering if I could get a few sets of eyes to take a look at it and determine whats what. The code is as follows:
[PHP]import re 

def logparse():   
        
            
            log_file = input("Enter the path to the log file: ") 
            sigs_file = input("Enter the path to the signature file: ") 

            lines = {}
            with open(sigs_file) as r:
                for item in r:
                    if item and not item.startswith("#"):
                        lines[item] = []
                        lines[item].append(re.compile(item))
                        lines[item].append(0)
                        prev = item
                    elif item and item.startswith("#"):
                        lines[prev].insert(0, item)
                        

                    

            with open(log_file) as fd:
                count = 0
                for line in fd:
                    count = count + 1
                    for expr in lines.keys():
                        found = lines[expr] [1].search(line)
                        if found:
                            lines[expr] [2] = lines[expr] [2] + 1
                            lines[expr].append(count)

            print("--Signatures Found--     --Occurences--")
            for val in lines.values():
                print(val[0], val[2])

print("A simple command line log parser.")
print()
logparse()[/PHP]Which is resulting in this error:
  File "/home/stephen/pyparse.py", line 29, in logparse
    found = lines[expr] [1].search(line)
AttributeError: 'int' object has no attribute 'search'

---

### Post by diesch on 2010-03-10
Here you append an int:

```

if item and not item.startswith("#"):
        lines[item] = []
        lines[item].append(re.compile(item))
        lines[item].append(0)

```

And then you try to call this int's .search method:

[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]```

for expr in lines.keys():
     found = lines[expr] [1].search(line)

```

---

### Post by Stev0 on 2010-03-10
:oops: well yes I am aware of the specific location thats causing the error, but I'm not regexpr savy enough to understand why its throwing the error at me. Any suggestions?

---

### Post by diesch on 2010-03-10
having a closer look the problems seems to be that in python lists start wit index 0 while you assume they start with index 1.

```
found = lines[expr] [1].search(line)
```
acceses the *second* item of *lines[expr]*, i.e. the int instead of the regex object.

---

### Post by Stev0 on 2010-03-10
I changed the line to read: ```
 found = lines[expr] [0].search(lines)
```

Giving me a similar error, AttributeError: 'str' object has no attribute 'search'.

---

### Post by DaithiF on 2010-03-10
with these 2 lines you insert strings into position 0 when the line is a comment.  So sometimes position 0 has a regex, and sometimes it has a string.  When its a string the search method fails with the error you describe.

```
elif item and item.startswith("#"):
    lines[prev].insert(0, item)

```

---

