---
title: "help with python program"
date: 2009-11-30
forum: Programming Talk
---

### Post by Despot Despondency on 2009-11-30
Hi, I'm trying to write a simple python program that opens a file and prints the first N lines of it. Here's the code

```

#! /usr/bin/env python

import os

filename = raw_input('Enter file name: ')
N = raw_input('Enter numbers of lines to display: ')

fobj = open(filename)
allLines = fobj.readlines()

counter = 0

for eachLine in allLines:
	counter += 1
	if counter < N:
		print eachLine,		

```

The program opens the file I enter but it prints all the lines in the file instead of just the first N lines. Why is this happening? TAI

---

### Post by 0cton on 2009-11-30
First of N is not an integer (a number) so in python a string will always be bigger than an integer (I think, not sure)
so you need to convert it to an int, do N=int(N) (beware if the user types let's say "A" instead of a number :)
Also your approach is kinda inefficient, the loop will still get lines m but not print them (you are getting all the lines from the file but just printing some of them)
instead you should break after the first N lines are printed.
if counter>=N:
  break
break will break out of the loop.
cheers.

---

### Post by DaithiF on 2009-11-30
because N is a string, not a number.  try converting it to an int first before doing the comparison against your counter.

---

### Post by Despot Despondency on 2009-11-30
Excellent. I knew it was going to be something silly like that. Thanks for your help.

---

### Post by Can+~ on 2009-11-30
Notice that your code:

[PHP]for eachLine in allLines:
	counter += 1
	if counter < N:
		print eachLine,[/PHP]

Actually goes through the whole file, but just prints the first N strings. So you're wasting resources. With a simple break statement, you can end it:

[PHP]filename = raw_input('Enter file name: ').strip()
maxlines = int(raw_input('Enter numbers of lines to display: '))

with open(filename) as infile:
	for count,line in enumerate(infile):
		print line
		
		if count > maxlines:
			break
		[/PHP]

(Using the "with" statement, and enumerate instead of a separate counter)

---

### Post by 0cton on 2009-12-01
> **Can+~ said:**
> Notice that your code:

[PHP]for eachLine in allLines:
	counter += 1
	if counter < N:
		print eachLine,[/PHP]

Actually goes through the whole file, but just prints the first N strings. So you're wasting resources. With a simple break statement, you can end it:

[PHP]filename = raw_input('Enter file name: ').strip()
maxlines = int(raw_input('Enter numbers of lines to display: '))

with open(filename) as infile:
	for count,line in enumerate(infile):
		print line
		
		if count > maxlines:
			break
		[/PHP]

(Using the "with" statement, and enumerate instead of a separate counter)

I wonder if anyone actually read my reply :\

---

### Post by wmcbrine on 2009-12-01
> **Can+~ said:**
> [PHP]filename = raw_input('Enter file name: ').strip()
maxlines = int(raw_input('Enter numbers of lines to display: '))

with open(filename) as infile:
	for count,line in enumerate(infile):
		print line
		
		if count > maxlines:
			break
		[/PHP]
How about this?

```
filename = raw_input('Enter file name: ').strip()
maxlines = int(raw_input('Enter numbers of lines to display: '))

with open(filename) as infile:
    for count in range(maxlines):
        print infile.readline().strip('\n')
```

---

