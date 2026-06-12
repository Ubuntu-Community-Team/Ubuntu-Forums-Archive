---
title: "Perl syntax problem"
date: 2009-09-01
forum: Programming Talk
---

### Post by 6ub8 on 2009-09-01
I'm confused with this line of perl code 
  if ( ! ( $n % 3 && $n % 5 ) )  
Could someone have a explanation?

What that does is only finding the multiple numbers of 3 and 5, like this one here
 if( $n % 3 == 0 or $n % 5 == 0) 

Cheers

---

### Post by DaithiF on 2009-09-01
the expression equates to:
if ( NOT ( number is not a multiple of 3 AND number is not a multiple of 5 ) )

or
NOT ( NOT multiple of 3 AND NOT multiple of 5 )
which cancelling out the double negatives can be boiled down to:
multiple of 3 OR multiple of 5

so as you say, you could have rewritten it as:
if ( $n % 3 == 0 || $n % 5 == 0 )

---

### Post by nvteighen on 2009-09-01
Actually, that's something you can get in all C-like languages.

---

### Post by Arndt on 2009-09-01
> **nvteighen said:**
> Actually, that's something you can get in all C-like languages.

Yes, in them too.

---

### Post by badperson on 2009-09-01
actually, 
isn't the original code:

> if ( ! ( $n % 3 && $n % 5 ) ) 

 looking for a number that is not divisible by both 3 and 5? 

the code in the response:

> if ( $n % 3 == 0 || $n % 5 == 0 )
 looks like it will accept a number that is divisible by 3 or 5. 


did I get that wrong?

---

### Post by soltanis on 2009-09-01
No, because if the number is a multiple of 3,

n % 3 = 0

0 is interpreted to mean "false"; therefore, using the not operator, we invert the truth value, and it becomes true.

In this code example, if n is a multiple of 3 OR a multiple of 5, then the result of the inner expression evaluates to 0. !0 is true, so the condition will branch.

Since the response code checks explicitly for the modulus to be 0 (and uses the logical or operator), it does the same thing the original code does.

The original code is more sleight-of-hand, or "clever", relying on the result of an integer operation to yield a boolean truth value, but which usually ends up annoying people trying to read your code. The second code posting is more obvious in its intention and is preferable in use.

---

### Post by DaithiF on 2009-09-01
$n % 3 returns 0 if $n is divisible by 3, and 1 or 2 if not.  So in an if statement where non-zero means true and zero means false, then $n % 3 is false when $n is divisible by 3 and true when $n is not divisible by 3.

yep, bit of a head-spinner.

EDIT: ah, i see i missed the boat -- same reply as soltanis

---

### Post by jpkotta on 2009-09-01
[http://en.wikipedia.org/wiki/Demorgan's_law](http://en.wikipedia.org/wiki/Demorgan's_law)

---

