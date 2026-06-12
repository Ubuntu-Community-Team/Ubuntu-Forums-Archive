---
title: "Java, number of digits in BigInteger"
date: 2010-04-24
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-24
Hello, me again....

Now I need to calculate the number of digits in a BigInteger.  I thought of doing this by converting it to a string and then finding the length of that; however this is returned as an int (using .length()) and so it may well be the case that there are more digits in the BigInteger than the int can represent. (Am I right in thinking this?  If not then this solves my problem.)

I know I could do this by having a counter and going through each digit in the BigInteger adding to the counter as I go, but if the BigInteger is large then this would be really inefficient.

I could also put the digits in an array and find out the index of the last digit, but this could take a lot of memory....

Any suggestions?  Apologies for the number of questions on BigIntegers, never really programmd with them before.

Thanks in advance

---

### Post by NovaAesa on 2010-04-25
Why not try dividing the number by 10 as many times as you can? The number of times you can divide by 10 before the number is less that 10 will be the number of digits (radix 10) - 1.

---

### Post by Lux Perpetua on 2010-04-25
> **mcweaver1 said:**
> Hello, me again....

Now I need to calculate the number of digits in a BigInteger.  I thought of doing this by converting it to a string and then finding the length of that; however this is returned as an int (using .length()) and so it may well be the case that there are more digits in the BigInteger than the int can represent. (Am I right in thinking this?  If not then this solves my problem.)Seriously, now, are your BigIntegers going to have 2^31 digits or more? That's more than two billion.

---

### Post by mcweaver1 on 2010-04-25
> **Lux Perpetua said:**
> Seriously, now, are your BigIntegers going to have 2^31 digits or more? That's more than two billion.

Ah.... Well I'm writing an implementation of the AKS primality test (although now I've come to the final stage of the algorithm, which requires computations involving polynomials, I'm thinking it would have been a much better idea to do this is Matlab...) - so I was trying to write the program so that no accuracy is lost anywhere, since this would stop the test from working.

Although I didn't realise quite how big the non-BigInteger methods are.  Even the largest prime number found so far doesn't quite have 1 billion digits (~12,000,000 in fact).

Thanks very much for all the help :)

---

### Post by Lux Perpetua on 2010-04-25
> **mcweaver1 said:**
> Ah.... Well I'm writing an implementation of the AKS primality test (although now I've come to the final stage of the algorithm, which requires computations involving polynomials, I'm thinking it would have been a much better idea to do this is Matlab...) - so I was trying to write the program so that no accuracy is lost anywhere, since this would stop the test from working.

Although I didn't realise quite how big the non-BigInteger methods are.  Even the largest prime number found so far doesn't quite have 1 billion digits (~12,000,000 in fact).

Thanks very much for all the help :)As a matter of fact, I implemented the AKS primality test in C++ some time ago. As I remember, it was taking on the order of 10-100 seconds to check (prime) numbers with tens of digits, so it would have been completely impractical for something with hundreds or thousands of digits, let alone millions or billions. Maybe you'll do better, but the fact remains that while AKS is polynomial-time in the number of digits, that polynomial has pretty high degree.

---

### Post by soltanis on 2010-04-25
Java strings can be up to 2,147,483,647 characters in length.

Unless your number has more digits than that, your string.length() solution should suffice.

---

