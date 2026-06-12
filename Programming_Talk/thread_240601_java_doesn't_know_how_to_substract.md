---
title: "java doesn't know how to substract"
date: 2006-08-21
forum: Programming Talk
---

### Post by newen on 2006-08-21
Try this and tell me what u get.
      
```
double result= 1.03-.42;
double wrongResult = .61-result;
if (wrongResult != 0.0)
    System.out.println(wrongResult);
```

Is this a java precision bug?

---

### Post by Cryonic on 2006-08-21
It's not, it's a feature ;)
If you read the docs at Sun

[http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html)

it says:

> double: The double data type is a double-precision 64-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in section 4.2.3 of the Java Language Specification. For decimal values, this data type is generally the default choice. As mentioned above, **this data type should never be used for precise values**, such as currency.

for your example, use the float type instead:

```

float result= 1.03f-.42f;
float wrongResult = .61f-result;
if (wrongResult != 0.0)
    System.out.println(wrongResult);

```

---

### Post by LordHunter317 on 2006-08-21
Umm, float is also a IEEE-754 floating point value, just of less precision.

Read: [http://docs.sun.com/source/806-3568/ncg_goldberg.html](http://docs.sun.com/source/806-3568/ncg_goldberg.html) and note it's probably one of the only pieces of really good documentation Sun has ever written.

---

### Post by newen on 2006-08-21
BigDecimal does neither give correct results. Try it, it's even worse than double!.

---

### Post by LordHunter317 on 2006-08-21
If you used it the way I think you did, then of course it doesn't give correct results, because it can't.

***Did you read the document above?  Until you do, please do not post anymore on this subject.***

Don't post about BigDecimal either until you read it's documentation carefully.  Especially if you're using the Java 5 version, which provides a lot of complicated rounding and precision support.

---

### Post by yaaarrrgg on 2006-08-21
I think you should generally avoid equality comparisons on floats and doubles in any langauge.  consider this:

```

clearly:
              1/3 + 1/3 + 1/3 = 1
and 
              .333... + .333... + .333... = .999...
note:
              1/3 == .333...
therefore:
              .999... == 1

```

This has nothing to do with precision erros.  The result is actually true.

---

### Post by LordHunter317 on 2006-08-21
> **yaaarrrgg said:**
> I think you should generally avoid equality comparisons on floats and doubles in any langauge.Yes, but not for the reason you state.  1/3 is **not equal** to .333.  It's **about** equal to .333.  It is equal to .3 infinitely repeating.

That difference is subtle, but fundamentally important, especially when dealing with fixed-precision systems.

This is why we deal with rationals in a special way if we need arbitrary percision, normally.

---

### Post by LordHunter317 on 2006-08-21
I see now I think you're saying the same thing as I was.  Was the '...' meant to mean infinitely repeating?

Anyway, like I said, if this is a problem, you deal with rationals specially.  Otherwise, you accept the small error and get on with life.  

But that's still not a good reason to not do equality on IEEE-754 floating-point values.  The fact they can't represent every value is reason enough.  Anything else is a strawman ultimately.

---

### Post by Cryonic on 2006-08-21
> **LordHunter317 said:**
> Umm, float is also a IEEE-754 floating point value, just of less precision.

Read: [http://docs.sun.com/source/806-3568/ncg_goldberg.html](http://docs.sun.com/source/806-3568/ncg_goldberg.html) and note it's probably one of the only pieces of really good documentation Sun has ever written.

You're totally right, I was reading carelessly. 
And thanks for the link, it's a good read! :)

---

### Post by yaaarrrgg on 2006-08-21
> **LordHunter317 said:**
> I see now I think you're saying the same thing as I was.  Was the '...' meant to mean infinitely repeating?

Yes... my fault for not being clear.  

I thought the OP was assuming that more precision would fix the problem.

But even with infinite precision, there's still difficulties with strict equality comparisons on real numbers.  At bottom, I think a '=' relation between two reals must be interpreted as a more verbose relation involving '<', '>' and arbitrarily small errors.   I'm not sure the idea of strict equality between two reals even makes logical sense (unless they can be pre-converted into fractions).

---

