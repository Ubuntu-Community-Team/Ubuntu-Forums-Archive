---
title: "missing something subtle on a canned templated function."
date: 2011-04-22
forum: Programming Talk
---

### Post by Jonas thomas on 2011-04-22
I think I'm missing something obvious here...

```
    bool item::placeBid(const string & bidder,const date &bidDate, const double&BidAmount) //*17*

{

    bid *bids;
    bids = new bid[numBids+1]; // *11*
    for (int i =0;i<numBids;i++)
        bids[i]=bidPointer[i];//Need to put the old bids into the new bids
    bids[numBids].amount=BidAmount;
    bids[numBids].bidDate=bidDate;
    bids[numBids].biddersName=bidder;
    numBids++;
    ***selectionSort(bids,numBids);***

    delete []bidPointer;
    bidPointer= bids;// This is ultimately removed by the destructor *13*
    return (true);
}
```

I'm getting this error on the selectionSort

> obj/Debug/item.o||In function `item::placeBid(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, date const&, double const&)':|
/media/0AFD-2985/Project02/item.cpp|186|undefined reference to `void selectionSort<bid>(bid*, int)'|
||=== Build finished: 1 errors, 0 warnings (0 minutes, 1 seconds) ===|

The function prototypes I've been given look like this:
```

// sort an integer array using selection sort
void selectionSort(int arr[], int n);

[B][I]// sort an array of type T using selection sort
template <typename T>
void selectionSort(T arr[], int n);[/I][/B]

// sort a vector of type T using selection sort
template <typename T>
void selectionSort(vector<T>& v);

// sort a vector of type T using insertion sort
template <typename T>
void insertionSort(vector<T>& v);

// sort the elements of a vector of type T in the range
// [first, last) using insertion sort
template <typename T>
void insertionSort(vector<T>& v, int first, int last);
```

I think I'm doing this correctly... Obviously, I'm missing something...
:confused:  Anyone?

---

### Post by dwhitney67 on 2011-04-22
Does the (header) file that defines the prototype functions contain the implementation of these functions?  It should.

---

### Post by jimi_hendrix on 2011-04-22
Try placing the implementation of the functions with templates in the header.

Edit: Looks like dwhitney67 beat me to it.

---

### Post by Jonas thomas on 2011-04-22
> **jimi_hendrix said:**
> Try placing the implementation of the functions with templates in the header.

Edit: Looks like dwhitney67 beat me to it.

Well textbook author actually had the declaration and implementation in the same header file.  It was driving me nuts because I was getting compiler errors with duplicated definitions so I split it apart declaration and implentation apart...

But... I'm pretty sure that the cpp correctly...
basically...

```
#include "d_sort_split.h"

// IMPLEMENTATIONS

void selectionSort(int arr[], int n)
{
   int smallIndex; // index of smallest element in the sublist
   int pass, j;
	int temp;

   // pass has the range 0 to n-2
   for (pass = 0; pass < n-1; pass++)
   {
		// scan the sublist starting at index pass
		smallIndex = pass;

		// j traverses the sublist arr[pass+1] to arr[n-1]
		for (j = pass+1; j < n; j++)
         // update if smaller element found
			if (arr[j] < arr[smallIndex])
				smallIndex = j;

		// if smallIndex and pass are not the same location,
		// exchange the smallest item in the sublist with arr[pass]
		if (smallIndex != pass)
		{
			temp = arr[pass];
			arr[pass] = arr[smallIndex];
			arr[smallIndex] = temp;
		}
	}
}

[B][I]template <typename T>
void selectionSort(T arr[], int n)
{
   int smallIndex; // index of smallest element in the sublist
   int pass, j;
	T temp;

   // pass has the range 0 to n-2
   for (pass = 0; pass < n-1; pass++)
   {
		// scan the sublist starting at index pass
		smallIndex = pass;

		// j traverses the sublist arr[pass+1] to arr[n-1]
		for (j = pass+1; j < n; j++)
         // update if smaller element found
			if (arr[j] < arr[smallIndex])
				smallIndex = j;

		// if smallIndex and pass are not the same location,
		// exchange the smallest item in the sublist with arr[pass]
		if (smallIndex != pass)
		{
			temp = arr[pass];
			arr[pass] = arr[smallIndex];
			arr[smallIndex] = temp;
		}
	}
}[/I][/B]
```

