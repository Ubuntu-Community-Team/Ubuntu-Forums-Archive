---
title: "Factorials in Java: Integer value larger than a long"
date: 2011-08-16
forum: Programming Talk
---

### Post by akand074 on 2011-08-16
Hey, I was calculating factorials in java for use in calculating combinations/permutations but the application would crash at anything over like 17. I tried using a float instead because they support larger values but I'd rather not have to cut off the decimal place every time and it doesn't even get that large. I tried a permutation/combination for a set size of 50 and it returned NaN.

My question is, is there an **integer **type value that can get to really large numbers? Otherwise is there any type value that can reach very large numbers? I mean, the overall value after the division of multiple factorials doesn't end up that large. It's just in the middle steps you can get extremely large values before they are divided.

---

### Post by cgroza on 2011-08-16
Java has a Bignum class that can hold large values.
[http://web.cs.mun.ca/~michael/java/jdk1.1-beta2-docs/api/java.lang.Bignum.html](http://web.cs.mun.ca/~michael/java/jdk1.1-beta2-docs/api/java.lang.Bignum.html)

---

### Post by akand074 on 2011-08-18
Bignum doesn't seem to exist in Java.lang like it states it should. I've tried BigInteger but it seems too convoluted and not the best choice for a simple factorial method.

---

### Post by Bachstelze on 2011-08-18
BigInteger is the standard Java way. Other libraris to implement arbitrary-precision integers exist [http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Libraries](http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Libraries)

---

### Post by akand074 on 2011-08-18
> **Bachstelze said:**
> BigInteger is the standard Java way. Other libraris to implement arbitrary-precision integers exist [http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Libraries](http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Libraries)

I just don't particularly understand how to use BigIntegers. It doesn't seem to allow you to input values, all of it's methods are return methods. Some which let you add values to it's stored value then returns it. How could I go about using a BigInteger to calculate a factorial?

---

### Post by unknownPoster on 2011-08-18
> **akand074 said:**
> I just don't particularly understand how to use BigIntegers. It doesn't seem to allow you to input values, all of it's methods are return methods. Some which let you add values to it's stored value then returns it. How could I go about using a BigInteger to calculate a factorial?

Pass your desired number to the BigInteger constructor.

---

### Post by akand074 on 2011-08-18
> **unknownPoster said:**
> Pass your desired number to the BigInteger constructor.

Oh I'm just reading up a bit more. Would I just have to pass it as a String? Because it didn't have any constructor set up for any int/long type value. So I guess I'll just send it as a String. I'll give that a try.

---

### Post by Queue29 on 2011-08-18
> **akand074 said:**
> Oh I'm just reading up a bit more. Would I just have to pass it as a String? Because it didn't have any constructor set up for any int/long type value. So I guess I'll just send it as a String. I'll give that a try.

Yep, the public constructor only takes a String. Technically there is another constructor that takes a long, but it's private. :(

---

### Post by Bachstelze on 2011-08-18
[http://download.oracle.com/javase/6/docs/api/java/math/BigInteger.html#BigInteger%28java.lang.String%29](http://download.oracle.com/javase/6/docs/api/java/math/BigInteger.html#BigInteger%28java.lang.String%29)

Passing a string works. Obviously you can't pass an int or a long since the value you want can't be represented as one. Another way is to use BigInteger.TEN and BigInteger.ONE. For example, to have the value 10^120 as a BigInteger:

```

BigInteger foo = BigInteger.ONE;
for (int i=0; i<120; i++) {
    foo = foo.multiply(BigInteger.TEN);
}
```

And so on for other digits.

---

### Post by akand074 on 2011-08-18
Okay so that actually seemed to work and fixed that problem. Though how come I find that every time I fix one thing I break two others. Basically I had to change everything in the methods calling factorial to use a BigInteger, which worked fine when everything was a BigInteger. Seems to be causing me problems when I'm multiplying/dividing by doubles and such even though I converted the BigInteger to a double. Does anyone see anything wrong with either of these?

```
public static double calcProbability(int x, int n, double p) {
        return Factorial.calcFactorial(n).divide(
                Factorial.calcFactorial(x).multiply(
                        Factorial.calcFactorial(n - x))).doubleValue()
                * Math.pow(p, x) * Math.pow(1 - p, n - x);
    }
``````
public static double calcProbability(int x, double lambda) {
        return new BigDecimal(String.valueOf((Math.pow(lambda, x) * Math.pow(
                Math.E, lambda * -1)))).divide(
                new BigDecimal((Factorial.calcFactorial(x)))).doubleValue();
    }
```

---

### Post by Bachstelze on 2011-08-18
> **akand074 said:**
> Does anyone see anything wrong with either of these?


Yes, your lines are way too long.

---

### Post by akand074 on 2011-08-18
> **Bachstelze said:**
> Yes, your lines are way too long.

hahahaha other than that!! I tend to format them after they are working. Perhaps I should get in the habit of doing it as I go.

Happy now? I edited it :P

EDIT: I don't think there is anything wrong with those two lines of code.. must be it's interaction with other parts. If anyone notices anything wrong though you can point it out, otherwise I'll mark this thread as solved! Thanks for the help!

---

