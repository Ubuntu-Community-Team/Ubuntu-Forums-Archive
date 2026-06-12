---
title: "Python read error?"
date: 2009-01-21
forum: Programming Talk
---

### Post by djbushido on 2009-01-21
Okay, I am trying to make a study card program. Yeah, it's small, but proof of concept for me. The problem is that I try to read just 1 character, but something gets messed up. My code is this:

```
import sys

"""
This is where all the study cards get placed. The format is:
def cardx():
	print 'Question goes here'
	print 'Answer choice A'
	print 'Answer choice B'
	print 'Answer choice N'
	
	if (sys.stdin.read(1)=='correct answer'):
		print 'Correct!\n\n'
	else:
		print 'Incorrect. Answer was <correct_answer>'
		
No return function is needed, but may be used.
"""
def card1():
	print 'As the founder of Rhode Island, Roger Williams:'
	print '\nA) Established religious freedom for all but Jews and Catholics'
	print '\nB) Supported some types of special priveleges'
	print '\nC) Established complete religious freedom for all'
	print '\nD) Demanded attendance at worship'
	print '\nE) Became a very wealthy man'
	
	if (sys.stdin.read(1)=='c'):
		print 'Correct!\n\n'
	else:
		print 'Incorrect. The answer was (C)\n\n'
	sys.stdin.flush()
	
def card2():
	print 'In 1649, Maryland\'s Act of Toleration'
	print '\nA) Was issued by Lord Baltimore'
	print '\nB) Abolished the Death Penalty'
	print '\nC) Gave freedom only to Catholics'
	print '\nD) Protected Jews and Atheists'
	print '\nE) Guaranteed toleration to all Christians'
	
	if (sys.stdin.read(1) == 'e'):
		print 'Correct!\n\n'
	else:
		print 'Incorrect. The answer was (E)\n\n'
	sys.stdin.flush()
```

My error is that when run, this happens:
```
As the founder of Rhode Island, Roger Williams:

A) Established religious freedom for all but Jews and Catholics

B) Supported some types of special priveleges

C) Established complete religious freedom for all

D) Demanded attendance at worship

E) Became a very wealthy man
c
Correct!


In 1649, Maryland's Act of Toleration

A) Was issued by Lord Baltimore

B) Abolished the Death Penalty

C) Gave freedom only to Catholics

D) Protected Jews and Atheists

E) Guaranteed toleration to all Christians
Incorrect. The answer was (E)

```

On the second one, I am not even able to get an answer in, although I tried to flush the input buffer. I'm pretty sure it has to do with the stdin.read, but want to just have a temporary location, so I don't have to pass around variables all the time, or keep redeclaring them.

---

### Post by eightmillion on 2009-01-21
Maybe you should use raw_input. Something like this:
```
	if raw_input().startwith('c'):
		print 'Correct!\n\n'
	else:
		print 'Incorrect. The answer was (C)\n\n'
```
or this:
```
	if raw_input()[0] == 'c':
		print 'Correct!\n\n'
	else:
		print 'Incorrect. The answer was (C)\n\n'
```
Note that on the second one, you'll raise an IndexError exception if the user doesn't enter anything and just presses return.

---

### Post by djbushido on 2009-01-21
I keep getting this problem:
```
 if (raw_input().startwith('c')):
AttributeError: 'str' object has no attribute 'startwith'

```

---

### Post by eightmillion on 2009-01-21
> **djbushido said:**
> I keep getting this problem:
```
 if (raw_input().startwith('c')):
AttributeError: 'str' object has no attribute 'startwith'

```

Sorry, that should have been startswith.

```
 if (raw_input().startswith('c')):

```

---

### Post by djbushido on 2009-01-21
Oh thanks!

I also fixed it right before the post with:
```
if (raw_input()=='c'):
```
however, this wasn't by any means without bugs, and your solution will work much better. Thanks! Now I need to figure out random.choice()... but that's for another topic.

---

### Post by snova on 2009-01-21
The sys.stdin.read() function reads one character, as it should, but then it leaves the newline in the stream. So the next time you read a character, it's not even a letter!

raw_input() conviently removes the trailing newline, so it works after switching input functions.

---

### Post by djbushido on 2009-01-21
Just for the record, I did know about the newline sitting on the buffer as well. The problem was that i called sys.stdin.flush(), which should have cleared out the stdin buffer. It apparently wasn't working right, and yes, the newline strip of raw_input() is nice, but may become a hassle later (i.e. not wanting newline stripped-don't know why). Anyway, thanks!

---

### Post by snova on 2009-01-21
> **djbushido said:**
> The problem was that i called sys.stdin.flush(), which should have cleared out the stdin buffer.

flush() doesn't do anything on input streams...

---

### Post by djbushido on 2009-01-21
That'll be why it didn't work...
Is there a way to "flush" the input buffer?

---

### Post by snova on 2009-01-21
"flush" doesn't apply to input streams, it only makes sense for output.

On the other hand, you can use sys.stdin.readline() and ignore the return- it'll take the newline with it, though also everything before it- so that may be undesirable sometimes.

Alternatively, you could just strip the input line.

```
sys.stdin.readline().strip()
```

---

### Post by wmcbrine on 2009-01-22
> **djbushido said:**
> Is there a way to "flush" the input buffer?You could use curses. Then you could detect each keystroke, too, instead of waiting for Enter. But you'd have to rewrite the whole thing.

---

### Post by djbushido on 2009-01-23
I think I'll just do the readline, check with starts_with(), and that should be it. I hope.

---

