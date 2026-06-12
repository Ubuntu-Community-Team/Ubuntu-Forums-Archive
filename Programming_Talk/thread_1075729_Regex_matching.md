---
title: "Regex matching"
date: 2009-02-20
forum: Programming Talk
---

### Post by fhsm on 2009-02-20
I'm trying to pull lines from a text file that match a regex.  I'm using python.  I've got everything under control except the regular expression pattern.  The file is output from a animal tracking system where lines can have almost any contents.  The lines I'm looking for are of the following format:
```

   0     0   0    0.0  0:00:00 0 

```
The white space between the numbers are a variable number of spaces and any number should count as a match.  The next to last column is a 24hr clock time.
The upper limit on output is (white space aside):
```

   999   999 999  99.9 23:59:59 oo

```
The last column is just a limitless integer counter (couldn't get an infinity symbol to post, thus the oo).  In practice it will never get above 100,000.  

Can someone suggest a pattern to match this?

---

### Post by unutbu on 2009-02-20
[PHP]#!/usr/bin/env python
import re
data='''blah blah blah
   0     0   0    0.0  0:00:00 0
   999   999 999  99.9 23:59:59 100000
walla walla washington'''
pat=re.compile('(\d+)\s+(\d+)\s+(\d+)\s+([\d.]+)\s+(\d{1,2}:\d{1,2}:\d{1,2})\s+(\d+)')
for line in data.split('\n'):
    match=pat.search(line)
    if match:
        num1=int(match.group(1))
        num2=int(match.group(2))
        num3=int(match.group(3))
        float1=float(match.group(4))
        time=match.group(5)
        counter=int(match.group(6))
        print 'num1: %s num2: %s num3: %s float1: %s time: %s counter: %s'%(num1,num2,num3,float1,time,counter)
    else:
        print 'Skipping: %s'%line[/PHP]
I think this is prety self-explanatory; if you have any questions, feel free to ask.

---

### Post by ghostdog74 on 2009-02-20
> **fhsm said:**
> I'm trying to pull lines from a text file that match a regex.  I'm using python.  I've got everything under control except the regular expression pattern.  The file is output from a animal tracking system where lines can have almost any contents.  The lines I'm looking for are of the following format:
```

   0     0   0    0.0  0:00:00 0 

```
The white space between the numbers are a variable number of spaces and any number should count as a match.  The next to last column is a 24hr clock time.
The upper limit on output is (white space aside):
```

   999   999 999  99.9 23:59:59 oo

```
The last column is just a limitless integer counter (couldn't get an infinity symbol to post, thus the oo).  In practice it will never get above 100,000.  

Can someone suggest a pattern to match this?

you don't have to specifically match each and every field. Does your text file contain the 24 hour clock format on any other lines?? ie, does this pattern occur elsewhere ?? if not, you can just split the line and get fifth element, then check for ":".
```

for line in open("file"):
  l = line.split()
  if ":" in l[4]:
    print line.strip()

```

---

### Post by mobilediesel on 2009-02-21
You could try [Redet]("http://www.billposer.org/Software/redet.html") to help build the regex. You enter some test data and adjust the regex until it matches properly. It's in the repository.

---

