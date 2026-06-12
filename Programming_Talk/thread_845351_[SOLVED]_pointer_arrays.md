---
title: "[SOLVED] pointer arrays?"
date: 2008-06-30
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-30
C++: To my knowledge I can make a pointer array with 'new' in this fashon:
```
int* value=new int(5);
```
But I'm curious what the right method is to make a pointer array, which points to values which already exist? You see, I'm afraid if I do it wrong I'll have problems I cant explain.

---

### Post by StOoZ on 2008-06-30
what you did is not an array, its just a dynamically allocated pointer which points to an int and initialized with 5.

---

### Post by dwhitney67 on 2008-06-30
This is the correct syntax used to allocate an array from the heap:
[PHP]int *array = new int[5];[/PHP]
Perhaps you had a typo?

If you want to declare an array on the stack:
[PHP]int array[5];[/PHP]

As for your question, I am not sure what you are looking for; perhaps something like the following?
[PHP]
  int value1 = 10;
  int value2 = 20;
  int value3 = 30;
  int value4 = 40;
  int value5 = 50;

  int *array[5];

  array[0] = &value1;
  array[1] = &value2;
  array[2] = &value3;
  array[3] = &value4;
  array[4] = &value5;
[/PHP]

---

### Post by WW on 2008-06-30
Check out the [wikipedia article about **new**](http://en.wikipedia.org/wiki/New_(C%2B%2B)).  To create an array of five pointers to integers:
```

int** p_parray = new int* [5];

```
Also, from the article,
> 
Initializers cannot be specified for arrays created with new. All elements of an array are initialized with the default constructor of the type. If the type does not have a default constructor, this is a compile-time error.


And, for kicks:

**newtest.cpp**
```

#include <iostream>

using namespace std;

int main(int argc, char *argv[])
    {
    // Create a new integer with the value 5
    int* p_scalar = new int(5);
    
    // Create an array of integers
    int* p_array = new int[5];
    
    // Create an array of pointers to integers
    int** p_parray = new  int* [5];
    
    for (int i = 0; i < 5; ++i)
        {
        p_array[i] = *p_scalar + i;
        p_parray[i] = p_array+i;
        }
    
    for (int i = 0; i < 5; ++i)
        {
        cout << "i=" << i << "  " << *(p_parray[i]) << endl;
        }
        
    return 0;
    }

```
Compile and run:
```

$ g++ -Wall newtest.cpp -o newtest
$ ./newtest 
i=0  5
i=1  6
i=2  7
i=3  8
i=4  9
$ 

```

---

### Post by Can+~ on 2008-06-30
> **Zeotronic said:**
> But I'm curious what the right method is to make a pointer array, which points to values which already exist? You see, I'm afraid if I do it wrong I'll have problems I cant explain.

Arrays are just blocks of memory on juxtaposition which you can iterate with pointer arithmetic [FONT="Courier New"]*(array+sizeof(type)*n)[/FONT] or using it's equivalent wrapper [FONT="Courier New"]array[n][/FONT]. So making a "pointer array" is pretty much any method suggested by **dwhitney67** (unless you mean making an array of pointers) .

And what do you mean with *"which points to values which already exist"*?

---

### Post by Zeotronic on 2008-06-30
> Perhaps you had a typo?
Yea, it was a typo. I wonder how I messed that up? :confused:
> perhaps something like the following?
That was the only thing I could think of... I just wanted to make sure that was the best way to do it... or even a viable way to do it.
> And what do you mean with "which points to values which already exist"? 
dwhitney67's last example is pretty well exactly what I mean... only instead of being ints... mine are already new'd int pointers to single values. (in actuality mine arn't ints at all, but its close enough for comparison)

---

