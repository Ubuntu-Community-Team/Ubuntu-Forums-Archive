---
title: "python how to list all possible keyboard combos"
date: 2016-12-03
forum: Programming Talk
---

### Post by kingpenguin on 2016-12-03
Ok, so I know if I do something like it will go through all numbers between the numbers that you type.

# This program is an attempt at making a number generator
import time
first = input("What is the first number you wish to try? ")
last = input("What is the last number you wish to try? ")
counter = int(first)
while counter <= int(last):
	print(counter)
	counter += 1
time.sleep(100)

Where am I getting lost is how can I do the same kind of output from letter and symbols as well?
So basically a, b, c.... aaa, aab, aac... 1ac, 3rc and so on. 
Also please don't just spell it out fully showing me the full code because I am doing to learn more than anything. Just give me some hints because I am not seeming to find online about how to do this that makes any sense. all my projects I have done is in python 3.5 so please give help for that version.

---

### Post by QIII on 2016-12-03
Hello!

See if [this]("http://www.asciitable.com/") gives you a hint.

Best wishes!

---

### Post by kingpenguin on 2016-12-03
edited because I figured out why it wouldn't run. now i am just trying to find what to do next

---

### Post by kingpenguin on 2016-12-03
But my idea was to try and make the how_long var make an array with that many spots. the change each array spot then do a str .join.

---