Are you guys saying I can't do that or did I screw something up on an include?? (I know there has been some errors in the authors code from changes in the C++ standard... I don't think that's whats going on here??)

---

### Post by jimi_hendrix on 2011-04-22
The issue has to do with forward declarations. If you were to split the implementation and the declaration of template functions, you would have to forward declare for every type that might be used.

---

### Post by dwhitney67 on 2011-04-22
> **Jonas thomas said:**
> 
Are you guys saying I can't do that...

Yes.

You have two choices...

1.  Prototype and implement the tempated functions in the same header file;

or

2.  Prototype the templated functions in the header file, and then within the same header file, include a file (preferably w/o a .cpp extension) that contains the function implementations.

Typically option 1 is used.

---

### Post by Jonas thomas on 2011-04-22
> **jimi_hendrix said:**
> The issue has to do with forward declarations. If you were to split the implementation and the declaration of template functions, you would have to forward declare for every type that might be used.

Huh??
Hoisted up by my own petards once again  ;(

Sooo.. If I'm running into compiler errors from duplicate definitions from declaration and implementation being in the same header file, the solution is split apart and to forward declare??

---

### Post by Jonas thomas on 2011-04-22
Are you saying I need to put an extern in somewhere and everything else should be good.  Let me try that.

---

### Post by dwhitney67 on 2011-04-22
> **Jonas thomas said:**
> Huh??
Hoisted up by my own petards once again  ;(

Sooo.. If I'm running into compiler errors from duplicate definitions from declaration and implementation being in the same header file, the solution is split apart and to forward declare??

Keep things simple; for example:

```

#ifndef MY_TEMPLATES_H
#define MY_TEMPLATES_H

template <typename T>
void someFunction(T& tobj)
{
   // do something here
}

#endif

```

---

### Post by Jonas thomas on 2011-04-22
> **dwhitney67 said:**
> Keep things simple; for example:

> 
[B][I]#ifndef MY_TEMPLATES_H
#define MY_TEMPLATES_H[/I][/B]

template <typename T>
void someFunction(T& tobj)
{
   // do something here
}

#endif
[/code]



The authors code had this in the original combined header...

#ifdef __BORLANDC__
// turn off Borland warning message about comparison of signed and
// unsigned values
#pragma warn -8012
#endif	// __BORLANDC__

[B][I]#ifndef SORTING_ALGORITHMS
#define SORTING_ALGORITHMS

[/I][/B]#include <vector>
#include <queue>

#include "d_heap.h"	// heap function library

[/QUOTE]

Which I think did that... But I was getting errors.. Which I thought I could eliminate by splitting the declaration and implementation.
I can go back to that and post the errors if you want??```

```

---

### Post by dwhitney67 on 2011-04-22
> **Jonas thomas said:**
> 
I can go back to that and post the errors if you want??```

```

Yes, I would recommend that.  If there are errors, it could be that you had a typo, or the authors had a typo, or their code is obsolete compared to today's standards.

Alternatively, you could just start out by implementing the header file with the template declaration, and as far as the selectionSort() function, don't do anything within it for now.  This will at least confirm that your application will compile.

SortingAlgorithms.h:
```

#ifndef SORTING_ALGORITHMS_H
#define SORTING_ALGORITHMS_H

...

template <typename T>
void selectionSort(T arr[], int n)
{
   // TODO
}

...
#endif

```

---

### Post by Jonas thomas on 2011-04-22
when I go back to the authors original d_sort.h file.. I get these errors.

```
/media/0AFD-2985/Project02/d_sort.h||In function ‘void distribute(const std::vector<int, std::allocator<int> >&, std::queue<int, std::deque<int, std::allocator<int> > >*, int)’:|
/media/0AFD-2985/Project02/d_sort.h|234|warning: comparison between signed and unsigned integer expressions|
/media/0AFD-2985/Project02/d_sort.h||In function ‘void distribute(const std::vector<int, std::allocator<int> >&, std::queue<int, std::deque<int, std::allocator<int> > >*, int)’:|
/media/0AFD-2985/Project02/d_sort.h|234|warning: comparison between signed and unsigned integer expressions|
obj/Debug/main.o||In function `selectionSort(int*, int)':|
/usr/include/c++/4.4/new|101|multiple definition of `selectionSort(int*, int)'|
obj/Debug/item.o:/media/0AFD-2985/Project02/d_sort.h|73|first defined here|
obj/Debug/main.o||In function `distribute(std::vector<int, std::allocator<int> > const&, std::queue<int, std::deque<int, std::allocator<int> > >*, int)':|
/media/0AFD-2985/Project02/d_sort.h|229|multiple definition of `distribute(std::vector<int, std::allocator<int> > const&, std::queue<int, std::deque<int, std::allocator<int> > >*, int)'|
obj/Debug/item.o:/media/0AFD-2985/Project02/d_sort.h|229|first defined here|
obj/Debug/main.o||In function `collect(std::queue<int, std::deque<int, std::allocator<int> > >*, std::vector<int, std::allocator<int> >&)':|
/media/0AFD-2985/Project02/d_sort.h|241|multiple definition of `collect(std::queue<int, std::deque<int, std::allocator<int> > >*, std::vector<int, std::allocator<int> >&)'|
obj/Debug/item.o:/media/0AFD-2985/Project02/d_sort.h|241|first defined here|
obj/Debug/main.o||In function `radixSort(std::vector<int, std::allocator<int> >&, int)':|
/media/0AFD-2985/Project02/d_sort.h|257|multiple definition of `radixSort(std::vector<int, std::allocator<int> >&, int)'|
obj/Debug/item.o:/media/0AFD-2985/Project02/d_sort.h|257|first defined here|
||=== Build finished: 8 errors, 2 warnings (0 minutes, 3 seconds) ===|
```

Dwhitney I think what you proposed is what the Author did... Which would work if I can my project in basically one header and main.. Correct or am I missing something??

---

### Post by Jonas thomas on 2011-04-22
Ok.. Some questions here..
If this was production code using a templated function.. Would the implementation and declaration be generally combined or split..  I'm thinking probably combined since otherwise you'd need to forward declare which would limit the usefulness of the template??  I'm thinking I'm not understanding forward declaration??

---

### Post by jimi_hendrix on 2011-04-22
It seems that certain functions are being defined multiple times. Can you show more code?

Also, the first four lines involve warnings for comparisons between signed and unsigned ints. A simple cast should fix those.


> **Jonas thomas said:**
> Ok.. Some questions here..
If this was production code using a templated function.. Would the implementation and declaration be generally combined or split..  I'm thinking probably combined since otherwise you'd need to forward declare which would limit the usefulness of the template??  I'm thinking I'm not understanding forward declaration??

They would be combined in the header. Take the Boost Library for example. Most of what it provides involves templates and they are all implemented in the header files.

---

### Post by Jonas thomas on 2011-04-22
> **jimi_hendrix said:**
> It seems that certain functions are being defined multiple times. Can you show more code?

Also, the first four lines involve warnings for comparisons between signed and unsigned ints. A simple cast should fix those.




They would be combined in the header. Take the Boost Library for example. Most of what it provides involves templates and they are all implemented in the header files.

Ok... By more code I'm assuming you mean the authors d_sort.h
here it is:
In class things usually labs usually work when we keep everything to one cpp and header... It just goes against the grain for me to do that I a large project.

```

#ifdef __BORLANDC__

// turn off Borland warning message about comparison of signed and

// unsigned values

#pragma warn -8012

#endif	// __BORLANDC__



#ifndef SORTING_ALGORITHMS

#define SORTING_ALGORITHMS



#include <vector>

#include <queue>



#include "d_heap.h"	// heap function library



using namespace std;



// sort an integer array using selection sort

void selectionSort(int arr[], int n);



// sort an array of type T using selection sort

template <typename T>

void selectionSort(T arr[], int n);



// sort a vector of type T using selection sort

template <typename T>

void selectionSort(vector<T>& v);



// sort a vector of type T using insertion sort

template <typename T>

void insertionSort(vector<T>& v);



// sort the elements of a vector of type T in the range

// [first, last) using insertion sort

template <typename T>

void insertionSort(vector<T>& v, int first, int last);



// sort v using the radix sort. each integer has d digits

void radixSort(vector<int>& v, int d);



// sort a vector using heapsort

template <typename T, typename Compare>

void heapSort (vector<T>& v, Compare comp);



// the elements in the ranges [first,mid) and [mid,last) are

// ordered. the function merges the ordered sequences into

// an ordered sequence in the range [first,last)

template <typename T>

void merge(vector<T>& v, int first, int mid, int last);



// sorts v in the index range [first,last) by merging

// ordered sublists

template <typename T>

void mergeSort(vector<T>& v, int first, int last);



// using the value at the midpoint of [first,last) as the pivot,

// locate the pivot in its final location so all elements

// to its left are <= to its value and all elements to the

// right are >= to its value. return the index of the pivot

template <typename T>

int pivotIndex(vector<T>& v, int first, int last);



// sort a vector using quicksort

template <typename T>

void quicksort(vector<T>& v, int first, int last);



// locate the kth largest element of v at index k

template <typename T>

void findK(vector<T>& v, int first, int last, int k);



// IMPLEMENTATIONS



void selectionSort(int arr[], int n)

{

   int smallIndex; // index of smallest element in the sublist

   int pass, j;

	int temp;



   // pass has the range 0 to n-2

   for (pass = 0; pass < n-1; pass++)

   {

		// scan the sublist starting at index pass

		smallIndex = pass;



		// j traverses the sublist arr[pass+1] to arr[n-1]

		for (j = pass+1; j < n; j++)

         // update if smaller element found

			if (arr[j] < arr[smallIndex])

				smallIndex = j;



		// if smallIndex and pass are not the same location,

		// exchange the smallest item in the sublist with arr[pass]

		if (smallIndex != pass)

		{

			temp = arr[pass];

			arr[pass] = arr[smallIndex];

			arr[smallIndex] = temp;

		}

	}

}



template <typename T>

void selectionSort(T arr[], int n)

{

   int smallIndex; // index of smallest element in the sublist

   int pass, j;

	T temp;



   // pass has the range 0 to n-2

   for (pass = 0; pass < n-1; pass++)

   {

		// scan the sublist starting at index pass

		smallIndex = pass;



		// j traverses the sublist arr[pass+1] to arr[n-1]

		for (j = pass+1; j < n; j++)

         // update if smaller element found

			if (arr[j] < arr[smallIndex])

				smallIndex = j;



		// if smallIndex and pass are not the same location,

		// exchange the smallest item in the sublist with arr[pass]

		if (smallIndex != pass)

		{

			temp = arr[pass];

			arr[pass] = arr[smallIndex];

			arr[smallIndex] = temp;

		}

	}

}



template <typename T>

void selectionSort(vector<T>& v)

{

   // index of smallest item in each pass

	int smallIndex;

	// save the vector size in n

	int pass, j, n = v.size();

	T temp;



	// sort v[0]..v[n-2], and arr[n-1] is in place

	for (pass = 0; pass < n-1; pass++)

	{

		// start the scan at index pass; set smallIndex to pass

		smallIndex = pass;

		// j scans the sublist v[pass+1]..v[n-1]

      for (j = pass+1; j < n; j++)

         // update smallIndex if smaller element is found

         if (v[j] < v[smallIndex])

            smallIndex = j;

      // when finished, place smallest item in arr[pass]

      if (smallIndex != pass)

		{

			temp = v[pass];

			v[pass] = v[smallIndex];

			v[smallIndex] = temp;

		}

   }

}



template <typename T>

void insertionSort(vector<T>& v)

{

   int i, j, n = v.size();

   T target;



	// place v[i] into the sublist

	//   v[0] ... v[i-1], 1 <= i < n,

	// so it is in the correct position

   for (i = 1; i < n; i++)

   {

      // index j scans down list from v[i] looking for

      // correct position to locate target. assigns it to

      // v[j]

      j = i;

      target = v[i];

      // locate insertion point by scanning downward as long

      // as target < v[j-1] and we have not encountered the

      // beginning of the list

      while (j > 0 && target < v[j-1])

      {

         // shift elements up list to make room for insertion

         v[j] = v[j-1];

         j--;

      }

      // the location is found; insert target

      v[j] = target;

   }

}



template <typename T>

void insertionSort(vector<T>& v, int first, int last)

{

   int i, j;

   T target;



	// place v[i] into the sublist

	//   v[first] ... v[i-1], first <= i < last,

	// so it is in the correct position

   for (i = first+1; i < last; i++)

   {

      // index j scans down list from v[i] looking for

      // correct position to locate target. assigns it to

      // v[j]

      j = i;

      target = v[i];

      // locate insertion point by scanning downward as long

      // as target < v[j-1] and we have not encountered the

      // beginning of the range

      while (j > first && target < v[j-1])

      {

         // shift elements up list to make room for insertion

         v[j] = v[j-1];

         j--;

      }

      // the location is found; insert target

      v[j] = target;

   }

}



// support function for radixSort()

// distribute vector elements into one of 10 queues

// using the digit corresponding to power

//   power = 1    ==> 1's digit

//   power = 10   ==> 10's digit

//   power = 100  ==> 100's digit

//   ...

void distribute(const vector<int>& v, queue<int> digitQueue[],

                int power)

{

	int i;



	// loop through the vector, inserting each element into

	// the queue (v[i] / power) % 10

	for (i = 0; i < v.size(); i++)

		digitQueue[(v[i] / power) % 10].push(v[i]);

}



// support function for radixSort()

// gather elements from the queues and copy back to the vector

void collect(queue<int> digitQueue[], vector<int>& v)

{

	int i = 0, digit;



	// scan the vector of queues using indices 0, 1, 2, etc.

	for (digit = 0; digit < 10; digit++)

		// collect items until queue empty and copy items back

		// to the vector

		while (!digitQueue[digit].empty())

		{

			v[i] = digitQueue[digit].front();

			digitQueue[digit].pop();

			i++;

		}

}



void radixSort(vector<int>& v, int d)

{

	int i;

	int power = 1;

	queue<int> digitQueue[10];



	for (i=0;i < d;i++)

	{

		distribute(v, digitQueue, power);

		collect(digitQueue, v);

		power *= 10;

	}

}



template <typename T, typename Compare>

void heapSort (vector<T>& v, Compare comp)

{

	// "heapify" the vector v

	makeHeap(v, comp);



	int i, n = v.size();



	// iteration that determines elements v[n-1] ... v[1]

	for(i = n; i > 1;i--)

	{

		// call popHeap() to move next largest to v[n-1]

		popHeap(v, i, comp);

	}

}



template <typename T>

void merge(vector<T>& v, int first, int mid, int last)

{

	// temporary vector to merge the sorted sublists

	vector<T> tempVector;

	int indexA, indexB, indexV;



	// set indexA to scan sublistA (index range [first,mid)

	// and indexB to scan sublistB (index range [mid, last)

	indexA = first;

	indexB = mid;



	// while both sublists are not exhausted, compare v[indexA] and

	// v[indexB]copy the smaller to vector temp using push_back()

	while (indexA < mid && indexB < last)

		if (v[indexA] < v[indexB])

		{

			tempVector.push_back(v[indexA]);	// copy element to temp

			indexA++;								// increment indexA

		}

		else

		{

			tempVector.push_back(v[indexB]);	// copy element to temp

			indexB++;								// increment indexB

		}



	// copy the tail of the sublist that is not exhausted

	while (indexA < mid)

	{

		tempVector.push_back(v[indexA]);

		indexA++;

	}



	while (indexB < last)

	{

		tempVector.push_back(v[indexB]);

		indexB++;

	}



	// copy vector tempVector using indexV to vector v using indexA

	// which is initially set to first

	indexA = first;



	// copy elements from temporary vector to original list

	for (indexV = 0; indexV < tempVector.size(); indexV++)

	{

		v[indexA] = tempVector [indexV];

		indexA++;

	}

}



// sorts v in the index range [first,last) by merging

// ordered sublists

template <typename T>

void mergeSort(vector<T>& v, int first, int last)

{

	// if the sublist has more than 1 element continue

	if (first + 1 < last)

  {

		// for sublists of size 2 or more, call mergeSort()

		// for the left and right sublists and then

		// merge the sorted sublists using merge()

		int midpt = (last + first) / 2;



		mergeSort(v, first, midpt);

		mergeSort(v, midpt, last);

		merge(v, first, midpt, last);

   }

}





template <typename T>

int pivotIndex(vector<T>& v, int first, int last)

{

	// index for the midpoint of [first,last) and the

	// indices that scan the index range in tandem

	int mid, scanUp, scanDown;

	// pivot value and object used for exchanges

	T pivot, temp;



	if (first == last)

		return last;

	else if (first == last-1)

		return first;

	else

	{

		mid = (last + first)/2;

		pivot = v[mid];



		// exchange the pivot and the low end of the range

		// and initialize the indices scanUp and scanDown.

		v[mid] = v[first];

		v[first] = pivot;



		scanUp = first + 1;

		scanDown = last - 1;



		// manage the indices to locate elements that are in

		// the wrong sublist; stop when scanDown <= scanUp

		for(;;)

		{

			// move up lower sublist; stop when scanUp enters

			// upper sublist or identifies an element >= pivot

			while (scanUp <= scanDown && v[scanUp] < pivot)

				scanUp++;



			// scan down upper sublist; stop when scanDown locates

			// an element <= pivot; we guarantee we stop at arr[first]

			while (pivot < v[scanDown])

				scanDown--;



			// if indices are not in their sublists, partition complete

			if (scanUp >= scanDown)

				break;



			// indices are still in their sublists and identify

			// two elements in wrong sublists. exchange

			temp = v[scanUp];

			v[scanUp] = v[scanDown];

			v[scanDown] = temp;



			scanUp++;

			scanDown--;

		}



		// copy pivot to index (scanDown) that partitions sublists

		// and return scanDown

		v[first] = v[scanDown];

		v[scanDown] = pivot;

		return scanDown;

	}

}



template <typename T>

void quicksort(vector<T>& v, int first, int last)

{

   // index of the pivot

   int pivotLoc;

	// temp used for an exchange when [first,last) has

	// two elements

	T temp;



   // if the range is not at least two elements, return

   if (last - first <= 1)

		return;



	// if sublist has two elements, compare v[first] and

	// v[last-1] and exchange if necessary

   else if (last - first == 2)

	{

		if (v[last-1] < v[first])

		{

			temp = v[last-1];

			v[last-1] = v[first];

			v[first] = temp;

		}

		return;

	}

   else

	{

		pivotLoc = pivotIndex(v, first, last);



		// make the recursive call

		quicksort(v, first, pivotLoc);



		// make the recursive call

		quicksort(v, pivotLoc +1, last);

	}

}



template <typename T>

void findK(vector<T>& v, int first, int last, int k)

{

	int index;



	// partition range [first,last) in v about the

	// pivot v[index]

	index = pivotIndex(v, first, last);



	// if index == k, we are done. kth largest is v[k]

	if (index == k)

		return;

	else if(k < index)

		// search in lower sublist [first,index)

		findK(v, first, index, k);

	else

		// search in upper sublist [index+1,last)

		findK(v, index+1, last, k);

}



#endif   // SORTING_ALGORITHMS
```

---

### Post by Jonas thomas on 2011-04-22
> **jimi_hendrix said:**
> 
They would be combined in the header. Take the Boost Library for example. Most of what it provides involves templates and they are all implemented in the header files.

Can you suggest offhand in Boost that represents your point and is not to heavy??

---

### Post by dwhitney67 on 2011-04-22
It would seem that you have declared/implemented certain (if not all) functions from the author's d_sort.h in your main.cpp file as well.

As for the warnings, note that the size() method (for a vector, map, etc) returns a size_t type, not an int.  Thus when comparing an int against a size_t, expect to get a warning.  Using a cast is not appropriate; just fix the data type of the declared type that is causing the issue; for example:
```

...

void distribute(const vector<int>& v, queue<int> digitQueue[],

                int power)

{

        //int i;
        **size_t i;**

...
}

```


P.S.  Do NOT specify a "using namespace std" statement within a header file; it is considered bad programming practice.

---

### Post by Jonas thomas on 2011-04-22
> **dwhitney67 said:**
> It would seem that you have declared/implemented certain (if not all) functions from the author's d_sort.h in your main.cpp file as well.

As for the warnings, note that the size() method (for a vector, map, etc) returns a size_t type, not an int.  Thus when comparing an int against a size_t, expect to get a warning.  Using a cast is not appropriate; just fix the data type of the declared type that is causing the issue; for example:
```

...

void distribute(const vector<int>& v, queue<int> digitQueue[],

                int power)

{

        //int i;
        **size_t i;**

...
}

```


P.S.  Do NOT specify a "using namespace std" statement within a header file; it is considered bad programming practice.

Ahhhhhhh... brain overloading ... ready tooo explode....
So... It looks like there are several deficiencies in the authors code.
I'm pretty sure that I've set up my includes properly... Even though It goes against the assignment spec, I think I could make the argument for implementing my own selectSort sort rather than trying to fix stuff that isn't required for my project... This is the last thing that I need to fix in my project and I'm done....

---

### Post by jimi_hendrix on 2011-04-22
> **dwhitney67 said:**
> 
Using a cast is not appropriate; just fix the data type of the declared type that is causing the issue;


This is the correct way to solve this. When i recommended a cast, I incorrectly thought that an int was being compared to an unsigned int, not a size_t.

---

### Post by Jonas thomas on 2011-04-22
Thank you guys... soo much for being my sounding board...

Ultimately I just stripped out selection sort code and did this:

```
#ifndef MYOWNSELECTIONSORT_INCLUDED
#define MYOWNSELECTIONSORT_INCLUDED
// sort an array of type T using selection sort
//template <typename T>
//void selectionSort( T arr[], int n);



// IMPLEMENTATIONS

template <typename T>
void  myOwnselectionSort( T arr[], int n)
{
   int smallIndex; // index of smallest element in the sublist
   int pass, j;
	T temp;

   // pass has the range 0 to n-2
   for (pass = 0; pass < n-1; pass++)
   {
		// scan the sublist starting at index pass
		smallIndex = pass;

		// j traverses the sublist arr[pass+1] to arr[n-1]
		for (j = pass+1; j < n; j++)
         // update if smaller element found
			if (arr[j] < arr[smallIndex])
				smallIndex = j;

		// if smallIndex and pass are not the same location,
		// exchange the smallest item in the sublist with arr[pass]
		if (smallIndex != pass)
		{
			temp = arr[pass];
			arr[pass] = arr[smallIndex];
			arr[smallIndex] = temp;
		}
	}
}
#endif // MYOWNSELECTIONSORT_INCLUDED
```

I'm had some bizarre stuff going on in code::blocks because had by file named as "MyOwnSelectionSort.h" and the include as #include myOwnSectionSort.h  (I think). It didn't generate an error message an took me a while to figure out..

As far a type casting, I was helping a newb a few days back... Lets see if I can find it.
[http://ubuntuforums.org/showthread.php?t=1732069]("http://ubuntuforums.org/showthread.php?t=1732069")

Anyway.. the link I found had a interesting in regards of when to [when to type cast]("http://www.geekinterview.com/question_details/3350")..:
> Very very *VERY* rarely. My rule of thumb is if you see a cast expect a design error.

One classic example of this is the oh-so-popular casting of the return value of malloc. Don't do it. C doesn't need it and it can hide bugs; C++ has new which has benefits malloc lacks.

Yes there are cases for it but in 20+ years of coding I've encountered *very* few of them.



Would you guys go along with that statement..

---

