---
title: "[SOLVED] Python problem with appending to a list"
date: 2007-08-16
forum: Programming Talk
---

### Post by triptoe on 2007-08-16
EDIT: Solved sorry. I was reinitializing scramm since i was using nested loops and declared it inside the first loop! argh

Hey I am a beginner here. I am just wondering how to fix this problem... basically I am using a while loop two shift the letters of a string over 2 places in the alphabet... and each time i shift them i store the value in a list.. and i append it which is suppose to add it to the end of the list. the problem is that each time it goes through the loop, instead of getting appended it replaces the original index. The length of the list never changes and only ever has 1 index...

I assume this is because the value of it is local... or something. how do i return it so that the value is save and it gets properly appended? Here is my code:

```
#! /usr/bin/env python
# Program that decodes an encrypted message which the letters of the alphabet
# are shifted over 2 places

import string
f = open("scramb","r")

scramble = f.read()
f.close()

alpha = "abcdefghijklmnopqrstuvwxzy"
index = 0

# cycle through the scrambled letters starting from the first
while index <len(scramble):
	index2 = 0
	counter = 0
# cycle through the alphabet, and then shift the value of the letter
# in the scrambled code, over 2 places in the alphabet
	while index2 < len(alpha):
		scramm = []
		if alpha[index2] == scramble[index]:
			if (index2+2) <= 25:
				scramm.append(index2+2)
		                print "scramm ", scramm[0]
				print "length of scram: ", len(scramm)
			# if the letter is y, shifting 2 places goes to a
			elif (index2+2) == 26:
				scramm.append(0)
			# if the letter is z, shift to b
			else:
				scramm.append(1)
		index2 = index2 + 1
	index = index + 1
```

---

