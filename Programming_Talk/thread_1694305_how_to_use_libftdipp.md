---
title: "how to use libftdipp"
date: 2011-02-24
forum: Programming Talk
---

### Post by aworld on 2011-02-24
Dear all

Can anyone gives me a clue that how to work with libftdipp ???


I have done : 

sudo apt-get install libftdi1 libftdipp-dev libftdi-dev libftdipp1

But I dont know how to compile that C++ program which i write,

It always shows me error like 'FT_STATUS was not declared in this scope'

what I do to compile this program is :

g++ -o *** -L.-lftd2xx -Wl,rpath /usr/local/lib -lusb ****.cpp

or, what should I do....???

when I am trying to add -lftdipp, it says it can not find this -ftdipp.

---

### Post by Zugzwang on 2011-02-24
"libftdipp" seems to support [pkg-config]("http://en.wikipedia.org/wiki/Pkg-config"). Try to compile your program as follows:
```

g++ -o *** ****.cpp -Wall $(pkg-config --libs --cflags libftdipp)

```

---

