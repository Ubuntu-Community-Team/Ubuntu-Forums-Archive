---
title: "Python problem"
date: 2007-12-26
forum: Programming Talk
---

### Post by Belliinator on 2007-12-26
I am a noob when it comes to programming. This is in the official documentation of python, but every single time I enter it in it comes out with a response that is mathematically incorrect, and it is different from the response in the manual. What am I doing wrong? 
```

>>> for n in range(2, 10):
	for x in range(2, n):
		if n % x == 0:
			print n, 'equals', x, '*', n/x
			break
		else:
			print n, 'is a prime number'

```

Then it comes out with this:
```
			
3 is a prime number
4 equals 2 * 2
5 is a prime number
5 is a prime number
5 is a prime number
6 equals 2 * 3
7 is a prime number
7 is a prime number
7 is a prime number
7 is a prime number
7 is a prime number
8 equals 2 * 4
9 is a prime number
9 equals 3 * 3

```

Thanks in advance, this is really bugging me!!!

---

### Post by LaRoza on 2007-12-26
> **Belliinator said:**
> 
Thanks in advance, this is really bugging me!!!

Can you link where you got it?

(Now you know why they are called "bugs", although the term originated from an actual moth in a computer system)

---

### Post by Belliinator on 2007-12-26
[HTML]http://docs.python.org/tut/node6.html#SECTION006400000000000000000[/HTML]

---

### Post by ghostdog74 on 2007-12-26
hint: Read the docs again, word by word. See where each word is placed. You will find your answer

---

### Post by LaRoza on 2007-12-26
-EDIT I should read code when I am half asleep.

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> Now that I look at it (unlike before) I see that it is running fine. Perhaps you misunderstood the intent of the code?

the "else" belongs to the inner for loop, not the "if"

---

