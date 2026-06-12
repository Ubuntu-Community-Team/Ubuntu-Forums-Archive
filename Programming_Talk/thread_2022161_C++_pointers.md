---
title: "C++ pointers"
date: 2012-07-10
forum: Programming Talk
---

### Post by Lymphocyte on 2012-07-10
hi, 
  i am starting to learn about pointers. Exactly what is the purpose of using them? when you can simply declare the variables instead?

---

### Post by cgroza on 2012-07-10
This topic should be covered by your tutorial or book. I highly recommend The C++ Programming language written by its inventor.

---

### Post by CptPicard on 2012-07-10
Pointers are essentially an indirection abstraction. When you can build things of references to things -- or of references to things with further references -- you can structure arbitrarily nested things at runtime. Try writing a non-trivial data structure and you'll quickly figure out why you'll want an ability to refer to a thing by not using the thing in itself.

---

### Post by SirWhy on 2012-07-10
A few years ago I asked the same thing.

Pointers aren't very useful in very small programs (the type used to illustrate concepts of C++ or any language) so declaring variables is easier. 

To illustrate the point of pointers (puns, puns, puns everywhere), consider this code

```
#include <iostream>
using namespace std;
void triple(int * number); //function prototype

int main()
{
    int num = 5;
    int *ptr = &num; //pointer to num location
    
    cout<< "num value is "<<num<<endl;
    triple(ptr);      //pass num location to function
    cout<< "num value is now "<<num<<endl;
    int pause;
    cin>>pause;
    return 0;
}

void triple (int * number)
{
     *number = *number * 3; //change the value of num
}
```

(First off this code isn't mine, it's from a bookmark I had when I was learning about them ([http://www.cplusplus.com/forum/beginner/337/](http://www.cplusplus.com/forum/beginner/337/))) The program creates a variable (int num = 5) and  pointer to that variable in the next line. The pointer is passed to the function triple. Since the pointer is pointing to the address of num, it's like passing num to triple. 

This can be done without the pointers but it does illustrate their point (pun)

Also a function cannot return char but it can return char* (pointer to that char variable) I believe (I'm not sure about that, I have to brush up on my C++, and I was quite amateur to begin)

---

### Post by the_unforgiven on 2012-07-11
> **Lymphocyte said:**
> hi, 
  i am starting to learn about pointers. Exactly what is the purpose of using them? when you can simply declare the variables instead?

The simplest definition of pointers is they are like normal variables but with the sole purpose of storing **addresses** of other variables.

Like CptPicard mentioned, they're essentially an abstraction of indirection - which allows for some really nifty stuff - like building really complex data structures. Since pointers are like regular variables, their contents (essentially, an address) can be changed/modified at runtime. That is, they can be made to point to different objects in memory at runtime - which is not possible using just references.

---

### Post by 11jmb on 2012-07-11
> **SirWhy said:**
> 
Pointers aren't very useful in very small programs (the type used to illustrate concepts of C++ or any language) so declaring variables is easier. 

To illustrate the point of pointers (puns, puns, puns everywhere), consider this code

```
#include <iostream>
using namespace std;
void triple(int * number); //function prototype

int main()
{
    int num = 5;
    int *ptr = &num; //pointer to num location
    
    cout<< "num value is "<<num<<endl;
    triple(ptr);      //pass num location to function
    cout<< "num value is now "<<num<<endl;
    int pause;
    cin>>pause;
    return 0;
}

void triple (int * number)
{
     *number = *number * 3; //change the value of num
}
```

...


The preferred way to do something like that in C++ is by reference. 

> **SirWhy said:**
> 
Also a function cannot return char but it can return char* (pointer to that char variable) I believe (I'm not sure about that, I have to brush up on my C++, and I was quite amateur to begin)


This is incorrect. Could you perhaps be confused about trying to return a string literal instead of a dynamically allocated char*?


In the C++ development I've done, the general mindset is that you should avoid the use of raw pointers at any reasonable cost. Preferred to raw pointers are references, STL containers and 'smart pointers' in the boost library (I think that the smart pointers are going to be standardized as well)

To answer your question, a more relevant example of where pointers are useful might be a linked list. Each node of the list has some kind of useful data and a pointer to the next node in the list. Suppose for the sake of argument that the useful data in each element in the list is a 32-bit integer and a 64-bit double.

Without the use of pointers, the last item in the list would be 96 bits, the one before that would be 192 bits, and the item before that would be 288...384...480...and so forth

Instead of actually embedding the next node into its parent, the practical way to solve this problem would be to store the next node as a Node*. That way every item in this (admittedly contrived) list would be 128 bits (using 32-bit addresses)

---

### Post by dwhitney67 on 2012-07-11
> **11jmb said:**
> 
Could you perhaps be confused about trying to return a string literal instead of a dynamically allocated char*?


Returning a string-literal is permitted too.  For example:
```

const char* helloworld()
{
    return "Hello World!";
}

```

As you pointed out (no pun), using pointers is generally considered the last option to consider in C++, however when allocating memory on the heap, they are essential.  In the case of char pointers, a better option to consider is using the STL string class (which encapsulates a char pointer).

---

### Post by SirWhy on 2012-07-11
> 
This is incorrect. Could you perhaps be confused about trying to return a string literal instead of a dynamically allocated char*?



Exactly, as I said I too need to brush up on my C++ knowledge

---

