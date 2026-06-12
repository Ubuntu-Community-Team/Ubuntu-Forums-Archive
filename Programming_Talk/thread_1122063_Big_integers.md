---
title: "Big integers"
date: 2009-04-10
forum: Programming Talk
---

### Post by Zorgoth on 2009-04-10
Is there a standard C++ package for big integers?  I wrote a program for school which works fine in general but given some of the data the assignment calls for doesn't work because it is too big.  It isn't supposed to do this, I suppose my computer must store smaller integers than most.  In any case, I need to be able to handle bigger numbers than I can now.

Thanks in advance!

---

### Post by zolookas on 2009-04-10
Try using **long** or **long long** insead of **int**. If you need even bigger numbers, try using one of bignum libraries (google for bignum c++) (those libraries are 3rd party, not standard).

---

### Post by soltanis on 2009-04-10
Unless you need your integers to have sign (positive or negative), define them as unsigned long or unsigned long long (so that you can use the sign bit to store a number instead of wasting it on a two's complement that you don't need).

unsigned long long = 64 bits on my system, for a maximum value of 0xFFFFFFFFFFFFFFFF or 1.8446 E +19. Your mileage may vary, but if you need larger numbers (arbitrarily large), try the GNU MP (MultiPrecision) Library, a pretty widely supported (and fast) bignum library.

---

### Post by JFASI on 2009-04-10
For large integers, you want to use the GMP library, which supports arbitrarily large integers. It's normally used in C rather than C++, although C++ class bindings are available. 

Here is a link to their website, complete with documentation: 
[http://gmplib.org/](http://gmplib.org/)

And here is a link to the C++ interface: 
[http://os.cqu.edu.au/cgi-bin/info/info2html.cgi?(gmp)C%AB%AB%20Class%20Interface](http://os.cqu.edu.au/cgi-bin/info/info2html.cgi?(gmp)C%AB%AB%20Class%20Interface)

To install, just install : 
```
sudo apt-get install libgmpxx3
```
and the required dependencies *should* fall into place.

---

### Post by samjh on 2009-04-10
> **Zorgoth said:**
> Is there a standard C++ package for big integers?  I wrote a program for school which works fine in general but given some of the data the assignment calls for doesn't work because it is too big.  It isn't supposed to do this, I suppose my computer must store smaller integers than most.  In any case, I need to be able to handle bigger numbers than I can now.

Thanks in advance!

There is no "standard" big integer package for C++, if you're talking about super large integer values with hundreds or more digits.

How big is "big"?  In standard C++, the biggest signed integer is long int, which has a range from-2147483647 to 2147483647.  The long long type is not yet standard C++, but it is supported in some C++ compilers.  If you want something bigger than that, you'll need third-party libraries like GMP (see the post by JFASI above).

---

### Post by Zorgoth on 2009-04-11
Thanks everyone I fixed my program's number problems now.

---

### Post by Arndt on 2009-04-11
> **Zorgoth said:**
> Thanks everyone I fixed my program's number problems now.

If you want to see how big your numbers can be, print out the results of sizeof(int), sizeof(long) and sizeof(long long).

---

### Post by JFASI on 2009-04-12
And to find the largest possible number, just print 2^(sizeof(long long)) etc.

---

