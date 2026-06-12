---
title: "C++ pointers"
date: 2008-03-12
forum: Programming Talk
---

### Post by StOoZ on 2008-03-12
as im progressing with my C++ studying , I use pointers more and more..
apparently I still cant see the advantage of pointer over regular variables...
what would I prefer to use a pointer instead of a regular variable? 
:confused:

---

### Post by Zugzwang on 2008-03-12
There are a couple of usages for pointers:
[LIST]
[*]You can use pointers if you want to pass something to a function that needs to be modified by the function (if you do it the "normal way", the argument is copied when calling the function and the original object stays untouched).
[*]In some cases, you need pointers for building data structures such as linked lists, for example
[*]A more technical argument is: Try to allocate ant int-array of size 30.000.000 in a function:```
int a[30000000];
``` Your program is likely to throw a stack overflow. If on the other hand, you do:```
int *a = new int[30000000];
``` this is going to work.
[*] ...a couple of reasons not mentioned here.
[/LIST]
Note that you can use references in the first case and STL data structures for the second case (in both cases pointers will be used internally). There exists a "philosophy" of designing C++ programs by avoiding pointers in your own code as much as possible since they are a common cause for errors, but nevertheless at least under the hood there will always be a lot of pointers involved.

---

### Post by StOoZ on 2008-03-12
thanks for that wonderful reply.
actually, I defiantly don't want to avoid pointers, I quite like them, but this subject is still obscured to me.. :(

---

### Post by psusi on 2008-03-12
The main reason is that the meaning of a pointer can change throughout the life of the program.  Normal variables always refer to the same variable.  This allows the program to manipulate sets of data that you don't necessarily know about at the time you write the program.

---

### Post by dempl_dempl on 2008-03-12
when you need to return multiple values : 

For example:

```


void function (  int x , int y) 
{
  x = x + 5;
 y = y + 5;
}

int main( ) 
{
 int x =5;
int y = 6;
function( x, y);
}


```


X and Y won't change, while with : 


```


void function (  int& x , int& y) 
{
  x = x + 5;
 y = y + 5;
}

int main( ) 
{
 int x =5;
int y = 6;
function( x, y);
}



```

They will.

In this example I've used references, but references are basically constant pointers. Cheers!

---

### Post by matherians2 on 2008-03-12
Pointers use less amount of memory.  Also, it would be helpful in referencing an array.  A lot of built in functions use pointers.

---

### Post by bjdodo on 2008-03-12
I think if you understand the background, you will understand the benefits. 

You can pass the location of an object (location = address in memory) by passing a pointer. The pointer is only the address, a simple number, like an int.

If you use it as a function parameter, you will not copy the object the pointer points to. If the function parameter is a class, the class will be copied.

That is why, as Zugzwang has written, you can use pointers to pass variables to functions, they can fill it and then the caller will see the new value, because the same memory area will be written - so it is useful in output (and in-out) parameters. It is usually useful for input parameters as well, because copying the object is usually more time consuming (as it is usually bigger than its address). If you do not want a function to modify your object (input parameter), it would be logical to copy the parameter (then the function would only be able to modify the copy that you do not care about), but to avoid copying large amounts of memory, you can declare the function parameter to be a const pointer (like void func(const string* str); ). In this case the invoked function will get the address of the object, but it is well... kindly asked not to modify that memory area (there are techniques how you can still write into that area a const pointer points to, but in general using a const pointer you cannot call any non-const function on a class - therefore you will not modify the class if no trick is involved).

You can also use pointer to share the same instance of a class. This is a stupid example, but let us suppose that you have a class that contains a list of product prices in a map, let us call it CPriceMap. The list would be created when the app starts, from a file that contains up-to date info updated daily. If you have 3 classes that make calculations based on product prices, you want to share the same instance of CPriceMap amongst the 3 classes. So you can pass a pointer to the constructor of your calculating classes and save a pointer to the CPriceMap class in a member variable and the product price info is always going to be there.

The reference stuff: by using pointers it is very easy to cause memory leaks. Using references in the trivial way has the same advantage as the pointers, but references guarantees that no memory leak happens, therefore it is very good to use them wherever possible instead of pointers. On the other hand references cannot be used in all situations (e.g. because a reference cannot be NULL that is a limit sometimes).

Another good thing to check is the auto_ptr in STL that tries to address the memory leak problem.

---

