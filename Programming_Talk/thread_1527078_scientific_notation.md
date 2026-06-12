---
title: "scientific notation?"
date: 2010-07-08
forum: Programming Talk
---

### Post by unrealer on 2010-07-08
I was wondering if bash allows any sort of multiplication that involves scientific notation.

for example


I have 3 variables 

a = 20
b = 0.4
c = 6e-5

I want to multiply those by a constant of 1e6 , and display the variable back in scientific notation, however I ran to issues with bc.

Anyone have any ideas?

Thanks

---

### Post by xsinsx on 2010-07-09
From what i know it does not. So you would of-course have to convert your number. I am sure that it would be simple enough to write a script that intercepts your the notation and could convert it for you to spit out an answer... I would play with the idea but i do not have time right now.

---

### Post by xsinsx on 2010-07-09
upon a quick google search i found someone who has given an example of one way to handle Scientific notation in the bash shell.

```
[color=#008000]echo[/color] [color=#BA2121]"1.234e23 9.876e14"[/color] | sed [color=#BA2121]'s/e/*10^/g;s/ /*/'[/color] | bc

```
 

here is the source i found this. You might find it helpful.

[http://www.unix.com/shell-programming-scripting/74198-bash-scientific-notation.html](http://www.unix.com/shell-programming-scripting/74198-bash-scientific-notation.html)

---

### Post by trent.josephsen on 2010-07-09
Zsh supports floating-point calculations with E-notation:

```
% echo $((1.234e23/2))     
6.1699999999999999e+22
```

Just a thought.

---

### Post by delerious010 on 2010-11-06
> **xsinsx said:**
> upon a quick google search i found someone who has given an example of one way to handle Scientific notation in the bash shell.

```
[color=#008000]echo[/color] [color=#BA2121]"1.234e23 9.876e14"[/color] | sed [color=#BA2121]'s/e/*10^/g;s/ /*/'[/color] | bc

```
 

here is the source i found this. You might find it helpful.

[http://www.unix.com/shell-programming-scripting/74198-bash-scientific-notation.html](http://www.unix.com/shell-programming-scripting/74198-bash-scientific-notation.html)

Just came across this post ...
There's an error in the sed regex. the "e" should be "e+".

---

