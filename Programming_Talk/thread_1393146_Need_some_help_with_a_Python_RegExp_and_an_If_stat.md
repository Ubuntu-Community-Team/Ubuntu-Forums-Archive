---
title: "Need some help with a Python RegExp and an If statement"
date: 2010-01-29
forum: Programming Talk
---

### Post by Stev0 on 2010-01-29
Messing around trying to write myself a rudimentary log parser to learn how to use regular expressions in Python. I've got it working...for the most part. I was able to get it to parse a log file and output the desired expression, but when I entered an else statement into the function in order to give the program the ability to display an error, I broke it. 

I've played with different positioning of the else statement, and it either doesn't parse the log file and just prints the error function, or it will parse like normal, until I purposely introduce an error, and just print error function continuously...any ideas what I'm doing wrong? And seeing as I have a total of about 45 minutes time programming in Python, is there a simpler or cleaner way of doing what I want it to do? Code is as follows:
[PHP]import sys
import re

def fail():

        print "Expression not found."
        print ""
        parser();

def parser():
        
        log = raw_input ("Path to log file: ")
        expr = raw_input ("Expression to parse: ")

        r = re.compile(expr)

        fd = open(log, 'r')
        for i in fd:
                if r.search(i):
                    print i

                else:
                        fail();
             
        parser();[/PHP]

---

### Post by Stev0 on 2010-01-29
bump after fixing my forum code idioacracy

---

### Post by whiteychs on 2010-01-29
last line shouldn't be indented. that's probably a pasting error i'm assuming. :)


You're parsing line by line, right?

Then remove the recusive calling parse() from fail()

```
def fail(): 

        print "Expression not found." 
        print "" 
```

---

### Post by diesch on 2010-01-29
Calling fail() for each line that doesn't match is probably not the right thing here.

I'd rather do something like

```
count=0
fd = open(log, 'r')
for i in fd:
    if r.search(i):
         print i
         count+=1

if count == 0:
  fail()
else:
  print "Found %s matching lines."%count

```

---

### Post by Stev0 on 2010-01-29
Thanks for the replies you guys. At first I thought it was just spewing for error statements continuously, but when scrolling through the output I noticed lines that had returned the input value, and it was returning the error for EVERY line that did not contain the value that matched the expr variable. The count thing is exactly what I was looking for.

---

### Post by lavinog on 2010-01-29
you can use a for...else statement to determine if the expression was not found

```

for i in fd:
  if r.search(i):
    print i
    break
else:
  fail()

```
notice the else is grouped with the for loop and not the if
                        fail();

---

