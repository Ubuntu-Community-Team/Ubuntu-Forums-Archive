---
title: "Need help with Factorial algorithm using Python"
date: 2008-09-03
forum: Programming Talk
---

### Post by thornmastr on 2008-09-03
I am using both the THINK PYTHON text and the Challenge-You website to learn Python. I am doing reasonably well and certainly enjoy the available challenges. 

I am currently attempting to work a challrenge known as the 'Zeros of a Factorial' challenge located at [http://www.challenge-you.com/challenge?id=484](http://www.challenge-you.com/challenge?id=484). The actual challenge is as follows: "It can easily be seen that 6! = 720 and has exactly one trailing zero. What is the lowest integer, x, such that x! has 7^20 trailing zeros?"

It does not, on the surface, appear to be a frontal lobe breaker. Design an algorithm to build factorials; count the number of trailing zeros, and the first time we hit it, we have the lowest integer. To test, I computed factorials for 50,000--12,499 trailing zeros,100,000 trailing zeros--24,999, 150,000 trailing zeros 37,498, and finally 200,000 trailing zeros of 49,998.

Obviously, running a test on 1000000 would take some time and would not even be close to the required number of trailing zeros. 

I need to know if I am even close with my approach to a workable algorithm and whatever suggestions you might have to speed up the process so that it would not take hours until it found the correct integer. Any and all suggestions as well as more efficient ways to code the algorithm will be most appreciated.

Please see attached source code.


Robert Berman

---

### Post by pmasiar on 2008-09-03
Did you tried to look at Python Challenge forum hints?

My guess: Zeros can get from multiplies of 2 and 5. 2's are more common, you need 7^20 fives.

---

### Post by thornmastr on 2008-09-03
> **pmasiar said:**
> Did you tried to look at Python Challenge forum hints?

My guess: Zeros can get from multiplies of 2 and 5. 2's are more common, you need 7^20 fives.

Pmasiar,

Thank you for both suggestions. I am not working with the Python Challenge web page. I am using the Challenge you site: [http://challenge-you.appspot.com/](http://challenge-you.appspot.com/) set up by Davy Wybiril.

I will look at the multiples of 2 and 5 suggestions.

Robert Berman

---

