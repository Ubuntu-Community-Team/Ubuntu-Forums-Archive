---
title: "Java, log of a BigInteger"
date: 2010-04-24
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-24
Hi guys,

Annoyingly, there is no Java function to calculate the log (to ANY base) of a BigInteger.  I have found a way to calculate the *ceiling* of the log (base 2) of a BigInteger (by taking the bitLength), but I now need a more exact answer -- I need to square the logarithm, so if I take the ceiling of it before squaring there will be some inaccuracy (for logs with the decimal part between 0.0...01 and 0.499...99).

I have been looking around online and a common solution seems to be to convert the BigInteger to a string and calculate the length of it, but apparently this is a very rough estimation of log base 10.

So does anyone know how I can do this sufficiently accurately?  It does not need to be exact (indeed, exact precision is probably impossible with BigIntegers) but I need to be accurate enough so that when I square the logarithm, and then take the floor of this, I get what I expect.

(Note, as I said, I can use a logarithm to any base since the change of base rule will give me a logarithm to the base I want)

Thanks very much

---

### Post by Lux Perpetua on 2010-04-24
The great thing about logarithms is how well they scale. I'm going to use base-ten logs for ease of exposition, but you can use any base. 

Let N = 58577342649717622264566499455. Note that N = (10^29)*(0.58577342649717622264566499455) = (10^29)*X, where X is the long decimal. Thus, log_10(N) = log_10(10^29*X) = 29 + log_10(X). Now X is just a number between 0 and 1, so you can compute its logarithm the normal way, using the standard library. (Obviously, you don't need all 29 digits; just chop it off somewhere and save it as a double.)

---

### Post by mcweaver1 on 2010-04-24
Wow, that's an ingenious way of doing this, hadn't thought of that! Nice one, thanks very much :D

---

### Post by breaddawson on 2011-07-10
I thing BigInteger.toString(radix) will help you on this.

---

