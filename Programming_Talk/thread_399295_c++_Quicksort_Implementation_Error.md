---
title: "c++ Quicksort Implementation Error"
date: 2007-04-02
forum: Programming Talk
---

### Post by fabulous_mr_e on 2007-04-02
Hello there, I'm fairly new to c++ programming and am trying to implement a quicksort routine I've adapted from Java.
The swap function works fine when run from the main function, but when I try to use it within the quicksort function it returns the folllowing error:

error: no matching function for call to ‘swap(int*&, int&, int&)’

I assume this is a problem with the pointers used as arguments. But i'll be damned if I can work out the exact problem. If someone could have a look and tell me where I went wrong i'd very much appreciate it.

```
void quicksort(int[],int,int);

void quicksort(int newarray[], int start, int end)
{
	int l = start;
	int r = end;
	int pivot = newarray[(start+end)/2];
	if(start >= end) return;
	while (l < r) 
	{
     	while (l<r && newarray[l] < pivot) l++;
        while (l<r &&newarray[r] >= pivot) r--;
        if (l < r) swap(newarray,l,r);
	}
	if(r<l) swap(newarray, r,l);
	quicksort(newarray, start, l);
	quicksort(newarray, r, end);
}

void swap(int array[], int first, int second)
{
	int temp = array[first];
	array[first] = array[second]; 
	array[second] = temp;
}

int main()
{
	int myArray[] = {9,4,6,8,3,1,2,7,5};
	swap(myArray, 0, 1);
	cout << myArray[0] << myArray[1];
	quicksort(myArray, 0, 8);
	return 0;
}
```

---

### Post by kpatz on 2007-04-02
You forgot to declare the function swap at the top.  Add these lines to the top of the program and then it'll compile:

#include <iostream>
using namespace std;

void swap(int array[], int first, int second);

However, I got a segfault in the quicksort routine, so something isn't right there yet.

---

### Post by hod139 on 2007-04-02
As kpatz pointed out, there is a bug in your quicksort routine.  If you want some help debugging, just post back here; I have a feeling this is a homework assignment and I don't want to paste the answer.

Also, I was wondering if I could make some general comments about the code?

---

### Post by kpatz on 2007-04-02
FYI, in addition to bugs in the code, the quicksort algorithm you're using is flawed.  I found the same Java code on the web and ported it myself, and got the same incorrect results.  So if you're trying to build a working quicksort using that code, it doesn't work.

If you post that it isn't a homework assignment, I'll post the fixes to make it match the Java routine, incorrect as it is.

---

### Post by fabulous_mr_e on 2007-04-03
Thank you for your help. 
I had kind of assumed it was flawed, I think when I copied it into java I needed to mess around with it anyway. I needed to get around the failure to compile before I debugged it. 

It's not a homework assignment, I just really like quicksort. I also wanted the challenge of getting it working myself. I was taught Java at university and wanted to move onto a language I could write my final year engineering project in. Thank you for your offers of assistance though.

---

### Post by Arndt on 2007-04-03
> **fabulous_mr_e said:**
> Thank you for your help. 
I had kind of assumed it was flawed, I think when I copied it into java I needed to mess around with it anyway. I needed to get around the failure to compile before I debugged it. 

It's not a homework assignment, I just really like quicksort. I also wanted the challenge of getting it working myself. I was taught Java at university and wanted to move onto a language I could write my final year engineering project in. Thank you for your offers of assistance though.

Mergesort is better. To begin with, it's stable.

---

### Post by Wybiral on 2007-04-03
If you like quicksort, you can always use qsort. It's part of the C standard library, so it's not exactly the most C++ way of doing it, but it will work (and pretty quickly too).

---

### Post by hod139 on 2007-04-03
> **Arndt said:**
> Mergesort is better. To begin with, it's stable.

Mergesort is very good, but there are far more issues at hand than stability (whatever your definition of stability means).  What I will agree with is that mergesort uses the fewest comparisons of the popular sorting algorithms.  This is great if comparisons are expensive and moves cheap (e.g. Java).  However, in C++ comparisons will be faster than copying large objects (compiler can inline aggressively, etc) and an algorithm with more comparisons but less swaps will be better (e.g. quicksort).  

