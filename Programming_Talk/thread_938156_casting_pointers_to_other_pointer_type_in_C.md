---
title: "casting pointers to other pointer type in C"
date: 2008-10-04
forum: Programming Talk
---

### Post by stairwayoflight on 2008-10-04
Greets to Ubuntu community!

I am following the GNU C tutorial, which asks the reader to: "Write a statement which converts a pointer to an integer into a pointer to a double type."

According to the tutorial, I can do:
```

int *my_integer_ptr;
long *my_long_ptr;

my_long_ptr = (long *) my_integer_ptr;
```

But when I do:
```

int my_int = 5;
double my_double = 10.0;
int *my_int_ptr;
double *my_double_ptr;
my_int_ptr = &my_int;
my_double_ptr = (double *) my_int_ptr;
printf("value: %f\n\n", my_double_ptr);

```

some fractional number is printed, nothing resembling 5.0 .

My questions are:
1. Have I done something wrong?
2. If not, what useful property is availed by casting an int* to a float* ?

Regards,
Stairway

---

### Post by Idefix82 on 2008-10-04
Your print statement prints out the value of the variable my_double_ptr, which is an address. If you want to access the value that it's referring to rather than the value of the variable itself you need to write
```
*my_double_ptr
```
This is called dereferencing (you can google for it).

---

### Post by lian1238 on 2008-10-04
You're casting correctly, but not printing correctly. Casting is just converting one type to another so you can assign them, because you can't assign objects of different type (they could be of different sizes).

[http://en.wikipedia.org/wiki/Type_conversion](http://en.wikipedia.org/wiki/Type_conversion)

---

### Post by stroyan on 2008-10-04
> **stairwayoflight said:**
> 
I am following the GNU C tutorial, which asks the reader to: "Write a statement which converts a pointer to an integer into a pointer to a double type."
...
My questions are:
1. Have I done something wrong?
2. If not, what useful property is availed by casting an int* to a float* ?


The question from the tutorial is an odd one.  It is possible to cast an
int* to a float* as you have done.  But it is seldom useful.
To use a pointer reliably the address that it points to needs to be set and read with a consistent type.  Setting it as and int and reading it as a double is not expected to give a useful result.  Some systems may even give the program a fatal SIGBUS when deferencing an int* as a double* because doubles require more strict address alignment to a multiple of sizeof(double).
The only really good use that comes to mind for such a cast is when a pointer may point to different types for different cases.  Another value may be used to specify which type is stored in the address pointed to.  That does require carefull handling of allocation for address alignment.  Such a generic pointer is usually declared as void* rather than a specific type like int*.  The compiler will catch any attempt to dereference a void* without casting it to another type of pointer first.

---

### Post by slavik on 2008-10-04
> **stroyan said:**
> The question from the tutorial is an odd one.  It is possible to cast an
int* to a float* as you have done.  But it is seldom useful.
To use a pointer reliably the address that it points to needs to be set and read with a consistent type.  Setting it as and int and reading it as a double is not expected to give a useful result.  Some systems may even give the program a fatal SIGBUS when deferencing an int* as a double* because doubles require more strict address alignment to a multiple of sizeof(double).
The only really good use that comes to mind for such a cast is when a pointer may point to different types for different cases.  Another value may be used to specify which type is stored in the address pointed to.  That does require carefull handling of allocation for address alignment.  Such a generic pointer is usually declared as void* rather than a specific type like int*.  The compiler will catch any attempt to dereference a void* without casting it to another type of pointer first.
there is an example where a float* is casted to an int*. It's the famous linear 1/sqrt(n) function from Q3A

---

### Post by stairwayoflight on 2008-10-05
Ahh, this helped me understand. The double is 8 bytes while the int is only 4; that explains why the value of the double changed every time I ran the program--the second "half" of it was a new memory address each time.

I appreciate the help. I don't like to go on in a book or a tutorial unless I understand the material from the beginning. Thanks, everyone.

---

### Post by nvteighen on 2008-10-05
> **stairwayoflight said:**
> Ahh, this helped me understand. The double is 8 bytes while the int is only 4

Ehmm... not actually.

An **int** will be as long as the natural word of your platform is. If you're on a 32-bit platform, it will be 32 bit long = 4 bytes. But in 64-bit, it will be 8.

A double lenghted **int** is a **long int** (or simply, **long**), which is 8 byte long. You can even have a **long long int** (16 bytes) and only in 64-bit platforms, a **long long long int**. If interested, to use printf() with them, you need the %ld, %lld or %llld identifiers, respectively.

Then, a **double** is usually 8 byte long, but for fractional values ([http://en.wikipedia.org/wiki/Double_precision](http://en.wikipedia.org/wiki/Double_precision)), where a **float** is 4 but divided as shown at: [http://en.wikipedia.org/wiki/Single_precision](http://en.wikipedia.org/wiki/Single_precision). (the name "float" is somewhat misleading, as it isn't a "floating precision" data type).

---

### Post by hod139 on 2008-10-06
> **nvteighen said:**
> Ehmm... not actually.

An **int** will be as long as the natural word of your platform is. If you're on a 32-bit platform, it will be 32 bit long = 4 bytes. But in 64-bit, it will be 8.

This is not correct.  For example, on an AMD64 processor, an int is defined as 32-bits, even though the word size is 64 bits.  The only standard is that pointers will be the word size.  This post also mentions this: [http://ubuntuforums.org/showpost.php?p=5508018&postcount=10](http://ubuntuforums.org/showpost.php?p=5508018&postcount=10)

---

### Post by nvteighen on 2008-10-06
> **hod139 said:**
> This is not correct.  For example, on an AMD64 processor, an int is defined as 32-bits, even though the word size is 64 bits.  The only standard is that pointers will be the word size.  This post also mentions this: [http://ubuntuforums.org/showpost.php?p=5508018&postcount=10](http://ubuntuforums.org/showpost.php?p=5508018&postcount=10)
Thanks for pointing out my mistake.

---

