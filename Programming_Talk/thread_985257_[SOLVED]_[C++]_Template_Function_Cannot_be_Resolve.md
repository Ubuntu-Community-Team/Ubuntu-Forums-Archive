---
title: "[SOLVED] [C++] Template Function Cannot be Resolved"
date: 2008-11-17
forum: Programming Talk
---

### Post by dwhitney67 on 2008-11-17
I have the following free-floating function declared (and implemented); the implementation is not really important.
[php]
template<typename T, typename S>
void quicksort(T& array, size_t left, size_t right)
{
  ...
}
[/php]

I am trying to call this function using a call similar to the following:
[php]
quicksort<TokenOccurrence, std::string>(m_occurrences, (size_t)0, m_occurrences.size());
[/php]

I have also tried:
[php]
quicksort(m_occurrences, (size_t)0, m_occurrences.size());
[/php]

In either case, I cannot get my application to compile.  I get this error:
```

TokenFindings.cpp: In member function ‘void TokenFindings::sortOccurrences()’:
TokenFindings.cpp:40: error: no matching function for call to ‘quicksort(nonstd::vector<TokenOccurrence>&, size_t, size_t)’

```

How can I define the quicksort() function so that I can use it to sort different types of objects?

---

### Post by Npl on 2008-11-17
did you place the **implementation** of quicksort in the header?
A C++ compiler needs to compile a seperate quicksort-function for different template-parameters. So you need the whole thing in the header and not just a declaration.

---

### Post by dwhitney67 on 2008-11-17
> **Npl said:**
> did you place the **implementation** of quicksort in the header?
A C++ compiler needs to compile a seperate quicksort-function for different template-parameters. So you need the whole thing in the header and not just a declaration.
Yes I did; and the header file (QuickSort.h) is also included in TokenFindings.cpp.

---

### Post by Npl on 2008-11-17
Im not sure if the first version *quicksort<TokenOccurrence, std::string>(m_occurrences, (size_t)0, m_occurrences.size());* is valid.

The second version wont work because the compiler cant figure out the second type (how should it know?). If youre using STL-Containers you can do the following (I assume S is the type of objects to sort):
```
template< typename T, typename S = T::value_type > 
void quicksort(T& array, size_t left, size_t right) 
{ 
  ... 
} 
.
.
 quicksort(m_occurrences, (size_t)0, m_occurrences.size()); 

```

Or even better, just take S out of the template and use T::value_type where you need it

---

### Post by dwhitney67 on 2008-11-17
How does one get T::value_type to compile when say, the T represents an int?

---

### Post by Npl on 2008-11-17
> **dwhitney67 said:**
> How does one get T::value_type to compile when say, the T represents an int?why would you want to sort an Integer? How would you even do it? :)
The above only works if T is a class and has value_type defined - STL Containers like vector<int> fit that description.

I believe you meant the case when T = int* . For that you`d have to do a specialization (which I`m not fluent with). The next C++ standard revision plans to fix such issues by providing an "automatic type", you would just do something like "autotype p = T[0];" and it should work aslong T has an operator[].  

Besides you could look at std::sort, the most generic algorithms use Iterators so you dont have to differenciate between container-Classes and builtin Arrays.[/CODE]

---

### Post by dwhitney67 on 2008-11-17
> **Npl said:**
> why would you want to sort an Integer? How would you even do it? :)

Yes, that was a silly question.  I was initially testing with an int array.

I found out, after reading the error messages more carefully (and seeing a hint provided by g++), that the proper format within the implementation, is to use the typename keyword.

So,
[php]
template <typename T>
void quicksort(T& data, const size_t begin, const size_t end)
{
   ...
   typename T::value_type val = ...;
   ...
}
[/php]

I just got done completing an exercise where the use of STL containers (e.g. vector, map, list, etc.) were not permitted.

I had to use a home-made vector object, which I defined to be in the nonstd namespace.

Now if I could only get my quicksort() algorithm to work.  :-)

---

