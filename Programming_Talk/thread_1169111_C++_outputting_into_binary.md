---
title: "C++ outputting into binary"
date: 2009-05-24
forum: Programming Talk
---

### Post by izint on 2009-05-24
I need some help in changing unsigned int and a string of 0s and 1s into binary. I need to cout unsigned ints into binary of 4bytes each. Something about using static_cast or dynamic_cast but I've never used it so I'm not sure. Another thing I need to do is cout a string of 0s and 1s into binary. If it is less than 8 bits in length add the correct number of 0s to the end and reverse. I know how to do that part, but I am not sure of how to cout it in binary as 1 byte? Any help would be appreciated. Thanks

---

### Post by dwhitney67 on 2009-05-24
This forum is not the proper place to be asking questions concerning your homework problems.

Before you zip off on a tangent, do not look into static_cast nor dynamic_cast for your solution; they have nothing to do with it.

All data values that are stored by a computer are stored in binary; thus when outputting binary format using cout, it is merely up to the programmer to take the value and output a series of 1's and 0's that represent the value.

So, if you were to take the value, and examine its left-most bit, what do you have?  There are only two possibilities:  a 0 or a 1.  Repeat this exercise for the remaining 31 bits, going from left to right.

Hint:  Define/use a mask to isolate an individual bit of the value.

With the string, I presume you mean either an STL string or a const char*.  In either case, just get the length of the string to determine if it is a multiple of 8 bits.  If it is not, then determine how many bits you have vs. how many you need.  So if your string is "00100", then you have 5 bits; thus missing 3 to make a total of 8 bits.  In this case, output 3 zeroes, then each of the bits of the string.

---

