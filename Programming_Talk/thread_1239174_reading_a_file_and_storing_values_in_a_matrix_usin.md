---
title: "reading a file and storing values in a matrix using python"
date: 2009-08-13
forum: Programming Talk
---

### Post by Glenn Jones on 2009-08-13
Hi guys,

I've slowly been moving away form scripting in matlab to scientific python. The move has been quite successful and I'm now quite comfortable with the matlab substitutes. What I'm currently doing is trying to learn 'pure' python.

My problem is that I'm trying to read a file which looks like the following 

19970201p,0001
0001
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
19970201p,0002
0002
...

What I'm interested in is the block of numbers i.e. lines 3 to 8 and so on and build up for each lien (i.e. line 3, line 11 etc). I can read the whole file using the following command

```
f=open('fname','r')
for eachLine in f:
    print eachLine,
f.close()
```

but I'm unsure how to store the numbers into a matrix.

Your help is much appreciated 

Cheers

---

### Post by unutbu on 2009-08-13
What can we take as certain about fname?

For instance, are lines of data always lines with 6 numbers separated by commas?

Does the beginning of a new block of numbers (e.g. 
19970201p,0001) always contain a letter? 

Is there always one extra line (e.g. 0001) before the block of numbers?

---

### Post by spupy on 2009-08-13
> **Glenn Jones said:**
> Hi guys,

I've slowly been moving away form scripting in matlab to scientific python. The move has been quite successful and I'm now quite comfortable with the matlab substitutes. What I'm currently doing is trying to learn 'pure' python.

My problem is that I'm trying to read a file which looks like the following 

19970201p,0001
0001
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
1,2,3,4,5,6
19970201p,0002
0002
...

What I'm interested in is the block of numbers i.e. lines 3 to 8 and so on and build up for each lien (i.e. line 3, line 11 etc). I can read the whole file using the following command

```
f=open('fname','r')
for eachLine in f:
    print eachLine,
f.close()
```

but I'm unsure how to store the numbers into a matrix.

Your help is much appreciated 

Cheers

As unutbu said, you first need to have a way to verify that the line you are reading is part of the block of numbers. Some simple rules like, "There are more than 3 commas", "there are only numbers besides the commas". How is the format of that file specified?
Let's say you have these rules down. Your code will look something like this:
```
numbers = []
for eachLine in f:
   if <here test if the line is from the numbers block>:
      line = [int(x) for x in eachLine.split(',')]
      numbers.append(line)
```

The first line in after the IF splits the line at the commas, converts the resulting strings into integers and stores them in the line array, which is appended to the numbers array on the next line. The numbers array will be a 2D array containing the integer values from the block.
At least that is how I see the solution, someone else might propose something more pythonic.

---

### Post by Glenn Jones on 2009-08-13
> **unutbu said:**
> What can we take as certain about fname?

For instance, are lines of data always lines with 6 numbers separated by commas?


The data is always seperated by commas. Based on what spupy said I can use this to get the data out. 

> if <here test if the line is from the numbers block>:

How do I test that the line had more than x commas?

---

### Post by spupy on 2009-08-13
> **Glenn Jones said:**
> The data is always seperated by commas. Based on what spupy said I can use this to get the data out. 



How do I test that the line had more than x commas?

```
comma_count = line.count(',')
```

---

### Post by Glenn Jones on 2009-08-13
> **spupy said:**
> ```
comma_count = line.count(',')
```

No way! Thats way to easy,  I feel like a real idiot!!!

---

### Post by spupy on 2009-08-13
> **Glenn Jones said:**
> No way! Thats way to easy,  I feel like a real idiot!!!

Don't worry. :) I'm also new to python, so I had to check this in the docs to make sure it was indeed so simple.

---

### Post by unutbu on 2009-08-13
It's hard to wipe that silly grin off our faces when programming in python. :P

---

### Post by spupy on 2009-08-13
> **unutbu said:**
> It's hard to wipe that silly grin off our faces when programming in python. :P

Someone finally understands what my avatar means! :D

---

### Post by dbw on 2011-04-07
Try numpy's getfromtxt.  It is about as powerful as Matlab's file import stuff.  [Here is a link to the relevant documentation.]("http://docs.scipy.org/doc/numpy/reference/generated/numpy.genfromtxt.html")

---

