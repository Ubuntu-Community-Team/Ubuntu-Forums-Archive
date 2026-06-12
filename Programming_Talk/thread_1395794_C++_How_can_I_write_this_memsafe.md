---
title: "C++: How can I write this memsafe?"
date: 2010-02-01
forum: Programming Talk
---

### Post by JFASI on 2010-02-01
Ok, so I am writing a sparse matrix class. I need to have a node class, which will be a template for its contents. Now I come from C, but most of my OO work has been in Java, so I need a bit of a primer on some of the features of C++. 

My issue in writing this class is: 

How do I store the links and the contents? 

The links I want to hold by pointer/reference (if someone could explain the subtleties of the reference, I'd be grateful). This is a linked list style implementation of the matrix, so I don't want to have them by value at all. 

However, the contents I want to store by value. If I stored it by pointer and it should be destroyed, then I'd have trouble. How can I safely perform a deep copy in the setContents method? 

I've looked into the copy constructor, but I have some qualms. What is the contained class does not implement a copy constructor? Then passing it to the node by reference would not be wise, since that could lead to a dangling reference. A shallow copy, however, is still not acceptable. 

What is the sort of "standard C++" way of doing this?

---

### Post by hessiess on 2010-02-01
If you want to create any sort of dynamic array(which, from your description it sounds like you do), use the std::vector or std::list template classes.

---

### Post by JFASI on 2010-02-01
I would, but the matrix needs both row *and* column operations, so I need to have two linked lists organizing the rows and the columns.

---

### Post by akvino on 2010-02-01
So why not make two dimensional vector?


```

std::vector<std::vector<mytype> > my_2d_int_array(SizeX, std::vector<mytype>(SizeY));

Example code:
#include <iostream>
#include <vector>

int main(int argc, char* argv[])
{
    int SizeX = 3;
    int SizeY = 5;
    std::vector<std::vector<int> > my_2d_int_array(SizeX, std::vector<int>(SizeY));

    int x, y;

    for(x = 0;x < my_2d_int_array.size();++x)
    {
        for(y = 0;y < my_2d_int_array[x].size();++y)
        {
            my_2d_int_array[x][y] = x*10 + y;
        }
    }

    for(x = 0;x < my_2d_int_array.size();++x)
    {
        for(y = 0;y < my_2d_int_array[x].size();++y)
        {
            std::cout << my_2d_int_array[x][y] << std::endl;
        }
    }
    return 0;
}
//The above method is simple, and requires no special class.

```

---

### Post by JFASI on 2010-02-01
That seems like a good method, but I'm not sure I trust/understand the vector data structure. I don't want to treat it as a black box is what I mean. 

Also, I'm coming from C, so I'm extremely prejudiced against using other people's data structures...

---

### Post by akvino on 2010-02-01
> **JFASI said:**
> That seems like a good method, but I'm not sure I trust/understand the vector data structure. I don't want to treat it as a black box is what I mean. 

Also, I'm coming from C, so I'm extremely prejudiced against using other people's data structures...

Vector is dynamic array. As data structure it is very similar to Linked List. Look it up on the wiki:

[http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29](http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29)



Overview of functions

The vector class models the Container concept, which means it has begin(), end(), size(), max_size(), empty(), and swap() methods.

    * informative
          o vector::front - Returns reference to first element of vector.
          o vector::back - Returns reference to last element of vector.
          o vector::size - Returns number of elements in the vector.
          o vector::empty - Returns true if vector has no elements.
          o vector::capacity - Returns current capacity (allocated memory) of vector.
    * standard operations
          o vector::insert - Inserts elements into a vector (single & range), shifts later elements up. O(n) time.
          o vector::push_back - Appends (inserts) an element to the end of a vector, allocating memory for it if necessary. Amortized O(1) time.
          o vector::erase - Deletes elements from a vector (single & range), shifts later elements down. O(n) time.
          o vector::pop_back - Erases the last element of the vector, O(1) time. Does not usually reduce the memory overhead of the vector. Amortized O(1) time.
          o vector::clear - Erases all of the elements. (For most STL implementations this is O(1) time and does not reduce capacity)
    * allocation/size modification
          o vector::reserve - Changes capacity (allocates more memory) of the vector, if needed. In many STL implementations capacity can only grow, and is never reduced. O(n) if the vector expands. O(1) if not.
          o vector::resize - Changes the vector size. O(n) time.
    * iteration
          o vector::begin - Returns an iterator to start traversal of the vector.
          o vector::end - Returns an iterator that points just beyond the end of the vector.

---

### Post by JFASI on 2010-02-01
I mean, I know what it does, I just don't want to be ignorant of implementation details. 

I suppose It wouldn't kill me to use Vector's though. In any case, look at it from the point of view of the language itself. How does C++ resolve such issues?

---

