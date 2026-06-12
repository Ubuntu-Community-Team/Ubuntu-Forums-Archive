---
title: "[C++] How to use qsort on an array of structs"
date: 2010-03-06
forum: Programming Talk
---

### Post by blooddrunk on 2010-03-06
Hi! I have an array of structs, which I want to sort.The struct looks like:

struct my_struct{
	int *number;
	long double *length;
};

As you can see the struct consists of arrays. I want to use qsort to sort each struct on its own (not caring about the other structs) in the struct array using the variable length as the key. How can I do that? Any help would be greatly appreciated.

---

### Post by NikitaUtiu on 2010-03-06
You include <algorithm>

and sort (mystruct.number, mystruct.number+numberof elemetns);
the number of elements in your case is *lenght 
it qsorts fro the first pointer to the second pointer
and you do it for each and every element

---

### Post by MadCow108 on 2010-03-06
write a compare function for qsort to use
qsort takes a function of this form:
int compare(const void*, const void*)
so it receives a pointer to the elements to be compared


you should be using sort instead of qsort in C++
its basically the same just easier and safer to use and more generic
[http://www.cplusplus.com/reference/algorithm/sort/](http://www.cplusplus.com/reference/algorithm/sort/)
sort takes functions and function objects as comparators.
The arguments are the objects to be compared (or references of these) instead of pointers

---

### Post by blooddrunk on 2010-03-06
Thanks for the quick reply!

Just one thing though. I have the length somewhere else. What I meant was that I want the elements in both the arrays numbers and length sorted depending on the values in length.
So, if they look like this:
numbers[3]={2,5,3}
length[3]={3,1,2}

After the sorting they should be:
numbers[3]={5,3,2}
length[3]={1,2,3}

I hope this makes my question clearer

Anyone?

---

### Post by dwhitney67 on 2010-03-06
When you need to associate two (or more) data items together, the best thing to do is to define a struct that encapsulates each of the items, so that you can maintain an array of these structs.

In other words, consider the following:
```

struct MyData
{
   int number;
   int length;
};

```
From here, you can define an array of MyData objects, or easier yet, since you are using C++, just use an STL vector.

Here's a complete example:
```

#include <vector>
#include <algorithm>
#include <iterator>
#include <iostream>


struct MyData
{
   MyData(int n, int l) : number(n), length(l) {}

   int number;
   int length;

   friend std::ostream& operator<<(std::ostream& os, const MyData& m)
   {
      os << "number: " << m.number << " " << "length: " << m.length;
      return os;
   }

   static bool MyDataSorter(const MyData& lhs, const MyData& rhs)
   {
      return lhs.length < rhs.length;
   }
};


int main(void)
{
   std::vector<MyData> myStructs;

   myStructs.push_back(MyData(2, 3));
   myStructs.push_back(MyData(5, 1));
   myStructs.push_back(MyData(3, 2));

   std::cout << "Before sorting:\n";
   std::copy(myStructs.begin(), myStructs.end(), std::ostream_iterator<MyData>(std::cout, "\n"));
   std::cout << std::endl;

   std::sort(myStructs.begin(), myStructs.end(), MyData::MyDataSorter);

   std::cout << "After sorting:\n";
   std::copy(myStructs.begin(), myStructs.end(), std::ostream_iterator<MyData>(std::cout, "\n"));
   std::cout << std::endl;
}

```

---

