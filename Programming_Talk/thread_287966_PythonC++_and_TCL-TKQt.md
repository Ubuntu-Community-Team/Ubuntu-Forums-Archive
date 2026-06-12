---
title: "Python/C++ and TCL-TK/Qt"
date: 2006-10-29
forum: Programming Talk
---

### Post by sherlock-holmes on 2006-10-29
Hello poeple,

I am planning to modify my codes from Matlab to C++, Python or Fortran. I am on the lookout for some advise here...My code is computationally intensive and includes hell of a lot of matrices and functions...

The reason i am planning to move is that  i need to generate a customizable GUI for specific user inputs at various stages of the code including variable inputs, conditions, limits, and even different optimization schemes with 'several' objective functions...

what is the best combination i could use to acheive this... patience and willingness to learn and facilities are not matters of concern here...

I was told to use (by different classmates-experts in diff things)
1. Fortran + TCL/TK...
2. C++ and Qt3/4
3. Matlab + its built-in GUI (probably the easiest)
4. Python + Numpy, Scipy, + bells and whistles
5. others? 

I have used matlab + builtin GUI stuff...But  didnt find that that interesting. It doesnt have the flexibility/intuitiveness of a good GUI platform.

SOS !

---

### Post by amo-ej1 on 2006-10-29
Hello,

since you code is computationally intensive and relies very hard on  matrix manipulations you will probably need to rely on many other mathematical functions. Personally I'd stick to matlab (since matlab was made for just that). 
If matlab turns out to be too slow and reimplementing/learning a library isn't too much work you might want to switch to a compiled language, here c/c++ would be my personal choice. If you want to migrate away from matlab, simply pick the language you feel most comfortable in. personally i think it will be easier to get some support for c/c++ and python than for fortran.

---

### Post by sherlock-holmes on 2006-10-29
> **amo-ej1 said:**
> Hello,

since you code is computationally intensive and relies very hard on  matrix manipulations you will probably need to rely on many other mathematical functions. Personally I'd stick to matlab (since matlab was made for just that). 
If matlab turns out to be too slow and reimplementing/learning a library isn't too much work you might want to switch to a compiled language, here c/c++ would be my personal choice. If you want to migrate away from matlab, simply pick the language you feel most comfortable in. personally i think it will be easier to get some support for c/c++ and python than for fortran.

Thank you for your response. yes i was planning to migrate from matlab. The idea is to have a versatile GUI program implemented through my source code. I read that the combinations, Python/tk or python/wxpython are great. 
I would really appreciate comments from people who have already familier with them....thanks again

---

