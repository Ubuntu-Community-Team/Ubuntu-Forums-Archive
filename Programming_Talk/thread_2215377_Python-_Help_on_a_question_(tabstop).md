---
title: "Python- Help on a question (tabstop)"
date: 2014-04-06
forum: Programming Talk
---

### Post by Yozuru on 2014-04-06
So I am doing practice problems I found online for python. The question goes as follow:
 
"Proceed to write a function called detab(string, stop) where string  is any string, and stop is a positive integer called tabstop (size of  it). It should return string, expect that each tab in the string has  been replace with the number of underscores '_'. The only input function  is the arguments, and the only output returns the string that has been  detabbed. Do not use input nor print for this practice problem."

 
I have trouble in starting this code and have look for ways on how to  do this. I am hoping I can get some input from the ubuntul community  about this. Its a rather interesting problem and it would help improve  my proficiency with python. Many thanks in advance.

 
I was thinking of something like:

 string 1 = string 
return string1.expand(stop)

---

### Post by steeldriver on 2014-04-06
Your starting point should be the python string library documentation --> [https://docs.python.org/2/library/string.html](https://docs.python.org/2/library/string.html)

You will also need to think how you can construct the replacement string (a **string** of underscores) programatically from an integer (the **number** of underscores)

---

### Post by Vaphell on 2014-04-06
> You will also need to think how you can construct the replacement string (a string of underscores) programatically from an integer (the number of underscores)

well, luckily for the OP, there is nothing to think about. In python the * operator does that by default

---

### Post by Yozuru on 2014-04-10
Ahh interesting! I forgot about list unpacking. :) Thanks guys.

---

