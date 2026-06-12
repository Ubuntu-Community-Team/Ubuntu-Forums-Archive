---
title: "Java - BigInt Sqrt?"
date: 2009-11-19
forum: Programming Talk
---

### Post by travmanx on 2009-11-19
I am doing some code for a problem at Project Euler. I have been doing all my code via Java, but if C++ will be easier, I may have to take that approach for this one. 

My problem is whilst using a BigInteger. I've only ever used it maybe 15 times in my Java life, and it was for simple homework stuff. Is there a simple way to take the square root of this monster(I have everything else figured out...)? Or should I use a user made function to work with this? If so, can anyone point me to one or atleast an algorithm that will work in this case with a number this massive.

I don't want answers, just which is the best way....

Edit: It has to not auto round...

Edit 2: Nevermind, Ive found my solution

```
BigInteger sqrt(BigInteger n) {
  BigInteger a = BigInteger.ONE;
  BigInteger b = new BigInteger(n.shiftRight(5).add(new BigInteger("8")).toString());
  while(b.compareTo(a) >= 0) {
    BigInteger mid = new BigInteger(a.add(b).shiftRight(1).toString());
    if(mid.multiply(mid).compareTo(n) > 0) b = mid.subtract(BigInteger.ONE);
    else a = mid.add(BigInteger.ONE);
  }
  return a.subtract(BigInteger.ONE);
}
```

Thanks to Faruk Akgul: Java's missing Algorithm

---

### Post by iruel on 2009-11-19
perhaps it's help
```
BigInteger sqrt(BigInteger n)
{
	Double d=Math.sqrt(n.doubleValue());
	n=BigInteger.valueOf(d.longValue());
	return n;
}
```

---

### Post by Arndt on 2009-11-20
> **travmanx said:**
> I am doing some code for a problem at Project Euler. I have been doing all my code via Java, but if C++ will be easier, I may have to take that approach for this one. 

My problem is whilst using a BigInteger. I've only ever used it maybe 15 times in my Java life, and it was for simple homework stuff. Is there a simple way to take the square root of this monster(I have everything else figured out...)? Or should I use a user made function to work with this? If so, can anyone point me to one or atleast an algorithm that will work in this case with a number this massive.

I don't want answers, just which is the best way....

Edit: It has to not auto round...

Edit 2: Nevermind, Ive found my solution

```
BigInteger sqrt(BigInteger n) {
  BigInteger a = BigInteger.ONE;
  BigInteger b = new BigInteger(n.shiftRight(5).add(new BigInteger("8")).toString());
  while(b.compareTo(a) >= 0) {
    BigInteger mid = new BigInteger(a.add(b).shiftRight(1).toString());
    if(mid.multiply(mid).compareTo(n) > 0) b = mid.subtract(BigInteger.ONE);
    else a = mid.add(BigInteger.ONE);
  }
  return a.subtract(BigInteger.ONE);
}
```

Thanks to Faruk Akgul: Java's missing Algorithm

Here's another one, which probably uses fewer iterations, but uses division: [http://www.merriampark.com/bigsqrt.htm](http://www.merriampark.com/bigsqrt.htm).

---

### Post by Arndt on 2009-11-20
> **iruel said:**
> perhaps it's help
```
BigInteger sqrt(BigInteger n)
{
	Double d=Math.sqrt(n.doubleValue());
	n=BigInteger.valueOf(d.longValue());
	return n;
}
```

I think the result must be exact up to the decimal part. Using Double you only have a limited number of digits. For example, if you put in 43674617461746127*43674617461746127, you want to get 43674617461746127 back.

---

### Post by iruel on 2009-11-20
> **Arndt said:**
> I think the result must be exact up to the decimal part. Using Double you only have a limited number of digits. For example, if you put in 43674617461746127*43674617461746127, you want to get 43674617461746127 back.
its different, the sample from my reply using **BigInteger** not **BigDecimal**;)

---

### Post by Arndt on 2009-11-20
> **iruel said:**
> its different, the sample from my reply using **BigInteger** not **BigDecimal**;)

No one has mentioned BigDecimal. Did you run the code yourself?

---