This is why mergesort is favored in java and [introsort]("http://www.cs.rpi.edu/%7Emusser/gp/index_1.html") is used in the C++ STL (at least SGI's and STLports implementations.  I'm not 100% sure about GCC.).  From the linked article "a new, hybrid sorting algorithm, *introsort* (for *introspective sort*), that behaves almost exactly like median-of-3 quicksort for most inputs (and is just as fast) but which is capable of detecting when partitioning is tending toward quadratic behavior. By switching to heapsort in those situations, introsort achieves the same *O(N logN)* time bound as heapsort but is almost always faster than just using heapsort in the first place."

---

### Post by hod139 on 2007-04-03
> **fabulous_mr_e said:**
> Thank you for your help. 
It's not a homework assignment, I just really like quicksort. I also wanted the challenge of getting it working myself. I was taught Java at university and wanted to move onto a language I could write my final year engineering project in. Thank you for your offers of assistance though.

I'm assuming you want to write quicksort as an exercise, because as Wybrial pointed out it already exists in C and it also exists as introsort (see an earlier post) in C++.   Anyways, I'll write down the basic idea of quicksort:  Given an container C
1. If size of C is 0 or 1, return
2. Pick a pivot element v in C
3. Partition C - {v} (the remaining elements of the container) into two sets, S1 is all elements less that the pivot, S2 is all elements greater than the pivot.
4. return quicksort(S1) , v , quicksort(S2)


For step 2, your algorithm picked the worst possible thing you can do.  You need to look up median-of-three partitioning (ask if you want more help).

The implementation of parts 3 and 4 is also wrong.  Below is code that works (**but not recommended to actually use**) with minimal changes from your posted code:
```

void swap(int array[], int first, int second)
{
    int temp = array[first];
    array[first] = array[second]; 
    array[second] = temp;
}

void quicksort(int newarray[], int start, int end)
{
    if(start >= end) return;

    int l = start;
    int r = end - 1;
    int center = (start+end)/2;
    int pivot = newarray[center];
    swap(newarray, center, end); //place pivot at end
      
    while (true) 
    {
          while (newarray[l] < pivot) ++l;
          while (newarray[r] > pivot) --r;
          if (l < r) 
             swap(newarray,l,r);
          else 
             break;
    }
    swap(newarray, l, end); // restore pivot

    quicksort(newarray, start, l-1);
    quicksort(newarray, l+1, end);
}

```As I said earlier, the pivoting selection here is horrible, and you really don't want to use it.  Also, you should consider writing a swap function that doesn't have to pass the entire array, something like:
```

template <class T>
inline void swap( T &obj1, T &obj2 )
{
  T tmp = obj1;
  obj1 = obj2;
  obj2 = tmp;
}

```Also, if this is C++, why don't you write the code to work on a vector, which will simplify the memory handling.  Also, it can be made generic to work on types other than int. 
```

template <typename T>
void quicksort(vector<T> &array, int start, int end)

```Lastly, typically when the array (or vector) size drops below 10, quicksort stops and insertion sort is called.  Insertion sort works faster than quicksort on small array.  So it would look something like:
```

template <typename T>
 void quicksort(vector<T> &array, int start, int end)
{
  if(start + 10 <= end)
  { // quicksort


  }
  else // do an insertion sort
    insertionSort(array, start, end)
} 

```I leave it to you to fill in the rest.  Post back if anything I've said is unclear.

---

### Post by Jmccaffrey on 2007-04-03
One note about merge sort, while it is indeed fast, it cannot compare arbitrary structures and is therefore of limited use unless you create very customized sort functions for each purpose.  More general sort routines can compare anything that can be evaluated with the ">" operator, and therefore are more applicable to real life scenarios.

---

### Post by hod139 on 2007-04-03
> **Jmccaffrey said:**
> One note about merge sort, while it is indeed fast, it cannot compare arbitrary structures and is therefore of limited use unless you create very customized sort functions for each purpose.  More general sort routines can compare anything that can be evaluated with the ">" operator, and therefore are more applicable to real life scenarios.
I don't understand what you mean here.  All sorting algorithms by their nature require that the items being sorted can be partially ordered (that is you can apply the <= operation).  As long as the items can be "compared" (technically partially ordered), any sorting algorithm will work, including merge sort.

---

