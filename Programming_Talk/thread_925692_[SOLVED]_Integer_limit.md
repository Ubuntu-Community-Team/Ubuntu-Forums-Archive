---
title: "[SOLVED] Integer limit??"
date: 2008-09-20
forum: Programming Talk
---

### Post by jesushero on 2008-09-20
Ok, this is a pretty stupid question... But why is the maximum integer value that bash can handle 9223372036854775807? Is that signed or not?

What happens in cases of floating point numbers? 

Is there a way around this in bash?

When it wraps, in 9223372036854775807 + 1, it goes to -9223372036854775808.. How is this possible and 9223372036854775808 is not?

```
user@machine:~$ a=9223372036854775807
user@machine:~$ echo $a
9223372036854775807
user@machine:~$ let a++
user@machine:~$ echo $a
-9223372036854775808
user@machine:~$ let a++
user@machine:~$ echo $a
-9223372036854775807

```

---

### Post by ghostdog74 on 2008-09-20
it depends on your machine. bash performs maths in the largest integer size your machine supports (intmax_t).

---

### Post by unutbu on 2008-09-20
According to [http://en.wikipedia.org/wiki/Integer_(computer_science](http://en.wikipedia.org/wiki/Integer_(computer_science))
a 64-bit signed long int has the range you describe.
(See also /usr/include/limits.h). It seems likely based on this that bash implements integers as 64-bit signed long ints.

You can see by looking at the Two's complement chart ([http://en.wikipedia.org/wiki/Signed_number_representations](http://en.wikipedia.org/wiki/Signed_number_representations)) that the Two's complement interpretation of 

0111...111  is 9223372036854775807, and
1000...000  is -9223372036854775808

---

### Post by mssever on 2008-09-20
> **jesushero said:**
> Is there a way around this in bash?
Store numbers as strings and use bc for math: ```
~:$ a=9223372036854775807
~:$ ((b = $a + 1))
~:$ echo $b
-9223372036854775808
~:$  echo $a + 1 | bc
9223372036854775808
```(Bash can't handle floating point numbers at all, so you have to use something like bc for that.

---

### Post by slavik on 2008-09-21
I would say that if you are using a two digit number in a bash script, you need to rethink your design (unless this is for educational purpose, then there are exceptions).

---

### Post by mssever on 2008-09-21
> **slavik said:**
> I would say that if you are using a two digit number in a bash script, you need to rethink your design (unless this is for educational purpose, then there are exceptions).
Wait. A two digit number is a sign of bad design? Huh?

---

### Post by jesushero on 2008-09-21
> **slavik said:**
> I would say that if you are using a two digit number in a bash script, you need to rethink your design (unless this is for educational purpose, then there are exceptions).

Would you recommend Python or Perl for scripting then? Or something else? I use bash if I need to use a lot of system commands and little else.

---

### Post by ghostdog74 on 2008-09-21
what other things do you want to do , beside the calculation? 
```

awk 'BEGIN{printf "%.2f", 9223372036854775807 + 1}'

```

---

### Post by mssever on 2008-09-21
> **jesushero said:**
> Would you recommend Python or Perl for scripting then? Or something else? I use bash if I need to use a lot of system commands and little else.
See this thread: [http://ubuntuforums.org/showthread.php?t=910779](http://ubuntuforums.org/showthread.php?t=910779)

---

### Post by slavik on 2008-09-21
> **mssever said:**
> Wait. A two digit number is a sign of bad design? Huh?
You're changing my words and misunderstanding the point. Please re-read my post.

---

### Post by pmasiar on 2008-09-22
> **slavik said:**
> You're changing my words and misunderstanding the point. Please re-read my post.

I did read it again and I am no wiser. How are two digits related to anything? Some background info maybe?

BTW, OP: see wiki in my sig for links to learn Python (excellent as replacement of bash, with unlimited size integers when you need them), including training tasks.

---

### Post by slavik on 2008-09-22
> **pmasiar said:**
> I did read it again and I am no wiser. How are two digits related to anything? Some background info maybe?

BTW, OP: see wiki in my sig for links to learn Python (excellent as replacement of bash, with unlimited size integers when you need them), including training tasks.
There's a reason the basic datatype in a shell is a string. Shells aren't intended to perform mathematical calculations even if they can.

---

### Post by ghostdog74 on 2008-09-22
> **slavik said:**
> There's a reason the basic datatype in a shell is a string. Shells aren't intended to perform mathematical calculations even if they can.

some shells, like zsh, or ksh99, can perform floating point, eg zsh
```

# echo $(( 1.0 / 2.0 ))
0.5

```
otherwise,  standard utility for the shell is to use bc, or dc.

---

