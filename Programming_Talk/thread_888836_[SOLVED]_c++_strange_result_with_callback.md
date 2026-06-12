---
title: "[SOLVED] c++ strange result with callback"
date: 2008-08-13
forum: Programming Talk
---

### Post by lian1238 on 2008-08-13
Hi,

In my programming class in college, we're learning about generic programming and now we're using the callback feature in c++. We're implementing a "truly" generic Quicksort function which can sort any type, in any order (defined at runtime using callback). My problem is with the callback. Hard-coding the logic works for both orders, ascending and descending. But using callback, sorting in descending order results in an altered but unsorted array.

Please take a look at the file. I've described the "bug" inside the file under "notes". Please take some time to understand the problem and my testing method, and try compiling it yourself.

Tested with compilers: 
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
and
Dev-C++ 4.9.9.2
both with the exact same output.

Thanks so much in advance. I'll be extremely grateful if someone, anyone, can help me.

---

### Post by dwhitney67 on 2008-08-13
Prepare to kick yourself in the rear...

The errors you are having are because you neglected to pass OrderLogic to the recursive calls of quicksort().

Here's a snapshot of the changes:
[PHP]template <typename RITR, typename BPRED>
        void quicksort(RITR begin, RITR end, BPRED OrderLogic)
{
...
                quicksort(midpoint+1, end, OrderLogic);  // <-- Here!
                quicksort(begin, midpoint-1, OrderLogic);  // <-- Here!

                #ifdef DEBUG_MSG
                cout << "after 1st recursion of QS: ";
                print(begin, end-begin+1);
                #endif

                quicksort(midpoint+1, end, OrderLogic);  // <-- Here!
...
}[/PHP]

---

### Post by lian1238 on 2008-08-13
Oh my.. Wow, **dwhitney67**, thanks!! I guess I was too focused on partition, I totally overlooked quicksort. I actually created a new bug while putting in the debugging message. There should be only two recursive calls. Thanks so much for finding this bug! You rock! :guitar:
I'll put the fixed version up for reference.

Thanks again!

---

### Post by dwhitney67 on 2008-08-14
Hey, I spent an hour looking over your code, especially in the partition() function.  Silly me... I should have looked top-down... starting from main(). then going to quicksort(), then etc.

I spent a lot of time looking over your code, trying to understand it (in an 80x24 terminal), and still it is difficult to get a grasp around it.  I understand that you are implementing a quicksort algorithm, but that is something I have not studied since my sophomore year in college (1987).

For sorting something as simple as an array of integers, one could use qsort(), to do something similar to:
[PHP]#include <cstdlib>
#include <iostream>

int ascending( const void *val1, const void *val2 )
{
  const int *v1 = reinterpret_cast<const int *>(val1);
  const int *v2 = reinterpret_cast<const int *>(val2);

  if ( *v1 < *v2 )
    return -1;

  if ( *v1 == *v2 )
    return 0;

  return 1;
}

int descending( const void *val1, const void *val2 )
{
  const int *v1 = reinterpret_cast<const int *>(val1);
  const int *v2 = reinterpret_cast<const int *>(val2);

  if ( *v1 < *v2 )
    return 1;

  if ( *v1 == *v2 )
    return 0;

  return -1;
}

template<typename T>
void printArray( T *arr, size_t size )
{
  for ( size_t i = 0; i < size; ++i )
  {
    std::cout << arr[i] << " ";
  }
  std::cout << std::endl;
}

int main()
{
  int arr[5] = { 3, 4, 5, 2, 1 };

  std::cout << "original  : ";
  printArray( arr, sizeof(arr)/sizeof(int) );

  qsort( arr, sizeof(arr)/sizeof(int), sizeof(int), ascending );
  std::cout << "ascending : ";
  printArray( arr, sizeof(arr)/sizeof(int) );

  qsort( arr, sizeof(arr)/sizeof(int), sizeof(int), descending );
  std::cout << "descending: ";
  printArray( arr, sizeof(arr)/sizeof(int) );

  return 0;
}[/PHP]

As for your code, what really confused me is the naming conventions chosen for variables.  Normally, I would preface a class (or object) type with an upper case letter, and start a variable name with a lower case letter.  When I saw OrderLogic, I was expecting a functor object... and it took me awhile to realize that no, it is a variable name!  I only wish that I had save myself countless minutes searching for quicksort() to determine what type of entity was OrderLogic.  To reiterate again... I should have examined your code from the top and progressed methodically towards the end.

Anyhow, I am glad I was of help.  Perhaps if you remove the templated function for quicksort(), that accepts two parameters, your problems could have been solved on your own.

---

### Post by lian1238 on 2008-08-14
Sorry I had wasted your time so much. I thought I was passing in functors.
 
[php]
/****** Functors ********/
class LessThan
{
public:
template <typename T>
bool operator() (const T &a, const T &b)
{ return a < b ? true:false;}
};
class MoreThan
{
public:
template <typename T>
bool operator() (const T &a, const T &b)
{return a > b ? true:false;}
};
/***** order logics of quicksort ***/
MoreThan ascending;
LessThan descending;
[/php]I declared the two functors and pass them into quicksort to determine the order. You're correct in saying I would have found the error if I hadn't overloaded the quicksort function with two variables. I shoulda known. I spent 2 days debugging this. How could I have missed it?
 
Thanks for the simpler code you showed me. I'll be sure to learn how to use it when I get home. :)

Edit: I've talked to my professor today and he said generally, we don't declare variables like I did to specify the order. Instead, we call the constructor of the functor.
[php]
quicksort(begin, end, MoreThan());
[/php]
Another thing is, I should use the lessthan logic to sort in ascending order, as a standard.

---

