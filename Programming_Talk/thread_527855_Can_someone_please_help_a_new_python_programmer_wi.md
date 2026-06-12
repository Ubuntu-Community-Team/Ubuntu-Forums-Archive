---
title: "Can someone please help a new python programmer with a semantic error"
date: 2007-08-17
forum: Programming Talk
---

### Post by triptoe on 2007-08-17
Hey I have a problem... it took me a while to realize exactly why my program wasn't working... yet although i see it i still don't understand why . here is my code:

```
#! /usr/bin/env python
#program takes a string, copies it into a list but only one of each unique value in the string, ignoring multiple copies
# if the string was "stramnal" it should create a list with s,t,r,a,m,n,l

import string

f = open("sordid", "r")

contains = f.read()

f.close()


container = [0]



i2 = 0
print "length of container is", len(container)
print "length of contains is", len(contains)
# only 10 repetitions for debugging purposes
while i2 < 10:
	counter = 0
	index = 0
	while index < len(container):
		print "index is: ", index
		print "length of container is: ", len(container)
		# cycle through entire container to the end
		# if a value in contains, is already stored in container, skip it
		if container[index] == contains[i2]:
			counter = counter + 1
			print "shout out now "
		# if you get to the end of container, and counter is still 0, then append the value from contains
		if index == (len(container)-1) & counter == 0:
			print "index inside the if is: ", index
			print "The length of container - 1 is: ", len(container) - 1
			container.append(contains[i2])
			break
		print "help meee"
		index = index + 1
	i2 = i2 + 1

print "length of container is: ", len(container)
```

Here is the output of the program (the print statements are just for debugging purposes)

> length of container is 1
length of contains is 98765
index is:  0
length of container is:  1
index inside the if is:  0
The length of container - 1 is:  0
index is:  0
length of container is:  2
index inside the if is:  0
The length of container - 1 is:  1
index is:  0
length of container is:  3
index inside the if is:  0
The length of container - 1 is:  2
index is:  0
length of container is:  4
index inside the if is:  0
The length of container - 1 is:  3
index is:  0
length of container is:  5
index inside the if is:  0
The length of container - 1 is:  4
index is:  0
length of container is:  6
index inside the if is:  0
The length of container - 1 is:  5
index is:  0
length of container is:  7
index inside the if is:  0
The length of container - 1 is:  6
index is:  0
length of container is:  8
index inside the if is:  0
The length of container - 1 is:  7
index is:  0
length of container is:  9
index inside the if is:  0
The length of container - 1 is:  8
index is:  0
length of container is:  10
index inside the if is:  0
The length of container - 1 is:  9
length of container is:  11


My problem... if i have an if statement: if index == (len(container)-1) & counter == 0:  , why does it keep executing that if statement even though the length of the container gets bigger and index stays at 0 ? if the value of index is 0 and the value of the length of the container - 1 is 1 or anything other than 0... then why is it executing that statement??

---

### Post by aJayRoo on 2007-08-17
The ampersand symbol ('&') is not the operator for logical AND. If you have come from a language like C then you might be surprised to learn that double ampersand ('&&') is also not the operator you are looking for! In python the operator for logical AND is simply the keyword 'and'. You would use it like this:
```
if ( (index == len(container)-1) and (counter == 0) )
```
I hope that helps you.

---

### Post by triptoe on 2007-08-17
That definitely helps... lol. I am surprised that it didn't give out a syntax error though... is & a legal to put in an if statement? What exactly does it do if it is not logical and?

---

### Post by aJayRoo on 2007-08-17
It does not give out a syntax error because a single ampersand is the operator the bitwise AND operation. I don't have time to explain what that means but the Wikipedia article on bitwise operations is fairly good so give that a read if you are curious :)

---

### Post by ssam on 2007-08-17
I recommend that you read some more about python.

i am guessing that you have come from another language. so you style is very un-pythonic. for example rather than a while loop with a counter, use a for loop

```

for x in range(10)
    print x

```

or even better, loop over the object you are working with

```

s = "hello"
for letter in s:
    print letter

```

so to get the unique letters do

```

s = "hello"
uniq = [] # an empty list
for letter in s:
    if letter not in uniq:
        uniq.append(letter)
print uniq

```

or if you don't care about the order you could just use a set (a set is just a list with no duplicates and no gaurenteed order)
```

print set("hello")

```

---

### Post by triptoe on 2007-08-17
> **ssam said:**
> I recommend that you read some more about python.


I agree! :P 

Your code is much easier to read and simpler. I came from a little bit of C++

---

### Post by pmasiar on 2007-08-17
As they say, really dedicated  C++ hacker can code C++ in any language! :-)

In python, I have this rule of thumb: if it feels like I am working too hard, I am doing it wrong. :-)

Python is very helpfull, and if you don't let him to help you, your code looks like C++ or Fortran :-)

Try this: in Python shell, type: "import this"
Read whole poem: every line is a sage advice from guru.

You need to look up not only syntax, but Python idioms. Google for it.
Also, "Dive into Python" might be good bood for you: not wasting your time with stuff for beginners, but intended for programmers experienced in some other language.

---

