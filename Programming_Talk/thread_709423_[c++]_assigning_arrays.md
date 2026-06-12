---
title: "[c++] assigning arrays?"
date: 2008-02-27
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-02-27
Let me explain the situation. I have 2 classes. Each class has a 
```
bool myarray[4];
```
I want to assign('=') the contents of one array to the other doing this inside the **2nd class**
```
1class->myarray1 = myarray2;
```

When I try to compile g++ says "error: ISO C++ forbids assignment of arrays". Obviously my assignement is wrong. So how do I copy the contents all at once? 

Note: the 2 arrays are of the same type and have the same number of elements.

---

### Post by LaRoza on 2008-02-27
I am not sure of C++, but in C

memcpy (which will work in C++) will work. [http://www.cplusplus.com/reference/clibrary/cstring/memcpy.html](http://www.cplusplus.com/reference/clibrary/cstring/memcpy.html)

Or you can use the STL or pointers.

---

### Post by pedro_orange on 2008-02-27
Or

```

for(i=0; i< myarray.size(); i++)
  myarray2[i] = myarray1[i];

```

---

### Post by SledgeHammer_999 on 2008-02-27
well I somehow solved with this ugly thing:
```
for (int i = 0; i <= 3; i)
            {
                iclass->myarray1[i] = myarray2[i];
            }
```

But I have another problem now. Again 2 classes. In one class I have a(1class)
```
bool myarray1[4];
```

And to the other, because I want to access the same content and not copy it all over I have(2class):
```
bool * myarray2[4];
```

And when I do:
```
2class->myarray2 = &myarray1;
```

I get while compiling "error: incompatible types in assignment of &#8216;bool (*)[4]&#8217; to &#8216;bool* [4]"

EDIT: I now saw your solution **pedro_orange**

---

### Post by matherians2 on 2008-02-27
Looks like a type mismatch to me.  I believe you have to do element to element not whole array = whole array.  You maybe could find a C++ function that will do what you want.

---

### Post by SledgeHammer_999 on 2008-02-27
**matherians2** I think you're right because I solved it in a similar way:
```
for (int i = 0; i <= 3; i++)
        {
            2class->myarray2[i] = &myarray1[i];
         }
```

---

### Post by hod139 on 2008-02-27
> **SledgeHammer_999 said:**
> **matherians2** I think you're right because I solved it in a similar way:
```
for (int i = 0; i <= 3; i++)
        {
            2class->myarray2[i] = &myarray1[i];
         }
```
I don't think this is doing what you expect.  If this is C++ why are you not using vectors?

```

std::vector<bool> myarray(4);

```Then the code```

1class->myarray1 = myarray2;
```will work as you expect.

Then in your second class, if you only want a reference to the array, you can have
```

std::vector<bool> &myarrayCopy = myarray;

```If you really want to use a pointer instead of a reference, you can do 
```

std::vector<bool> *myarrayCopy = &myarray

```

---

### Post by Jucato on 2008-02-27
Just wondering if this doesn't work (not a C++ guru yet):

```

bool myarray1[4];

bool *myarray2;

2class->myarray2 = myarray1;

```

Since the name of the array (myarray1) is a constant pointer to the first element of the array, equivalent to &myarray[1]. Then you can use myarray2 like a regular array.

---

### Post by LaRoza on 2008-02-27
> **Jucato said:**
> 
Since the name of the array (myarray1) is a constant pointer to the first element of the array, equivalent to &myarray[1]. Then you can use myarray2 like a regular array.

It &myarray[0] because arrays are indexed from 0.

Yes, you can use it as an array, but you didn't allocate memory for it.

---

### Post by hod139 on 2008-02-27
> **LaRoza said:**
> 
Yes, you can use it as an array, but you didn't allocate memory for it.


This is a very important point.
```

int myarray1[4] = {1, 2, 3, 4};
int *myarray2 = myarray1;

```
this is known as pointer aliasing.  In this case, myarray2 points to another pointer.  This is legal, but bad things can happen if the original pointer is freed, since the alias is now pointing to released memory. 

Pointer aliasing also messes up a lot of standard compiler optimization tricks.

---

### Post by Lux Perpetua on 2008-02-27
> **SledgeHammer_999 said:**
> Let me explain the situation. I have 2 classes. Each class has a 
```
bool myarray[4];
```
I want to assign('=') the contents of one array to the other doing this inside the **2nd class**
```
1class->myarray1 = myarray2;
```

When I try to compile g++ says "error: ISO C++ forbids assignment of arrays". Obviously my assignement is wrong. So how do I copy the contents all at once? 

Note: the 2 arrays are of the same type and have the same number of elements.It is one of the quirks of C and C++ that arrays cannot be copied via the assignment operator, but structs containing arrays can (and it actually does copy the arrays). For example: ```
#include <iostream>

/* This wraps a (statically allocated) array of any type and size
 * and allows copying via the assignment operator. Note that no copy
 * constructor is implemented. */
template<typename T, int N>
struct array_wrapper {
    T array[N];

    // For syntactic sugar
    operator T *() {
        return array;
    }
};

using namespace std;

int main(int argc, char **argv)
{
    array_wrapper<int, 10> a1, a2;

    // Clear a2 to 0:
    for (int k = 0; k < 10; ++k) {
        a2[k] = 0;
    }

    // Now populate a1 (not a2):
    for (int k = 0; k < 10; ++k) {
        a1[k] = k;
    }

    // Copy a1 to a2:
    a2 = a1;

    // Let's see what we have now:
    for (int k = 0; k < 10; ++k) {
        cout << a2[k] << endl;
    }

    return 0;
}
```If you are really so opposed to writing your own loop to copy an array or using memcpy/memmove, you can use a contrivance like the above.

---

### Post by Jucato on 2008-02-28
Ah right! I completely forgot the case when the original pointer no longer points to what it's intended to point to. (ouch! pointy!) I guess the intimate relationship between arrays and pointers got so stuck in my head that I forgot about those considerations. Just when you think you've got a firm grasp on pointers, it manages to prove you terribly wrong again.

So in C++, the cleanest and most efficient way to do this would be to use vectors, right? I'm interested to learn how to do it in C or in a "low-level" way (using arrays and pointers), specially the 2nd task: "I want to access the same content and not copy it all over."

---

### Post by eye208 on 2008-02-28
> **SledgeHammer_999 said:**
> When I try to compile g++ says "error: ISO C++ forbids assignment of arrays". Obviously my assignement is wrong. So how do I copy the contents all at once? 

Note: the 2 arrays are of the same type and have the same number of elements.
Yes, but that is unknown at runtime. You can make it known by putting the array into a struct so that it forms a new type:
```
struct MyArray
{
        bool values[4];
};
```
Then you can copy it like this:
```
MyArray myarray1, myarray2;
...
myarray2 = myarray1;
```
Whatever you do, avoid pointers! ;)

