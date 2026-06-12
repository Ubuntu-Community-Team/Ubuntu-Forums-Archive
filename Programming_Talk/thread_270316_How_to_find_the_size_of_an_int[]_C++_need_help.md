---
title: "How to find the size of an int[] C++ need help"
date: 2006-10-03
forum: Programming Talk
---

### Post by thenetduck on 2006-10-03
Hi, 
  I need to find the size of an array that I have type int[]. The size is unknown but I need to run it though a for loop. Does anyone know what the member function for the size of an int array is? Im fairly new to c++ so I am not sure and can't find anything so far. Thanks ,
 
 The Net Duck

---

### Post by amo-ej1 on 2006-10-03
and int[] array isn't an object, so the size isn't readily available (unless you make use of a datastructure like a vector).

Luckily there is the sizeof() operator. Here sizeof() returns the amount of bytes such an array occupies, when we dived this by the size of one unit (sizeof(int)) of the array we get the number of elements in it. (or at least the number of elements we reserver the room for)


```

#include <iostream>
using namespace std;

int main(int argc, char **argv){
        int testing[15];
        cout << sizeof(testing)/sizeof(int) << endl;

}


```

---

### Post by Ragazzo on 2006-10-03
sizeof is a compile-time operator so the compiler doesn't know the size if you pass only the array to a function.

---

### Post by Ayman on 2006-10-04
If it's a dynamic array (created with new or (m|c)alloc, there is no way to tell its size without storing it in another variable.

Either that or use std::vector.

---

### Post by fyz on 2006-10-04
As Ayman said, unless you use standard container such as vector,
you would not be able to know the size of your array readily.

Normally, when you use "new", you should alreay know how many elements. 

In the case of function parameter, there should be another parameter together with the raw pointer, indicating the size of array. (Unless you don't care)


> **thenetduck said:**
> Hi, 
  I need to find the size of an array that I have type int[]. The size is unknown but I need to run it though a for loop. Does anyone know what the member function for the size of an int array is? Im fairly new to c++ so I am not sure and can't find anything so far. Thanks ,
 
 The Net Duck

---

