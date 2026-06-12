---
title: "Need help with python..."
date: 2009-09-14
forum: Programming Talk
---

### Post by anotherdisciple on 2009-09-14
I am reading "A Byte of Python" and it's going well...
except I don't get this piece of example code.
```
#!/usr/bin/python
# Filename: total.py

def total(initial=5, *numbers, **keywords):
[INDENT]count = initial
for number in numbers:[/INDENT]
[INDENT][INDENT]count += number[/INDENT][/INDENT]
[INDENT]for key in keywords:[/INDENT]
[INDENT][INDENT]count += keywords[key][/INDENT][/INDENT]
[INDENT]return count[/INDENT]
print(total(10, 1, 2, 3, vegetables=50, fruits=100))
```

It all makes sense to me except the "+=" part. How do I interpret that?

---

### Post by lykeion on 2009-09-14
count += number

is the same as

count = count + number

---

### Post by Arndt on 2009-09-14
> **anotherdisciple said:**
> I am reading "A Byte of Python" and it's going well...
except I don't get this piece of example code.
```
#!/usr/bin/python
# Filename: total.py

def total(initial=5, *numbers, **keywords):
[INDENT]count = initial
for number in numbers:[/INDENT]
[INDENT][INDENT]count += number[/INDENT][/INDENT]
[INDENT]for key in keywords:[/INDENT]
[INDENT][INDENT]count += keywords[key][/INDENT][/INDENT]
[INDENT]return count[/INDENT]
print(total(10, 1, 2, 3, vegetables=50, fruits=100))
```

It all makes sense to me except the "+=" part. How do I interpret that?

These seem to be called "augmented assignments" in Python (they exist in C, too, for example). Look at [http://python.org/doc/2.5.2/ref/augassign.html](http://python.org/doc/2.5.2/ref/augassign.html).

---

### Post by Drone022 on 2009-09-14
```
count += 1;
```
and
```
count = count + 1
```
mean the same thing.

e.g. from your code...
```
count += number
count = count + number
```

---

### Post by anotherdisciple on 2009-09-14
Thanks everyone... that is what I kind of assumed, but it seems like a strange way to write it. Thanks for the help everyone!

---

### Post by Arndt on 2009-09-14
> **anotherdisciple said:**
> Thanks everyone... that is what I kind of assumed, but it seems like a strange way to write it. Thanks for the help everyone!

Actually, the original form in C was =+ etc.

---

### Post by anotherdisciple on 2009-09-14
> **Arndt said:**
> Actually, the original form in C was =+ etc.

You know... that actually makes more sense to me...

---

### Post by diafanos on 2009-09-14
the bad thing is that Python does not support increment operation:

i.e., ++i    
<=>    i += 1    
<=>    i = i + 1
(as well as --i, i++, i-- etc)

I love that in Java, and I really miss it.

---

### Post by Can+~ on 2009-09-14
> **diafanos said:**
> the bad thing is that Python does not support increment operation:

i.e., ++i    
<=>    i += 1    
<=>    i = i + 1
(as well as --i, i++, i-- etc)

I love that in Java, and I really miss it.

How frequently are you doing this? Most of the time in python, you rarely need to keep track of a counter.

---

### Post by snova on 2009-09-14
> **anotherdisciple said:**
> You know... that actually makes more sense to me...

As I recall, it is also ambiguous. Is this addition, or changing the sign?

[PHP]x=+y;[/PHP]

---

