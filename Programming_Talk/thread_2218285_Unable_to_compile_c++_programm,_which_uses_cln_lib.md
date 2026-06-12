---
title: "Unable to compile c++ programm, which uses cln library."
date: 2014-04-20
forum: Programming Talk
---

### Post by leftwin on 2014-04-20
Hello to everybody!
I wrote a simple programm for my school project, but when I'm trying to compile it on my PC with Ubuntu 14.04 :
> 
g++ -lcln -o ferma ferma.cpp

I get errors:
[http://bpaste.net/show/218812/](http://bpaste.net/show/218812/)

I suppose that there is no errors in my programm, because It succesfully compiles on my PC with gentoo.

And here is my code:
[http://bpaste.net/show/218813/](http://bpaste.net/show/218813/)

I have got gcc 4.8.2 and libcln6 installed. Also I tried installing that library from source code.

---

### Post by dwhitney67 on 2014-04-20
Specify the library that you wish to link against last, not first, in your g++ statement.  For example:
```

g++ -o ferma ferma.cpp -lcln

```

---

### Post by leftwin on 2014-04-20
Thank you a lot! I'm wondering why does it compile on gentoo machine.

---

