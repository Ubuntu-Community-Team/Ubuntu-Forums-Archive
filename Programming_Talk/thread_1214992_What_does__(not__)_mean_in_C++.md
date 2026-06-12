---
title: "What does | (not || ) mean in C++"
date: 2009-07-16
forum: Programming Talk
---

### Post by wbest on 2009-07-16
I'm looking at some examples of code and they use the | operator.  The code is

GRAY      = RED   | GREEN | BLUE

and

B_GREEN   = GREEN   | FOREGROUND_INTENSITY

for example.

Now, I figure these aren't additions as (these are windows constants) is 0x0002 and FOREGROUND_INTENSITY IS 0x0008 making for a total of 0x0010.  But 0x0010 is already the definition for BACKGROUND_BLUE.

I'm a little confused about what this | operator does, but I can't find anything online as the search engines ignore it or something.

Any help would be greatly appreciated.

---

### Post by jero3n on 2009-07-16
| is bitwise OR operator.

---

### Post by lisati on 2009-07-16
[http://en.wikipedia.org/wiki/Bitwise_operation](http://en.wikipedia.org/wiki/Bitwise_operation)

---

### Post by wbest on 2009-07-16
Groovy, thanks.

---

### Post by Can+~ on 2009-07-16
```
00100001
01001011
----------
01101011
```

```

0 | 0 = 0
1 | 0 = 1
0 | 1 = 1
1 | 1 = 1
```

Same thing with bitwise-and

---

### Post by curvedinfinity on 2009-07-16
00001001 | 01000001 = 01001001

---

### Post by fr4nko on 2009-07-16
There are only 10 kinds of people in the world, those who understand binary numbers and those who don't.

:-)

Francesco

---

### Post by nvteighen on 2009-07-16
The importance of binary OR is that it allows you to sum up properties, as it will only yield 0 if both are 0. OR is also known as "bitwise addition". (AND is "bitwise product", where you only get 1 if both "factors" are 1).

---

### Post by Can+~ on 2009-07-16
The most common use is to store multiple boolean values in a single (or multiple) byte(s), just like the file permissions in *nix:

Say that you can read and execute

```
r-- = 100 = 4
--x = 001 = 1

r-x = 101 = 5
```

Later you want to know "Can I read the file?"

```
101 &
100
----------
100 : true
```

Yes, I can.

Can I write to the file?

```
101 &
010
----------
000 : false
```

Nope, I can't.

---

### Post by MadCow108 on 2009-07-16
c++ overs a standard container for just that purpose:
[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

---

