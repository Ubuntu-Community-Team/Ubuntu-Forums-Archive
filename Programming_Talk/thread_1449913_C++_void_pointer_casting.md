---
title: "C++ void pointer casting"
date: 2010-04-08
forum: Programming Talk
---

### Post by Houman on 2010-04-08
hello there;

In my C++ app i am calling a C function that expects some data as a void pointer, however my data is in this format:

```

vector< vector<HMat*> > myData;

```

where HMat is my own class;
I really tried to avoid this but i dont see any ways around it, is there any way to cast a double vector like the one i have to a void and vice versa?

thank you

H

---

### Post by SledgeHammer_999 on 2010-04-08
Let's assume that the function you want to call has this format "my_function (void *data)"

Then you can do a: "my_function((void*)&myData);"
But you have to ensure that the vector myData doesn't get out-of-scope after that function-call.

---

### Post by Houman on 2010-04-08
hi there;

yes it worked; i guess its just like C. i thought i had to use reinterpret_cast or something;

thanks you 
H

---

### Post by MadCow108 on 2010-04-08
static_cast reinterpret_cast and const_cast are just "typedefs" for C style casts. They all do the same as a plain C cast.

the purpose of them is to indicate what the cast does and is thus the recommended way (better documentation and c++ casts are easier to find with code parsers)
static_cast is the normal C style cast
reinterpret_cast should be used when the cast changes how the data will be interpreted (but it does the same as static_cast). e.g. casting a char pointer to double pointer. It is most often used for binary input output.
const_cast changes the constness

the only different cast is dynamic_cast. This cast is different as it adds runtime code to check if the type is correct.
C has no equivalent for this.

btw I would be quite surprised if the C function can handle that data.
the internals of a vector are implementation dependent. and when you pass the pointer to a vector to a function you confront the C function with this structure and it may not know how to handle it.

If the function expects a plain 1d C array you pass this (assuming mydata is a 1d vector):
&mydata[0]
this passes the address of the first value in the internal memory block of the vector. This is defined in the standard to be identical to a C array

---

### Post by Houman on 2010-04-08
hi there;

thank you for your clear explanation; 

the C code that im using is part of a bigger library. In this library the argument of one of the functions is a void pointer and this is where i have to cast my double vector. However, this C function will pass this void pointer to another custom function that i have written and in that function i will simply cast the void pointer back to a double vector and use it normally. Its just this C style interface that is forcing me to temporarily use a void pointer as a reference to my original data. 

thank you 
H

---

