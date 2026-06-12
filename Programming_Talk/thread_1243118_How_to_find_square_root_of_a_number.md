---
title: "How to find square root of a number?"
date: 2009-08-17
forum: Programming Talk
---

### Post by colau on 2009-08-17
Hi,
How to find square root of a number in bash shell?
Is there any built-in sqrt function?

---

### Post by kaibob on 2009-08-18
I don't know of any built-in square root function. I've just started to learn the bc utility. It will find the square root of a number as follows:

```
calc=$(echo "sqrt ( 10 )" | bc -l) ; echo $calc
```

Change the number 10 to whatever is applicable.

---

### Post by colau on 2009-08-18
> **kaibob said:**
> I don't know of any built-in square root function. I've just started to learn the bc utility. It will find the square root of a number as follows:

```
calc=$(echo "sqrt ( 10 )" | bc -l) ; echo $calc
```

Change the number 10 to whatever is applicable.

What are the other mathematical functions available in bash shell(like "sqrt")?
```

floor
ceil
pow

```

---

### Post by soltanis on 2009-08-18
They're not available through bash, they're available through the bc (1) utility, a command line calculator. Look through its manpage for syntax + examples.

---

### Post by geirha on 2009-08-18
Bash can only do integer arithmetics, not floating point, so you have to rely on an external program to do those types of calculations.

```
$ echo $((2+2))
4
$ echo $((5/2))
2

```

---

### Post by colau on 2009-08-18
> **geirha said:**
> Bash can only do integer arithmetics, not floating point, so you have to rely on an external program to do those types of calculations.

```
$ echo $((2+2))
4
$ echo $((5/2))
2

```
What are those external programs?One is bc.

---

### Post by Arndt on 2009-08-18
> **colau said:**
> What are those external programs?One is bc.

For example:

```
$ python -c 'import math; print math.sqrt(3)'
1.73205080757
$ perl -e 'print sqrt(3), "\n"'
1.73205080756888

```

---

### Post by credobyte on 2009-08-18
[http://abs-guide.awardspace.com/mathc.php](http://abs-guide.awardspace.com/mathc.php) - give it a try :)

---

### Post by djbushido on 2009-08-18
You could write simple C/C++ programs to "import <math.h>" and then perform a simple function and exit - like cos, sqrt, etc. But I like the idea of a python shell a bit more, personally.

---

