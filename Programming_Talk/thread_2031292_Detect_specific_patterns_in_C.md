---
title: "Detect specific patterns in C"
date: 2012-07-21
forum: Programming Talk
---

### Post by vikkyhacks on 2012-07-21
I have this huge problem.

char *a="asdasd75erbfv87xxcvb**int**as**float**87xzjhbxcv**double**"

how do i search and display specific patterns( float int double (in bold)) from that string a. ????

---

### Post by MadCow108 on 2012-07-21
regular expressions are often a good way to find patterns in text:
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)
[http://www.gnu.org/software/libc/manual/html_node/Regular-Expressions.html](http://www.gnu.org/software/libc/manual/html_node/Regular-Expressions.html)

though if your pattern is so specific you may be better of just using *strstr*

---

### Post by Bachstelze on 2012-07-21
C is not the right language to do text-related stuff.

---

### Post by vikkyhacks on 2012-07-22
Thanks fr t reply bt i need to get my prgm wrking in both linux and turbo c++, that regexp header is not available in Turbo c++

---

### Post by lisati on 2012-07-22
It might be an idea to start with something like the previously mentioned [strstr]("http://www.codecogs.com/reference/computing/c/string.h/strstr.php").

Which language are you primarily using, C or C++?

---

### Post by codemaniac on 2012-07-22
As mentioned by Bachstelze , C might not be the best choice to do text manipulation .

By combining several small, but powerful, text processing tools through UNIX pipes, text can be transformed and manipulated in a myriad of ways and can save you hundreds of lines of C code .

---

