---
title: "Optimization in python or C"
date: 2007-11-21
forum: Programming Talk
---

### Post by aquavitae on 2007-11-21
I've just written a script in python which performs some calculations on each line of a text file containing delimited data.  The trouble is the file can contain about 10 million lines, which equates to a running time of about 3hrs on a slow pc (which is where it will probably be running). I profiled the script to get that figure.  As I see it there are two options - try to improve the python code to get it to run faster or rewrite it in C.  

Assuming I've reduced the number of loops and recursions to a minimum, the questions are:
1)  How much of a relative speed increase am I likely to get by using generators, built-in types only, and inline code rather than functions?
2)  Am I likely to get a significant speed increase in C?

I suspect the python lists are not nearly as fast as C arrays, so I might get an increase, but I'd like some advice before I rewrite it.

---

### Post by samjh on 2007-11-21
In my own experience, Python lists are around 200 times slower than C arrays.  So you probably will achieve very great speed increases using C arrays, as long as the implementation is reasonably efficient.

For your situation with a 10,000,000-line file, you're probably going to run into integer overflow problems if each line is contained within an array element.  Beware of this if you're using C, and plan on splitting up the data into multiple arrays.  It's a non-issue with Python, however, since Python has built-in support for extremely long integers.  But the price of Python's ease of use is its lack of speed.  The decision is only yours to make: Python's ease of use but slow speed, or C's difficulty and execution efficiency?

---

### Post by aquavitae on 2007-11-21
Thanks for the info.  

How long is a C unsigned long int - I though it was either 4 or 8 bytes depending on architecture?  4b is about 4.3e9 - plenty if I need 1e7.

I think I've optimized the implementation as much as possible and I've only managed to reduce the time by about 25% so I might do it in C.  Its starting to look a bit like C code anyway - e.g. keeping track of list sizes separately to reduce len() calls!

---

### Post by smartbei on 2007-11-21
Well, unsigned int is 32bits (4 bytes), that sounds like it will do.

If I am not mistaken on 32bit architectures the long is actually an int. If you need it longer you use long long.

---

### Post by aquavitae on 2007-11-21
> **smartbei said:**
> Well, unsigned int is 32bits (4 bytes), that sounds like it will do.

If I am not mistaken on 32bit architectures the long is actually an int. If you need it longer you use long long.Yes, just found that out from google too.  I don't think that will really be a problem - the problem is trying to remember how to code C array, and remembering those damn semicolons!

---

### Post by CptPicard on 2007-11-21
Well.. it depends on your algorithm. What are you doing to your data? Are you being linear in the size of your list... so you just go through the list once, do something pretty simple, and then move on? In that case you probably won't gain much from optimizing your Python code, and need to move to C.

On the other hand, if your algorithm is just plain slow, then it might not be necessary yet...

---

### Post by aquavitae on 2007-11-22
> **CptPicard said:**
> Well.. it depends on your algorithm. What are you doing to your data? Are you being linear in the size of your list... so you just go through the list once, do something pretty simple, and then move on? In that case you probably won't gain much from optimizing your Python code, and need to move to C.

On the other hand, if your algorithm is just plain slow, then it might not be necessary yet...
Are you saying that iterating through a python list is not much slower than iterating through a python array?  I have to go through the list a couple of times.  The purpose of the algorithm is to read values logged against time from a file, interpolate between them to get a constant frequency, then run a fast fourier transform.  I haven't looked at the fft yet - originally it wasn't part of the script, but it makes sense to put it in now ratehr than export the data to a separate file which then has to be re-read by another program.  So (before the fft) that's 3 loops - one to read the data, one to find the optimum frequency, and one to calculate the interpolated values.... Ok, looking at the code again, I think I've got a few more loops than that!  And I should be able to combine the first two anyway. Looks like I've found a place to optimize!

---

### Post by CptPicard on 2007-11-22
If your loops are one after the other, you're still being linear in the size of input :)

But anyway, if you're feeling the heat already for a low multiplier of your n, you'd probably be better off with C as your FFT is going to be O(n log n) and will have bigger constants...

---

### Post by aquavitae on 2007-11-22
I'm hoping the fft algorithmns in numpy will already be optimized in C...  Btw, does anyone know if there's a function in numpy to reduce the data to equal time intervals like I need to do?

---

