---
title: "debug lists in gdb"
date: 2016-04-19
forum: Programming Talk
---

### Post by chuchi on 2016-04-19
Hi there!

I am working with a list l from the STL. In gdb, if I call 'l.front()' I get this message:

```


Cannot evaluate function -- may be inlined


```

Why? I have been surfing the net for ages but found nothing.


This is the output of gdb -v and gcc -v, respectively.

```


GNU gdb (Ubuntu 7.7.1-0ubuntu5~14.04.2) 7.7.1
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.1)


```

And this is the compile instruction:

```


g++ -Wall -g -fno-inline-functions -O0 -std=c++0x  main.cpp -o main


```

Please help!!

Thank you very much!

---

