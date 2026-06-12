---
title: "Programming test, cout&lt;&lt;i%6"
date: 2007-10-15
forum: Programming Talk
---

### Post by grogger13 on 2007-10-15
For a practice test one of the code lines read cout<<i%6,

I did some practice code and for i=100 the output was 4, for i-50 output is 2, i=25, output is 1, and when i was less then 25 output was zero.

I am so confused on what this % symbol means and can't find it on the internet anywhere.

Also is there a resource i can find a list of things for cout like \n, \t, endl, and all the other cammands like that(not sure what you would call them)

---

### Post by Compyx on 2007-10-15
> **grogger13 said:**
> For a practice test one of the code lines read cout<<i%6,

I did some practice code and for i=100 the output was 4, for i-50 output is 2, i=25, output is 1, and when i was less then 25 output was zero.

I am so confused on what this % symbol means and can't find it on the internet anywhere.

Also is there a resource i can find a list of things for cout like \n, \t, endl, and all the other cammands like that(not sure what you would call them)

I suggest you get a good textbook on C++, like "The C++ Programming Language, 3rd Edition" by Bjarne Stoustrup. The '%' means (in this context) 'modulo'.

The escape sequences like '\n' and '\t' are also explained in any decent textbook.

---

### Post by Siph0n on 2007-10-15
100%6 = 4 because 100/6 has a remainder of 4 (16*6 = 96)
50%6 = 2 because 50/6 has a remainder of 2 (8*6 = 48)
25%6 = 1 because 25/6 has a remainder of 1 (4*6 = 24)

Hope that helps some...

btw: You will probably find the modulus section of a book next to division, multiplication, addition, and subtraction operators :)

---

### Post by grogger13 on 2007-10-15
thanks for the help, i did understand the \n and \t, i was just looking for a list of all similar things like that, but i took the test and it was fine.

---

