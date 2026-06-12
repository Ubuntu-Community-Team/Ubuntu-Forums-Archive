---
title: "2D vector programming in Python"
date: 2010-08-23
forum: Programming Talk
---

### Post by eckeroo on 2010-08-23
For my engineering program, I need to calculate the properties of various cross sections of all shapes and sizes. I believe using vectors is the best approach, that way any shape I specify will be defined mathematically and will thus provide me with good mathematical properties.

After a quick Google search, I found just what I was looking for!

[http://www.partiallydisassembled.net/euclid.html](http://www.partiallydisassembled.net/euclid.html)

I'm using python and I will be trying out the euclid.py module from the above link. If anyone else knows of any other handy 2D vector modules then please post a link.

:D

---

### Post by surfer on 2010-08-23
the mother of all python speaking maths programs is [sage]("http://www.sagemath.org/"). but this may be a lot more than you need...

---

### Post by ssam on 2010-08-23
also have a look at numpy

---

### Post by worksofcraft on 2010-08-23
Python supports complex numbers and you can use a complex number to represent a 2D vector (Real component = X, Imaginary component is Y). Adding and subtracting two complex numbers is then the same as adding 2D vectors also scale multiplication works.

All you have to do is define your 2D shapes as a path in the complex plane, typically as a complex function of a simple real parameter.

---

