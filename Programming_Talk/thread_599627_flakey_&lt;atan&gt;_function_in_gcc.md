---
title: "flakey &lt;atan&gt; function in gcc ?"
date: 2007-11-01
forum: Programming Talk
---

### Post by nss0000 on 2007-11-01
Gents:

Is it a known issue that gcc exhibits flakey behavior for the function <atan> ?? In the code_fragment below, one of the two <atan> calls always returns the arg_RATIO, rather than atan(arg). Other guy is fine. Swapping order-of-op makes no difference. 

For the weird result O_arg ~ 0.009.  Yes, I know <atan> wants a DOUBLE, but I tried that CAST to no effect.

float getbothrawangles( float aa[], float bb[], float rraw[])
 {
   float  temp; 
     

   rraw[1] = atan( bb[1]/bb[0] );
   rraw[0] = atan( aa[1]/aa[0] ) ;
       
   printf("%f\t%f\t%f\n", aa[1], aa[0], rraw[0] );
   temp = rraw[1] - rraw[0];

  return temp; 
}

---

### Post by LaRoza on 2007-11-01
Try using doubles explicitly. Also, use [ code ] or [ php ] tags when posting code on the forum.

I don't really see what the function is for. Can you give an example of what you want to happen? Give the answer you expect, and the answer given. Sorry, my trig skills have shrunk through disuse.

---

### Post by wolfbone on 2007-11-01
[QUOTE="nss0000"][Is it a known issue that gcc exhibits flakey behavior for the function <atan> ??[/QUOTE]

As LaRoza implies: a) you haven't demonstrated that it (or libc) does and b) your description of your problem is incomprehensible.

[QUOTE="Libc info page"] -- Function: double atan (double X)
 -- Function: float atanf (float X)
 -- Function: long double atanl (long double X)
     These functions compute the arc tangent of X--that is, the value
     whose tangent is X.  The value is in units of radians.
     Mathematically, there are infinitely many such values; the one
     actually returned is the one between `-pi/2' and `pi/2'
     (inclusive).
[/QUOTE]

---

### Post by nss0000 on 2007-11-01
Yes indeed. I had scr*wed-up on an earlier step. Thank you, gents.

---

