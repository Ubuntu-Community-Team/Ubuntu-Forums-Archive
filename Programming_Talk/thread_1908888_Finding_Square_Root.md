---
title: "Finding Square Root"
date: 2012-01-14
forum: Programming Talk
---

### Post by achuth on 2012-01-14
Sir,
I would like to find the square root of a number.
How can I do it in a shell script (bash)?. While writing a shell script, can I use external libraries?

---

### Post by WasMeHere on 2012-01-14
I think that the shellscript commands are rather limited (+-*/ ...), so you have to add something. One possibility is to use octave (which can be installed from the repositories
```
sudo apt-get install octave
```
for example (write the [COLOR="Red"]red[/COLOR] commands inside octave)
```
octave:1> **[COLOR="Red"]rt2=sqrt(2)[/COLOR]**
rt2 =  1.4142
octave:2> **[COLOR="Red"]save octave-out.txt rt2[/COLOR]**
```
```
cat octave-out.txt
``` shows the content
```
# Created by Octave 3.0.5, Sat Jan 14 15:00:19 2012 CET
# name: rt2
# type: scalar
1.414213562373095
```
---
man bash shows what is included
```
ARITHMETIC EVALUATION
       The  shell allows arithmetic expressions to be evaluated, under certain
       circumstances (see the let and declare builtin commands and  Arithmetic
       Expansion).   Evaluation  is done in fixed-width integers with no check
       for overflow, though division by 0 is trapped and flagged as an  error.
       The  operators  and their precedence, associativity, and values are the
       same as in the C language.  The following list of operators is  grouped
       into  levels  of  equal-precedence operators.  The levels are listed in
       order of decreasing precedence.

       id++ id--
              variable post-increment and post-decrement
       ++id --id
              variable pre-increment and pre-decrement
       - +    unary minus and plus
       ! ~    logical and bitwise negation
       **     exponentiation
       * / %  multiplication, division, remainder
       + -    addition, subtraction
       << >>  left and right bitwise shifts
       <= >= < >
              comparison
       == !=  equality and inequality
       &      bitwise AND
       ^      bitwise exclusive OR
       |      bitwise OR
       &&     logical AND
       ||     logical OR
       expr?expr:expr
              conditional operator
       = *= /= %= += -= <<= >>= &= ^= |=
              assignment
       expr1 , expr2
              comma
```
for example
```
echo $((17*3))
``` prints the answer, 51

---

### Post by trent.josephsen on 2012-01-14
I'd use bc:

```
% echo 'sqrt(225)' | bc -l
15.00000000000000000000

% echo 'scale=0;sqrt(225)' | bc -l 
15
```

---

### Post by WasMeHere on 2012-01-14
Hi again,

I got curious and found bc
[[COLOR="RoyalBlue"]_http://www.basicallytech.com/blog/index.php?/archives/23-command-line-calculations-using-bc.html_[/COLOR]]("http://www.basicallytech.com/blog/index.php?/archives/23-command-line-calculations-using-bc.html")

In the examples the number of decimals differ:
```
echo 'scale=30;sqrt(2)' | bc
1.414213562373095048801688724209
'scale=4;sqrt(2)' | bc
1.4142
```

Maybe bc fits you better than octave

Good luck
Olle

*Edit: so +1 for Trents' suggestion*

---

### Post by sisco311 on 2012-01-14
BASH's builtin arithmetic uses integers only. For operations involving floating point numbers, you have to use an external application, like bc, dc, awk, calc... See BashFAQ 022 (link in my signature).

---

### Post by achuth on 2012-01-14
> **trent.josephsen said:**
> I'd use bc:

```
% echo 'sqrt(225)' | bc -l
15.00000000000000000000

% echo 'scale=0;sqrt(225)' | bc -l 
15
```

What is that bc?
I mean what does **b** and **c** stands for?

---

### Post by trent.josephsen on 2012-01-15
bc is one of those commands that has been around so long nobody bothers to remember what it might have once been an abbreviation for.  I had to look it up.

---

