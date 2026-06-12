---
title: "Python vs C"
date: 2012-02-10
forum: Programming Talk
---

### Post by AkiraBergman on 2012-02-10
I am trying to make a Ulam Spiral which involves looking up two very large arrays (in the order order of many millions) of numbers for the iteration of the elements of a very large matrix. I have sorted the arrays and optimized the searching, but it still takes too long. I am doing this in Python.

How much speed increase can I expect if I use C++  ?

---

### Post by squenson on 2012-02-10
It is difficult to answer your question as the result may vary.

If you mainly use the native Python objects (lists, sets, etc) and their core methods, they are very efficient and the gain in C or C++ will be in the range of 10% max, in my opinion. On the other hand, if you have a lot of lines of code, do repetitive mathematical operations implying casting of numbers, then the performance may be 3 to 10 times better in C or C++.

When dealing with prime numbers, you may consider building a very large list with all the prime numbers within a range and then search this list instead of verifying whether a number is prime with mathematical calculations.

---

### Post by AkiraBergman on 2012-02-10
Thank you for the reply. I have already done the building of the primes into an array for searching. I took the prime list from the web so I don't spend time with these. I have another small array of corner numbers to build the square spiral.

So there may be no big gains with C++. I will build a smaller spiral and do further work on that, using Python. Maybe later I will shift to C++.

---

### Post by sisco311 on 2012-02-10
Interesting question. :)

Thread moved to **Programming Talk**.

---

### Post by JDShu on 2012-02-10
Out of curiosity, are you using scipy or numpy? If you aren't, perhaps you could try using one of those libraries. Another option might be to run what you have using pypy.

---

### Post by AkiraBergman on 2012-02-10
Thanks, pypy is worth trying. Yes I am using numpy. 

I realized that I made a mistake in the use of the arrays. I will try and synchronize the arrays with the matrix, by walking them together only once, since they are sorted. That should increase the speed quite a bit and open the way to a very large matrix, perhaps 50-10M.

I will keep you posted if interested.

---

### Post by MadCow108 on 2012-02-11
in general if you use numpy/scipy correctly and your problem is not to complicated (e.g. it can be reduced to a bunch of blas routines) you will not gain very much by changing to C. In cases where you do you could use scipy.weave to add in inline C code.

PyPy is indeed an option you should consider, especially when the logic is non-trivial and dependend on how the data looks like at runtime. Unfortunatly the numerical support (numpypy) is still quite basic (but improving fast)

you can also plug in a better linear algebra package into numpy/scipy.
e.g. a machine optimized atlas can gain you quite some performance (+ "automatic" parallizing of your code) when you use a bunch of blas level 3 routines.

(the atlas in the ubuntu repositories is only optimized for i386/amd64 nothing more, see the readme on instructions to optimize it further to your machine)

---

### Post by stchman on 2012-02-11
I am no Python expert, but from what I understand all the really computation intensive tasks have a library already written in C.  Also what I've read is that Python is much too slow for heavy computation so it uses C code to do all the heavy lifting.

---

