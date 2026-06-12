---
title: "Using len(sys.argv) directly to define a for loop in Python"
date: 2016-08-21
forum: Programming Talk
---

### Post by motoperpetuo on 2016-08-21
Is there a way to use sys.argv directly to define the upper limit of a for loop in Python? I hope I'm using the right terminology. I don't have a lot of experience writing code, and I'm very new to Python. What I mean is that when I try this:

```

for x in range(1,len(sys.argv):

```
I get:
```

File "./dice.py", line 13
    for x in range(1,(len(sys.argv)):
                                    ^
SyntaxError: invalid syntax

```
So, I have to do this as a workaround:
```
y = len(sys.argv)

for x in range(1,y):

```
I was able to do the equivalent of what I want in Perl:
```

for $x (1..$#ARGV) {

```
I'm guessing I just have my parentheses wrong or need to put a space somewhere or something like that, but it's been a difficult question to google. I'd greatly appreciate any advice.

---

### Post by steeldriver on 2016-08-21
Maybe just mismatched parentheses (count 'em) ... ?

---

### Post by motoperpetuo on 2016-08-21
Dammit...that was it. Could have sworn I checked for that. Thanks!

---

### Post by motoperpetuo on 2016-08-21
I know I'm supposed to mark this as solved now, but I can't see an easy way to do it.

---

### Post by howefield on 2016-08-21
> **motoperpetuo said:**
> I know I'm supposed to mark this as solved now, but I can't see an easy way to do it.

Up above your original post, thread tools menu > mark this thread as solved.

Thanks for marking it such.

---

