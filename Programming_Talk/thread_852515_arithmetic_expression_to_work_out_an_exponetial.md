---
title: "arithmetic expression to work out an exponetial"
date: 2008-07-07
forum: Programming Talk
---

### Post by J05HYYY on 2008-07-07
hello i'm writing some shell script (sh) and I would like to know how to get the power of something. e.g. x ^ y . when i try:
```
$(( x ** y ))
```
using:
```
#!/bin/sh
```
it doesn't work.

any suggestions?

---

### Post by slavik on 2008-07-07
** works in Perl, I don't think Bash can do it, unless you write your own function.

May I ask what you are trying to do? If you intent on using Bash for heavy math, I would advise against it.

---

### Post by J05HYYY on 2008-07-07
it does work in bash with the interpreter set as
```
#/bin/bash
```
but i really want my code to be as portable as possible - so it can run on unix and mac and maybe windows too.

this part of the program creates every different combination when it's given bit size and numeral system:
It can be used in many situations for example - if you had a 3 digit lock, with the numbers 0 - 9 (10 ^ 3 = 1000 different combinations)

---

### Post by geirha on 2008-07-07
$(( x ** y)) will work in bash if x and y are integers. In sh, you'll need to use some third-party tool. bc is commonly used for arithmetics in shell scripts.

```
$ echo 2^5 | bc
32

```

---

### Post by J05HYYY on 2008-07-07
well i wrote a little algorithm - which works to a certain extent but it can't handle "big numbers" :D
```

C=1
read A
D=$A
read B
while [ $C -lt $B ]; do
C=$(( C + 1 ))
D=$(( $D * $A ))
done
echo $D

```

i read a bit more and apparently you can do powers with the math.h include which was added to the C library or something...
not sure what would be the more preferable (math.h or bc)?

[here's a link...]("http://www.codecogs.com/reference/c/math.h/pow.php?alias=pow")

---

### Post by gnusci on 2008-07-07
Use **bc** with **-l** option to work with float point numbers

**echo "2.3^3" | bc -l**

but only works for integer power, if you need for a float point power use "x^y == e^(y*log(x))", for instance for 2.3^3.5 you can use:

**echo "e(3.5*l(2.3))" | bc -l**

---

### Post by ghostdog74 on 2008-07-07
> **J05HYYY said:**
> well i wrote a little algorithm - which works to a certain extent but it can't handle "big numbers" :D
```

C=1
read A
D=$A
read B
while [ $C -lt $B ]; do
C=$(( C + 1 ))
D=$(( $D * $A ))
done
echo $D

```

i read a bit more and apparently you can do powers with the math.h include which was added to the C library or something...
not sure what would be the more preferable (math.h or bc)?

[here's a link...]("http://www.codecogs.com/reference/c/math.h/pow.php?alias=pow")

awk comes with most all flavors of *nix by default.
```

awk 'BEGIN{print 4^5}'

```
otherwise, you can use bash too (after version 2.02)
```

let "y=5**3"
echo $y

```
you have posted previously, so why haven't you started reading the bash manual yet? its answered [here.](http://tldp.org/LDP/abs/html/ops.html)

---

### Post by J05HYYY on 2008-07-11
As I might have mentioned; personally in an idealistic manner I would the I write to be as portable as possible.

I have read several guides and manuals, each one a little different. As an intellectual person I want to find the best way of doing things hence why I sometimes ask these questions.

There are things which have to be considered when writing code. The main and first concern is that not every shell in the world is bash. Hence why I am trying to avoid bash-specific commands.

Now (because I asked) I have four potential options: write my own, libc, awk or bc. People have different ways of doing things which is why I like forums. :)

---

