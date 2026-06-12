---
title: "Python Challenge 7: Boolean Expressions"
date: 2007-08-20
forum: Programming Talk
---

### Post by yuvlevental on 2007-08-20
Using what you learned, create a program where you have to enter both a username and a password. The program will say “You are correct” or “You are Incorrect.” The person will get five tries. Also, to get the usual reward, you must use the “and” operator at least once. Email challenge answers to yuval [dot] imperius [at] gmail [dot] com. Thanks for visiting!

---

### Post by Smygis on 2007-08-20
```

import sys
i = 5
while i: 
    if raw_input("User: ") and raw_input("Password: "): 
        print "You are correct"
        i = 0 # I culd use a break heare but nahh
    else: 
        print "You are Incorrect."
        i -= 1
        if not i:
            sys.exit()
```

lol? All according to specifications.

---

### Post by triptoe on 2007-08-21
I think it would be more fun if rather than people emailing you the answers they posted them in this thread. That way other beginners could see the many and various ways different people implement the same thing... and could learn from it.. and also if they were uncertain.

You could put it in code like this:

```
*

*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*

*
*
**spoiler below**
#!
name = "joe"
passw = "shmo"

for i in range(5):

        if raw_input("Username: ") == name and raw_input("pass: ") == passw:
                print "you are correct"
                break
        else:
                print "you are incorrect"


```

If you wanted to let people read the thread without spoilers

---

### Post by samjh on 2007-08-21
> **Smygis said:**
> lol? All according to specifications.There is always at least one smart-alec. ;)

******* SPOILER WARNING *******
.
.
.
.
.
.
.
.
.
.
******* SPOILER REAL SOON *******
.
.
.
.
.
.
.
.
.
```
i = 0
realUser = "Joe"
realPass = "Blow"

while i < 5:
	userName = raw_input("Username: ")
	passWord = raw_input("Password: ")
	if (userName == realUser) and (passWord == realPass):
		print "You are correct."
		i = 5
	else:
		print "You are incorrect."
		i = i + 1
```
:D

---

