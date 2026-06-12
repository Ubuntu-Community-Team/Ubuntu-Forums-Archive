---
title: "Script read highest value"
date: 2012-06-09
forum: Programming Talk
---

### Post by dekker74 on 2012-06-09
Hi All,

Can someone help steer me to the simplest approach to write a script that reads the second column of a csv file and returns the highest value.

example file:

DATE,QUANTITY
Mon Apr 30 01:56:00 2012,42
Mon Apr 30 02:24:00 2012,72
Mon Apr 30 02:56:00 2012,102
Mon Apr 30 02:59:00 2012,132
Mon Apr 30 03:31:00 2012,222
Mon Apr 30 03:38:00 2012,192

TIA

---

### Post by diesch on 2012-06-09
```
 cut -d, -f2 your_file.csv  |  sort -n | tail -n1
```

---

### Post by dekker74 on 2012-06-10
That works great Diesch.

Can you explain how that line works?

TIA

---

### Post by The Cog on 2012-06-10
These three manual pages will help:
man cut
man sort
man tail
Use Q to quit the manual.

But in brief:
"|" is a joiner that takes the output from one program and feeds it into the next one.
cut cuts each line into pieces, -d, says comma is the delimiter
sort -n sorts these pieces numerically
tail -n1 takes the single last line from the list.

So overall, it cuts the number out of each line, sorts the numbers into order and then prints the last one in the list.

Nice solution, diesch.

---

### Post by codemaniac on 2012-06-10
> **dekker74 said:**
> Hi All,

Can someone help steer me to the simplest approach to write a script that reads the second column of a csv file and returns the highest value.

example file:

DATE,QUANTITY
Mon Apr 30 01:56:00 2012,42
Mon Apr 30 02:24:00 2012,72
Mon Apr 30 02:56:00 2012,102
Mon Apr 30 02:59:00 2012,132
Mon Apr 30 03:31:00 2012,222
Mon Apr 30 03:38:00 2012,192

TIA
An awk solution .

```
awk -F"," '$2 > max { max=$2 }; END { print max }' example_file
```

---

### Post by greenpeace on 2012-06-11
Example in python... assumes input file is called: 'data.csv'

```
#!/usr/bin/python
import csv
biggest=0 # where we're going to put the value
for line in csv.reader(open('data.csv', 'r')):
  try:
    if int(line[1]) > biggest: # number value is in 2nd column, index "1"
      biggest = int(line[1])     
  except ValueError: # if input is not actually a number...
    pass  # ...don't count it    
print "biggest: %s" % biggest
```

---