---

### Post by rye_ on 2008-02-28
I prefer c but ....if your a c++ type..

if its a 'class' that you have created you could use the c++ way of creating an asignment operators (constructor method) in order to copy by value the instance variables of two objects of the same class.
ofcourse one of intance variables to be copied would be the array that youy are referring to.


Ryan

---

### Post by hod139 on 2008-02-28
> **Lux Perpetua said:**
> It is one of the quirks of C and C++ that arrays cannot be copied via the assignment operator, but structs containing arrays can (and it actually does copy the arrays). 
Be very careful with this statement.  The default copy constructor will only do a shallow copy, not a deep copy. ([http://en.wikipedia.org/wiki/Object_copy#Deep_vs._Shallow_vs._Lazy_copy](http://en.wikipedia.org/wiki/Object_copy#Deep_vs._Shallow_vs._Lazy_copy))

---

### Post by Lux Perpetua on 2008-02-28
> **hod139 said:**
> Be very careful with this statement.  The default copy constructor will only do a shallow copy, not a deep copy. ([http://en.wikipedia.org/wiki/Object_copy#Deep_vs._Shallow_vs._Lazy_copy](http://en.wikipedia.org/wiki/Object_copy#Deep_vs._Shallow_vs._Lazy_copy))Right, but if a struct contains a field that is a true array (not a pointer to one: the distinction is very important here), then a shallow copy will copy the array elements.

---

### Post by hod139 on 2008-02-28
> **Lux Perpetua said:**
> Right, but if a struct contains a field that is a true array (not a pointer to one: the distinction is very important here), then a shallow copy will copy the array elements.
It will also (potentially) fail if the array elements are not primitive types.  If you have an array of pointers, it will only do a shallow copy (which may be fine depending on the problem).

---

### Post by eye208 on 2008-02-29
> **hod139 said:**
> It will also (potentially) fail if the array elements are not primitive types.
Any non-primitive type is supposed to behave like a primitive one in regard to copying. Anything else would be considered a bug in its implementation. A non-primitive type that fails to copy itself cannot be passed to a function either.

Pointers are the only types that are not covered by shallow copying, i.e. if a struct or class contains pointers to non-static data, it must override the default copy constructor to handle these.

---

