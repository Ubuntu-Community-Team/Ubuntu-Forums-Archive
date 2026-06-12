---
title: "resize array length in a function c++"
date: 2007-08-23
forum: Programming Talk
---

### Post by monkeyking on 2007-08-23
Hi,

I need to pass an array to a function, resize the length.
So what I'm doing is making a new array and then try to point to the new allocation.
But it doesn't work.
And I also have problems, deleting [] the array.
```

#include <iostream>

using namespace std;

void test(int *array){
  int *var = new int[20];
    
  for (int i=0;i<10;i++)
    var[i]=array[i]+10;

  for (int i=10;i<20;i++)
    var[i]= i * 3;
  
  array=var;
  
}


int main(){
  int *var = new int[10];
  for (int i=0;i<10;i++)
    var[i]=i;
  test(var);
 
  for (int i=0;i<20;i++)
    cout <<var[i] << "\t";
  cout <<endl;

  delete [] var;
}




```

thanks in advance

---

### Post by psusi on 2007-08-23
array is  a local variable in test(), so assigning to it has no effect outside of test().  

You need to either use a std::vector<> or pass a pointer to pointer so that test can modify the caller's pointer.

---

### Post by Wybiral on 2007-08-23
You could define the function to take in the reference of the pointer...

But this would be VERY easy to leak memory with (calling the function twice with the same array would completely leak the first array).

I too think a vector (or some other STL container depending on your needs) would be your best (and safest) bet.

---

### Post by hod139 on 2007-08-23
There are 3 problems that I can see:
1) This is C++ code, so why are you using C-style arrays?  You should be using C++'s std::vector
2) You are passing the array pointer by value, not by reference.
3) Fixing 2 will cause a memory leak in your test function.

To fix 2, you need to change the test function to be call by reference:
```

void test(int ***&**array)

```One you do this though, you will now be leaking memory when you set array = var;  You need to delete the old array before the assignment.
```

if(array) 
   delete[] array;
array=var;

```I highly suggest you learn to use the STL, and leave the C-style arrays, and their associated problems, in C.

**Edit:** Looks like others were faster than me, but I gave code :)

---

### Post by Wybiral on 2007-08-23
> **hod139 said:**
> 
```

if(array) 
   delete[] array;
array=var;

```I highly suggest you learn to use the STL, and leave the C-style arrays, and their associated problems, in C.


Even this would only work if they made sure to set it to NULL when initializing and after it's been freed previously by something else, otherwise you'd get a double free error.

Use the STL, it's there.

---

### Post by rharriso on 2007-08-23
It's always a good idea to use Pointer arrays as apposed to the older array format. They are more flexible and i think. A really good book for that is Data Structures Using C++, it is a text book at most universities, but you could probably find an ebook copy fo free.

---

### Post by hod139 on 2007-08-23
> **Wybiral said:**
> Even this would only work if they made sure to set it to NULL when initializing and after it's been freed previously by something else, otherwise you'd get a double free error.

Use the STL, it's there.

Who doesn't initialize pointers to 0 :).  You are absolutely correct though, and I also highly recommend using the STL to avoid all this nastiness.

---

### Post by aks44 on 2007-08-23
May I add my voice to second that?

Use the STL, stop reinventing the wheel. You may achieve something all by yourself, but it will almost for sure be way worse than a library that quite a number of great brains out there took years to develop.

---

