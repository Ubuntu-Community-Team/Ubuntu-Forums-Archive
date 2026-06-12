---
title: "[SOLVED] value too great for base -bash"
date: 2008-01-25
forum: Programming Talk
---

### Post by sagarhshah on 2008-01-25
Hi,

I am writing a script in bash.
Everything works fine well almost!!

I am only having one problem
whenever this part of the script

```

if [ $((items)) -eq 0 ] ; then

```

comes across a 08 or 09 it throws an error "value too great for base (error token is "09")" 

I read up on it and apparently it seems to think 08 or 09 are hex nos or something to that effect.
I can't replace the 0's as I need them for later on in the script.

does anybody have a workaround to this?

any help would be appreciated
thanks
sagar

---

### Post by colo on 2008-01-25
Why are you using an arithmetical expression in there ( "$((value))" instead of "${value}"?

The error message is, however, quite easily explained. Numerical values starting with a zero (0) are interpreted as numbers in octal notation by the C language. As the only digits allowed in octal are {0..7}, an 8 or a 9 will cause the evaluation to fail.

Hth,
- colo

---

### Post by sagarhshah on 2008-01-25
The double brackets were my bad.
Am new to shell scripting.


ok so numbers that start with 0 are thought of as octal or base 8

Is there any way I can work around this?
This is the only thing in my script which is not working.

Quite frustrating when you know you're close yet you are still far!!

---

### Post by ghostdog74 on 2008-01-25
you can remove the "0"s in front of the numbers first

eg
```

items="08"
items=`echo $items|sed 's/^0*//'`
echo $items

```

---

### Post by colo on 2008-01-25
Please post an excerpt of the relevant parts of the script in question, and also provide an example of in- and output (expected and actually received).

---

### Post by stroyan on 2008-01-25
You can explicitly state the base of a number using *base*#*number*
```
if [ $((10#$item)) -eq 0 ] ; then
```
That will have trouble if the number starts with a minus sign.
The '-' needs to be in front of the base like -10#009 for -9.

---

### Post by sagarhshah on 2008-01-25
```

if [ $((10#$item)) -eq 0 ] ; then

```

worked brilliantly for me .
there are no negative numbers in the script so the code that stroyan suggested works brilliantly!!

colo - the script in question takes input of a text file which contains random letters and numbers. I have to separate the numbers from the letters and pass on the numbers to a Luhn algorithm checker for validation.
it worked fine except when it came across numbers which started with 08 and 09 where it would abort that part of the script and continue to the next part without processing the rest of the numbers.

thanks man

Sagar

marked as solved for others who might find it useful

---

### Post by Davidux on 2009-08-18
Thanks, very useful! :D

---

### Post by X3MBoy on 2011-09-06
> **ghostdog74 said:**
> you can remove the "0"s in front of the numbers first

eg
```

items="08"
items=`echo $items|sed 's/^0*//'`
echo $items

```

This work for me perfectly, Thx. I had test this in SunOS 5.9, where commands don't have the actual sintax and i have to do calculations by myself with code.

Greetings,
X3MBoy

---

