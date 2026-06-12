---
title: "[c++] Function Prototyping"
date: 2009-03-09
forum: Programming Talk
---

### Post by kreggz on 2009-03-09
Hello,

I am trying to teach myself c++ and I am wondering what the point of function prototyping is? Seems like you can put your functions above main and avoid compilation problems.

cheers

---

### Post by tneva82 on 2009-03-09
> **kreggz said:**
> Hello,

I am trying to teach myself c++ and I am wondering what the point of function prototyping is? Seems like you can put your functions above main and avoid compilation problems.

cheers

That only works if you need function in the file that contains main.

However the larger the program the more it becomes unfeasible to contain every code in one .cpp file.

Then you need prototypes ;-)

---

### Post by regala on 2009-03-09
> **kreggz said:**
> Hello,

I am trying to teach myself c++ and I am wondering what the point of function prototyping is? Seems like you can put your functions above main and avoid compilation problems.

cheers

How do you teach yourself c++ ? and which languages do you already know ?

---

### Post by jimi_hendrix on 2009-03-09
if you have a large program and multple .cpp files, you put your prototypes in headers, this lets you use the fuctions elsewhere but lets the compiler knows they exist, but the compiler hasnt found them yet and wont until you link at the end of the build process

---

### Post by abhilashm86 on 2009-03-09
function prototyping also tells the type of data type parameters passing to function by calling function,
we help syntax analyzer of compiler inorder to recognise eroors if we pass exeeding parameters or mismatch datatypes.

---

### Post by kreggz on 2009-03-09
Thanks, great replies!

I am using a really old c++ book to teach myself, I know how to do basic vb and bash. This is just as a hobby though.

---

