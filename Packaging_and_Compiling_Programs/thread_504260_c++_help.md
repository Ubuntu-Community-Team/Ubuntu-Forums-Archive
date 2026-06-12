---
title: "c++ help"
date: 2007-07-18
forum: Packaging and Compiling Programs
---

### Post by zerobinary on 2007-07-18
what is setprecision this manipulator do and what is the header iomanip do

---

### Post by zerobinary on 2007-07-19
any one knows

---

### Post by Rui Pais on 2007-07-19
> **zerobinary said:**
> what is setprecision this manipulator do and what is the header iomanip do

Hi, use:
```
cout.precision(N);
```
(no iomanip header needed)

or:
```
#include <iomanip>
cout << "A number" << setprecision(N) << some_float_number;
```
where N is an integer with the precision digits desired.

[Check this]("http://www.cppreference.com/io_flags.html") and [this]("http://www.cppreference.com/cppio/precision.html").

---

### Post by zerobinary on 2007-07-19
so what is setprecision actually do i don't quite get what do u mean 
plz help me

---

### Post by Rui Pais on 2007-07-19
They are 2 different ways for you to change precision of float numbers from default to the one you want.

For instance, if you want the output of 2.0/3.0 with 15 digits you can do the above with N=15. 
```

cout.precision(15);
cout<<2.0/3.0;
```

---

### Post by zerobinary on 2007-07-19
k thx

---

