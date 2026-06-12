---
title: "calculating LSB in BogoMIPS"
date: 2010-09-05
forum: Programming Talk
---

### Post by jamesbon on 2010-09-05
On the following [link]("http://books.google.com/books?id=Boo57V0IOq0C&pg=PA24&lpg=PA24&dq=loopbit+%3D+loops_per_jiffy&source=bl&ots=pwHxgTVaX9&sig=mmFc_E2o9-xS7Xy-kzYXxTu1-a8&hl=en&ei=_RODTLP9H8bJcdPHpNAL&sa=X&oi=book_result&ct=result&resnum=5&ved=0CCQQ6AEwBA#v=onepage&q=loopbit%20%3D%20loops_per_jiffy&f=false")


Following code  is given
```

loopbit = loops_per_jiffy;
/* Gradually work on the lower-order bits */
while (lps_precision-- && (loopbit >>= 1)) {
loops_per_jiffy |= loopbit;
ticks = jiffies;
while (ticks == jiffies); /* Wait until the start
of the next jiffy */
ticks = jiffies;
/* Delay */
__delay(loops_per_jiffy);

if (jiffies != ticks)
/* longer than 1 tick */
loops_per_jiffy &= ~loopbit;
}

```
I am trying to understand above.
In above code I am not clear with 
```

loops_per_jiffy |= loopbit; 
```
How is OR in above statement 
and
```

loops_per_jiffy &= ~loopbit; 
```
How is AND with Inverse of Number helping to get the desired result.

---

