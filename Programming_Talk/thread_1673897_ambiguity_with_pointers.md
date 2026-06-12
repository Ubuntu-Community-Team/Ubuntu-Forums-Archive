---
title: "ambiguity with pointers"
date: 2011-01-23
forum: Programming Talk
---

### Post by c2tarun on 2011-01-23
```


[LIST=1]
[*]#include<stdio.h>
[*]void main()
[*]{
[*]int a[5]={7,3,1,4,5};
[*]printf("%p\n",a);
[*]printf("%p\n",&a);
[*]printf("%p",&a+1);
[*]}
[/LIST]

```why the o/p of line 5 and 7 are same? Conceptually &a should return the address of the memory location that stores the base address of array.

on increment of 1 the resulting memory address is 14 greater than the base address, why so?

---

### Post by Praveen30 on 2011-01-23
> **c2tarun said:**
> ```


[LIST=1]
[*]#include<stdio.h>
[*]void main()
[*]{
[*]int a[5]={7,3,1,4,5};
[*]printf("%p\n",a);
[*]printf("%p\n",&a);
[*]printf("%p",&a+1);
[*]}
[/LIST]

```why the o/p of line 5 and 7 are same? Conceptually &a should return the address of the memory location that stores the base address of array.

on increment of 1 the resulting memory address is 14 greater than the base address, why so?

tell me your output!!!

---

### Post by c2tarun on 2011-01-23
> **Praveen30 said:**
> tell me your output!!!

0x7fff5dbff520
0x7fff5dbff520
0x7fff5dbff534

---

### Post by Praveen30 on 2011-01-23
> **c2tarun said:**
> 0x7fff5dbff520
0x7fff5dbff520
0x7fff5dbff534

topic--using array name as a pointer
concept-
An array name can be used as a pointer to the first element in the array...

for example--int a[10];
 using a as a pointer to the first element you can modify a[0];
 so *a=7;

 similarly, you can modify a[1] by *(a+1)..

note-- in general a+i is same as &a[i] and *(a+i) as a[i].

first ans:- a and &a both will point at the first element of the array so the address will be same...

---

### Post by c2tarun on 2011-01-23
> **Praveen30 said:**
> topic--using array name as a pointer
concept-
An array name can be used as a pointer to the first element in the array...

for example--int a[10];
 using a as a pointer to the first element you can modify a[0];
 so *a=7;

 similarly, you can modify a[1] by *(a+1)..

note-- in general a+i is same as &a[i] and *(a+i) as a[i].

first ans:- a and &a both will point at the first element of the array so the address will be same...

If a is pointer to first element than &a should be a pointer to a, as double pointer.

---

### Post by Arndt on 2011-01-23
> **c2tarun said:**
> If a is pointer to first element than &a should be a pointer to a, as double pointer.

If a is a variable, yes. But pointers are not created by the & operation; they are just values. In this case, a is not a variable whose address can be taken, it's an address itself. What would you want &a to be?

---

### Post by worksofcraft on 2011-01-23
> **Arndt said:**
> If a is a variable, yes. But pointers are not created by the & operation; they are just values. In this case, a is not a variable whose address can be taken, it's an address itself. What would you want &a to be?

Yes I agree with this.
However you are correct c2tarun, "a" here is indeed ambiguous.

In C and C++ that "a" can mean the address of the array, but it can also mean the whole array. Try compiling with all warnings switched on and see look this what we get:
```

g++ -Wall -pedantic arryptr.cpp
arryptr.cpp: In function &#8216;int main()&#8217;:
arryptr.cpp:9: warning: format &#8216;%p&#8217; expects type &#8216;void*&#8217;, but argument 2 has type &#8216;int*&#8217;
arryptr.cpp:11: warning: format &#8216;%p&#8217; expects type &#8216;void*&#8217;, but argument 2 has type &#8216;int (*)[5]&#8217;
arryptr.cpp:13: warning: format &#8216;%p&#8217; expects type &#8216;void*&#8217;, but argument 2 has type &#8216;int (*)[5]&#8217;

```

Well I'm not interested in the "void*" bit (nor main returning and int), but when you take the address of a the compiler decides that you CAN'T have the address of an address (because an address is not an [lvalue]("http://en.wikipedia.org/wiki/Value_(computer_science)"))

So instead it decides that you must have meant the whole array and the address of that is infact the same as "a" when it is used as an address:
```

$ ./a.out
0x7fff96eb6790 <--- a
0x7fff96eb6790 <--- see &a = a
0x7fff96eb67a4

```

now if a is a whole array of 5 ints and an int is 4 bytes then  a+1 must be the next array of 5 ints... so 5 * 4 = 20 decimal = 16 + 4 = 0x14 hex...

;)

---

### Post by c2tarun on 2011-01-23
> **worksofcraft said:**
> Yes I agree with this.
However you are correct c2tarun, "a" here is indeed ambiguous.

In C and C++ that "a" can mean the address of the array, but it can also mean the whole array. Try compiling with all warnings switched on and see look this what we get:
```

g++ -Wall -pedantic arryptr.cpp
arryptr.cpp: In function ‘int main()’:
arryptr.cpp:9: warning: format ‘%p’ expects type ‘void*’, but argument 2 has type ‘int*’
arryptr.cpp:11: warning: format ‘%p’ expects type ‘void*’, but argument 2 has type ‘int (*)[5]’
arryptr.cpp:13: warning: format ‘%p’ expects type ‘void*’, but argument 2 has type ‘int (*)[5]’

```Well I'm not interested in the "void*" bit (nor main returning and int), but when you take the address of a the compiler decides that you CAN'T have the address of an address (because an address is not an [lvalue]("http://en.wikipedia.org/wiki/Value_%28computer_science%29"))

So instead it decides that you must have meant the whole array and the address of that is infact the same as "a" when it is used as an address:
```

$ ./a.out
0x7fff96eb6790 <--- a
0x7fff96eb6790 <--- see &a = a
0x7fff96eb67a4

```now if a is a whole array of 5 ints and an int is 4 bytes then  a+1 must be the next array of 5 ints... so 5 * 4 = 20 decimal = 16 + 4 = 0x14 hex...

;)

awesome explanation. Thanks a lot.
A bit personal question, are you denss richie or someone, you know almost everything about C and C++. How come :)

---

### Post by worksofcraft on 2011-01-23
> **c2tarun said:**
> awesome explanation. Thanks a lot.
A bit personal question, are you denss richie or someone, you know almost everything about C and C++. How come :)

lol - no, once upon a time I used to program test routines to test OEM equipment. Then I had an arts and craft shop for a while (hence the name) and I only recently decided to pick up programming again (as a hobby)... still unemployed single parent atm :/

---

### Post by c2tarun on 2011-01-23
> **worksofcraft said:**
> lol - no, once upon a time I used to program test routines to test OEM equipment. Then I had an arts and craft shop for a while (hence the name) and I only recently decided to pick up programming again (as a hobby)... still unemployed single parent atm :/
god if its just a hobby than u know so much :). I can't even imagine what will happen when you'll be a professional. Believe me here there are programmers who know lot less than you and still they are software engineers ;)

---

### Post by worksofcraft on 2011-01-23
> **c2tarun said:**
> god if its just a hobby than u know so much :). I can't even imagine what will happen when you'll be a professional. Believe me here there are programmers who know lot less than you and still they are software engineers ;)

TYVM :) I did actually apply for some tutor jobs because I think I am good at explaining things. However they tend to only want people with qualifications... so you make sure you get some while you can! :shock:

---

