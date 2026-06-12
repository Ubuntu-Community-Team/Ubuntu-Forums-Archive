---
title: "MPFR and IOFormat in C++"
date: 2012-11-09
forum: Programming Talk
---

### Post by Dirich on 2012-11-09
Hello,

I need to format my output to have a specific precision, and since I need to format the output file as 3 columns, I also would like them to be aligned. This means I should normally use this code block:

```

#define COUT_PRECISION 15

cout.precision(COUT_PRECISION);
#ifdef SCIENTIFIC
      cout.setf(ios::scientific,ios::floatfield);
#else
      cout.setf(ios::fixed,ios::floatfield);
#endif

```This doesn't work on the type I need to use: mpreal.
This type is essentially a multiple precision type based on MPFR (I use MPFR++, a wrapper for MPFR, which I included in the tar. The type is defined there).
Also, just in case someone suggest another wrapper or no wrapper at all or something along those lines, I use this stuff with Eigen, and that specific wrapper helps a ton.

In order to compile the code:
1. you need to have installed MPFR, that library installs also GMP which is the other library needed
2. the compile line is: g++ -o run test.cpp mpreal.cpp -lmpfr -lgmp -lstdc++

The program will output on screen and on file. I need it to work on file, but I guess once it works on screen it works on file too, since they are both just streams.

Anyway the problem is that the program executes the orders I gave when I input in the stream a double, but it doesn't when I input an mpreal value:


```

//These are for double inputs
1.666666666666667
1.428571428571429
1.250000000000000
1.111111111111111
1.000000000000000

//These are for mpreal inputs
1.66666666666667
1.42857142857143
1.25
1.11111111111111
1

```How can I get the second block of the output to look alike the first block? In other words, to always write the same number of digits?


P.S.
I can not afford to convert the mpreal to double (mpreal::toDouble() is for this).

---

### Post by Zugzwang on 2012-11-13
There might be a cleaner way to do this, but unless you want to dive into modifying the existing code for MPFR functions, the following workaround should do the trick: stream your numbers not to cout, but to some ostringstream that you constructed beforehand. Then, use the .str() method of the ostringstream to obtain a string representation of your number. You can now analyse the string (e.g., for its length) and add trailing 0s and the like as needed.

---

