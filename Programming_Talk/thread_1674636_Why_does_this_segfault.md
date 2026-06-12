---
title: "Why does this segfault?"
date: 2011-01-24
forum: Programming Talk
---

### Post by tommy1987 on 2011-01-24
Hi,

I'm learning C++ and fail to see why this program segfaults in the second for loop.

Any programming style or best practices that are missing from this snippet, please let me know :-)

```
#include <iostream>

using std::endl;    using std::cout;

static const int NUM_INTS = 100;

int main()
{
    // Allocate memory for an integer array
    int arr[NUM_INTS];

    // Populate the array
    for(int i = 0; i < NUM_INTS; ++i)
    {
        arr[i] = 10;
    }

    // Create pointer to array
    int *ptr_to_arr = arr;

    // Loop over array and print values (+ that of the pointer)
    for (int i = 0; i < NUM_INTS; ++i) {
        cout << i << arr[i] << endl;
        cout << i << ptr_to_arr[i] << endl;
    }

    // Free up the memory used in the array
    delete []ptr_to_arr;

    return 0;
}
```

Probably something simple...

---

### Post by slavik on 2011-01-24
you can't delete what is stored in the stack. if you didn't call new, don't call delete.

for every call to new, there must be a call to delete (and vice versa).

---

### Post by nickleboyblue on 2011-01-24
Just a suggestion:  instead of separating the "using" statements at the top of your program, put them all together:

```
using namespace std;
```

Unless you've gone beyond the beginning programmer stage, you will probably not be using anything outside of the std namespace.

Also, I compiled your code without the delete statement, and it works fine, EXCEPT that the output appears starts at 010, increments by 100 on every other iteration, and ends at 9910.  Actually, this isn't exactly what it's doing, but that's what it looks like.  In order to make the output more person-readable, label the output of "i" for each iteration and the output of the array for each iteration, and label the direct and pointer iterations separately.  Sample code:

```
for (int i = 0; i < NUM_INTS; ++i) {
        cout << "Iteration(direct): " << i << " Result: " << arr[i] << endl;
        cout << "Iteration(pointer): " << i << " Result: " << ptr_to_arr[i] << endl;
    }
```

---

### Post by tommy1987 on 2011-01-26
Thanks guys, it's clear for me now.

---

