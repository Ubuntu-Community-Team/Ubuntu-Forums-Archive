---
title: "Max/min float and double"
date: 2006-03-30
forum: Programming Talk
---

### Post by Téragone on 2006-03-30
In which .h file max/min float and double are defined ?

Thanks

---

### Post by JmSchanck on 2006-03-30
math.h provides fmax() and fmin() for double values. I'm pretty it also provides functions for float and long double values by appending an f or an l to the function names.

---

### Post by lovebyte on 2006-03-31
Ints are defined in /usr/include/limits.h

Floats (and doubles) are defined in float.h.  On my machine at work (fedora) it is in :
/usr/lib/gcc/i386-redhat-linux/3.4.3/include/float.h

You might want to try a find command such as:
find /usr -name float.h -print

---

### Post by rplantz on 2006-03-31
[QUOTE=lovebyte]You might want to try a find command such as:
find /usr -name float.h -print[/QUOTE]

Also, ```

$ locate float.h
/usr/share/doc/rubybook/html/ref_c_float.html
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/include/float.h

```
will help you find it.

---

### Post by Téragone on 2006-03-31
Thanks very much to all.

I also find that for c++ we can use :  

std::numeric_limits<double>::max()
std::numeric_limits<float>::max()

---

### Post by LordHunter317 on 2006-04-01
'float' and 'double' aren't defined anywhere as they're part of the language.

---

