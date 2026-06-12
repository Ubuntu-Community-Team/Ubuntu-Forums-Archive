---
title: "C++ Class without constructor and Memory Corruption"
date: 2011-04-04
forum: Programming Talk
---

### Post by DBQ on 2011-04-04
Hi Everybody!

I was fighting to debug a memory corruption issue now for a day!

My question is this: in C++, could memory corruption somehow be caused by creating a class without a constructor?  Is it even considered wrong to declare a class without a constructor? This is what I am lead to believe so far.  The structure of my code shown below mirrors in structure the actual problematic code (but the code below does NOT produce any problems).

```

#include <stdio.h>
#include <unistd.h>

class A
{
        public:
     
        int func()
        {   
                printf("Hello");
        }   
            
        int a;
        int b;
};

class B
{
        public:
            
            
        B(int& a)
        {   
                b = a;  
        }   
     
        A classa;
        int b;
      
};


int main() {
            
        int a = 100;
            
        B b(a);
} 


```

My original code would produce a segmentation fault in the constructor of class B when I try to copy the parameter to one of classes variables (in the actual class the parameter is a vector of strings.

Please help! I no longer know what to think.

---

### Post by DBQ on 2011-04-04
If anybody can help me, I would be very grateful!

---

### Post by dwhitney67 on 2011-04-04
There are no memory leaks in the code you provided; all of the objects and simple types (ie int) are declared on the stack.

If you do not declare a constructor for a class, the compiler will cheerfully provide one for you.  Of course, it may not be what you want.

In certain cases, it might be desirable to declare a private or protected constructor so that the class cannot be directly instantiated.

---

### Post by DBQ on 2011-04-04
Thank you so much for the reply...

So you are basically saying that memory corruption is impossible for such cases.  I am really puzzled now..

---

### Post by DBQ on 2011-04-04
I am wondering...is there such thing as the size of the local variable being too big?

---

### Post by DBQ on 2011-04-05
Also, is there such thing of the struct size being too big?  I.e. I have a struct of size of 10392

Could this be a problem?

---

### Post by dwhitney67 on 2011-04-05
> **DBQ said:**
> Also, is there such thing of the struct size being too big?  I.e. I have a struct of size of 10392

Could this be a problem?

Yes, it could be, especially if you declare it on the stack.  I have no idea what your system's stack size is set to.

I would rather not use my crystal ball to search for your code.  Could please post it!  You are supposed to make this easy for me, not hard.

---

### Post by Chimes on 2011-04-05
as discussed, your problem has nothing to do with dynamic memory / memory allocation. If you have not allocated memory dynamically with "new" then you aren't working with any dynamic memory.

It is though, as mentioned, a segmentation fault. A segmentation fault means you are trying to read or write from a segment of memory you are not supposed to be reading or writing from. 

Normally, your program only allocates and reads from memory in a few general areas which your computer has told it it should be using. These are called segments.

Usually what a segmentation fault means is you told your compiler to read or write in an area it shouldn't be reading or writing. That is, you gave it a memory address which either never pointed to a variable your program allocated, or which was being used to store a variable but isn't being used for that anymore (say, the variable only existed when a particular function was being called).

Things that can cause this: using either the reference(&) or deference(*) operator improperly in any of their uses, as well as using an index ([]) for an array past the bounds of their array. If you want to find the source of the problem, look for where those characters are for clues.

There is nothing wrong with not putting a constructor in a class. Constructors are useful for certain things, and can be necessary for others (they are necessary for guaranteeing certain instructions will be followed within any class instance immediately after its creation) but they are not, strictly speaking, necessary to a class.

It is generally considered good practice to make sure any classes you have made which are complex have a reasonable constructor, copy constructor and destructor in a class which do things you would expect. For example, if each instance of your class allocates a predictable amount of dynamic variables, it would be good to do those on construction, and good to make sure all those variables are deleted on destruction.

---

### Post by dazman19 on 2011-04-05
You have two choices for storing your information. 
1) heap
2) stack

The below is correct:
 
> 
If you do not declare a constructor for a class, the compiler will cheerfully provide one for you. 

If you want to use memory on the heap you must allocate it. In C++ this is done using the keyword "new".

Generally with the standard  API's like vector you can use "Push/Pop" mentality, where you can push things onto the stack, and pop them off. 

e.g. if i push "Chicken" onto the stack using the vector class, then push "cat". They will pop off in reverse order. So as the stack resolves cat will come off then chicken. 

Yeh I have never really tried to overflow the stack, and you usually get stack trace errors at runtime if you are overflowing it. I have not yet reached upper limitations of the stack sizes for a single object to be placed on it. But yes in a 32bit or 16 bit system you could run into these problems. The only problem i have ever had is declare a piece of memory say for an int of only 32 bits of memory, then run off the end of it, so i couldnt represent values larger than 2^32.
But like dwhitney67 said, we dont know what size your compiler has thinks you stack is. 

One important thing about c++, and I am guilty of this mistake, especially after coding in java. MAKE SURE YOU CLEAN UP you memory or you will have noticeable leaks in larger programs.

If you are constructing non-basic objects then destruct them. 

e.g. if you called new in the constructor or copy constructor, then you need to call delete() in the destructor.

Sometimes if you are dealing with abstract classes you can use virtual destructors/constructors to force implementation, but you need to remember if you are working with lots of tiny objects (only a few bits) then virtual destructors/constructors create a bit of an overhead because they use extra memory.

---

### Post by andrew1992 on 2011-04-05
Also, why are you using C's library for input and output? You're coding in C++, so use C++, not C. 

#include <iostream>

---

### Post by psusi on 2011-04-05
Since the example you posted does not cause the problem, you have obviously left out the critical part.  Post the original code.

---

