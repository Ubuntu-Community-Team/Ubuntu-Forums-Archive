---
title: "The Ubuntu Sorting Challenge"
date: 2007-10-27
forum: Programming Talk
---

### Post by samjh on 2007-10-27
Due to lack of mental stimulation in our Programming Forums, I propose: The Ubuntu Sorting Challenge

Your mission - if you choose to accept it - is to **create a program or script that populates an array or list with 10,000 pseudo-random integers between 0 to 100, and then sort it in ascending order using the best sorting algorithm of your cunning.**

Criteria:
[list][*]Execution time.
[*]Memory efficiency,
[*]Readable code.
[*]Innovative algorithms.[/list]

You may use any programming language, but all must be compilable and runnable in Ubuntu using standard libraries for that language.

Good luck.

CLARIFICATION:
Prohibited are built-in sorting algorithms.  You have to code the sorting algorithm yourself.
Everything else is fair game, as long as you stick to the standard libraries.


Here's a selection sort example written in Ada:
```
with Ada.Numerics.Discrete_Random;

procedure selsort is

	subtype Num is Integer range 0..100;

	List : array (1..10000) of Num;
	Temp : Num;

	package Random_Num is new Ada.Numerics.Discrete_Random(Num);
	use Random_Num;

	G : Generator;

begin

	Reset(G);

	for I in List'Range loop
		List(I) := Random(G);
	end loop;

	for I in List'Range loop
		for J in I..List'Last loop
			if List(J) < List(I) then
				Temp := List(I);
				List(I) := List(J);
				List(J) := Temp;
			end if;
		end loop;
	end loop;

end selsort;
```

I didn't try too hard, did I? ;)

---

### Post by LaRoza on 2007-10-27
> **samjh said:**
> 
I didn't try too hard, did I? ;)

Bubblesort is rather simple. All that will happen is the same code in different languages. Maybe if it were a "An efficient Sort challange", where any algorithm could be used, and speed or efficiency was the criteria.

---

### Post by samjh on 2007-10-27
Suggestion accepted, post revised.  Title change requested from mods. :)

---

### Post by LaRoza on 2007-10-27
> **samjh said:**
> Suggestion accepted, post revised.

Too tired to work on a solution, sorry. I'll look into it later.

Does using build in features of a langauge count? Like Python lists? or built in functions? How about standard library?

---

### Post by samjh on 2007-10-27
Prohibited are built-in sorting algorithms.  You have to code the sorting algorithm yourself.

Everything else is fair game, as long as you stick to the standard libraries.

---

### Post by dumbsnake on 2007-10-27
here is my hurried code... certainly there is room for optimization, but it is pretty fast and efficient I'd say:

```
int main(void)
{
    const int size = 10000;
    const int max_value = 100; // actually one more than max value
    int list[size];
    
    srand(time(NULL));

    for(int i = 0; i < size; i++){
        list[i] = rand() % max_value;
    }
    
    int histogram[100] = {
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0,
      0,0,0,0,0,0,0,0,0,0
    }
    
    for(int i = 0; i < max_value; i++){
      histogram[list[i]]++;
    }
    
    int *list_ptr = &list;
    for(int i = 0; i < max_value; i++){
      int rep = histogram[i];
      for(int j = 0; j < rep; j++){
        list_ptr++ = i;
      }
    }
}

```

---

### Post by jpkotta on 2007-10-27
nevermind.

---

### Post by slavik on 2007-10-27
Your wording seems to suggest any sort is fine for this competition. I give you the heap sort (this is almost my college nickname :))

Fastest heap sort implementation I have ever done (about an hour).

the only way to speed this up:
[list]
[*]change some addl/subl instructions to incl/decl
[*]inline the functions in the source code (the compiler is an ******** and doesn't listen to me :-P)
[*]use smooth sort instead (which is a more complex algorithm)
[*]use threads to maintain the heap (going to start working on it) but performance will be visible only on SMP systems (single CPU systems may suffer due to thread creation/deletion overhead)
[/list]

EDIT: re-read first post, changed the code from 1000 to 10000 numbers :)

[php]
/*
 *      sort.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define NUM 10000

//let's hope the compiler listens to us ...
inline void swap(char *heap, int count) {
	char tmp = heap[0];
	heap[0] = heap[count];
	heap[count] = tmp;
}

inline void heapify(char *heap, int count, int i) {
	int left = 2 * i + 1;
	int right = 2 * i + 2;

	//we have no kids, return
	if (right > count) return;

	//if we have a left child, heapify the subtree
	if (left <= count)	heapify(heap, count, left);

	//if we have a right child, heapify the subtree
	if (right <= count) heapify(heap, count, right);

	//we have two heapified subtrees, let's test the kids
	if (left == count) { //we have only 1 (left) child
		if (heap[left] > heap[i]) {
			char tmp = heap[left];
			heap[left] = heap[i];
			heap[i] = tmp;
		}
	}
	else {
		if (heap[left] > heap[right]) {
			if (heap[left] > heap[i]) {
				char tmp = heap[left];
				heap[left] = heap[i];
				heap[i] = tmp;
			}
		}
		else {
			if (heap[right] > heap[i]) {
				char tmp = heap[right];
				heap[right] = heap[i];
				heap[i] = tmp;
			}
		}
	}

}

int main(int argc, char** argv) {
	char heap[NUM]; // 1000 bytes ... should fit in most CPU's caches ;)
	int count = 0;

	//a true test would be to have the numbers inputed
	srand(time(NULL));
	for (count = 0; count < NUM; count++) {
		heap[count] = (char)abs((rand()*100/((RAND_MAX-1)/100.0)));
	}

	for (count = 0; count < NUM; count++) {
		printf("%d\t",heap[count]);
	}

	printf("\n=====================SORTING BEGINS=============================\n");

	count--;
	while(count > 1) {
		heapify(heap, count, 0);
		swap(heap, count);
		count--;
	}

	for (count = 0; count < NUM; count++) {
		printf("%d\t",heap[count]);
	}

	return 0;
}
[/php]

---

### Post by dumbsnake on 2007-10-27
oops, i had some typos and I guess I ought to have some comments too:

```

int main(void)
{
  // total memory used:
  // memory for the list
  // 400 bytes on stack
  // maybe locals? but probably they will
  // mostly be in registers and they wouldn't
  // be signifigant anyway
  // so, only 400 bytes that could theoretically be avoided
  // without optimizing the storage of the actual list
  // which I decided was cheating
 
  // store these as constants for easy changing
  const int size = 10000;
  const int max_value = 100; // actually one more than max value

  // this will hold our list
  int list[size];

  // make a random list
  srand(time(NULL));
  for(int i = 0; i < size; i++){
    list[i] = rand() % max_value;
  }

  // this stores the number of occurances
  // runs in constant time (allocated on the stack)
  // so it is very fast
  // must increment ESP by 400 and zero out 400 bytes
  int histogram[100] = {
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0
  };

  // count occurances of each number
  // O(n) where n is the number of items
  // one read, one write
  for(int i = 0; i < size; i++){
    histogram[list[i]]++;
  }

  // this tracks our position in the list we are writing back    
  int *list_ptr = list;

  // for each histogram entry...
  // the innermost portion will be executed n times
  // which makes this O(n) time
  // 100 reads, n writes
  for(int i = 0; i < max_value; i++){

    // get the number of occurances
    int rep = histogram[i];

    // write that number of occurances into the list
    for(int j = 0; j < rep; j++){
      *(list_ptr++) = i;
    }
  }
}

```

---

### Post by slavik on 2007-10-27
> **dumbsnake said:**
> oops, i had some typos and I guess I ought to have some comments too:

```

int main(void)
{
  // total memory used:
  // memory for the list
  // 400 bytes on stack
  // maybe locals? but probably they will
  // mostly be in registers and they wouldn't
  // be signifigant anyway
  // so, only 400 bytes that could theoretically be avoided
  // without optimizing the storage of the actual list
  // which I decided was cheating
 
  // store these as constants for easy changing
  const int size = 10000;
  const int max_value = 100; // actually one more than max value

  // this will hold our list
  int list[size];

  // make a random list
  srand(time(NULL));
  for(int i = 0; i < size; i++){
    list[i] = rand() % max_value;
  }

  // this stores the number of occurances
  // runs in constant time (allocated on the stack)
  // so it is very fast
  // must increment ESP by 400 and zero out 400 bytes
  int histogram[100] = {
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0,
    0,0,0,0,0,0,0,0,0,0
  };

  // count occurances of each number
  // O(n) where n is the number of items
  // one read, one write
  for(int i = 0; i < size; i++){
    histogram[list[i]]++;
  }

  // this tracks our position in the list we are writing back    
  int *list_ptr = list;

  // for each histogram entry...
  // the innermost portion will be executed n times
  // which makes this O(n) time
  // 100 reads, n writes
  for(int i = 0; i < max_value; i++){

    // get the number of occurances
    int rep = histogram[i];

    // write that number of occurances into the list
    for(int j = 0; j < rep; j++){
      *(list_ptr++) = i;
    }
  }
}

```
interesting (non-scalable) way of doing it :)

---

### Post by wolfbone on 2007-10-27
[QUOTE="samjh"]I didn't try too hard, did I?[/QUOTE]

Harder than me ;-)

```
(defun quicksort (numbers)
   (when numbers
     (let* ((x0 (car numbers))
	    (xi (cdr numbers))
	    (lt  (loop for y in xi when (< y x0) collect y))
	    (ge (loop for y in xi when (>= y x0) collect y)))
       (append (quicksort lt) (list x0) (quicksort ge)))))

(quicksort (let ((numbers)) (dotimes (i 10000 numbers) (push (random 101) numbers))))

```

---

### Post by almothana on 2007-10-27
:lolflag: :popcorn: i have lots of codes do u want them all

---

### Post by almothana on 2007-10-27
:( :confused: :guitar: :mad: :lolflag::popcorn: :KS :popcorn: (defun quicksort (numbers)
   (when numbers
     (let* ((x0 (car numbers))
	    (xi (cdr numbers))
	    (lt  (loop for y in xi when (< y x0) collect y))
	    (ge (loop for y in xi when (>= y x0) collect y)))
       (append (quicksort lt) (list x0) (quicksort ge)))))

(quicksort (let ((numbers)) (dotimes (i 10000 numbers) (push (random 101) numbers))))  thats won of them

---

### Post by public_void on 2007-10-27
A very simple Gnome sort.
```
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(int argc, char *argv[]) {
    size_t size = 1000;
    int numbers[size];
    int i;

    /*Generate 1000 random integers.*/
    srand(time(0));
    for (i = 0; i < size; ++i) {
        numbers[i] = rand();
    }
    
    /*Implementation of the Gnome sort. Very simple sort, yet highly inefficient.*/
    int j = 0;
    while (j < size) {
        if ((j == 0) || (numbers[j - 1] <= numbers[j])) {
            ++j;        
        }
        else {
            int temp = numbers[j];
            numbers[j] = numbers[j - 1];
            numbers[--j] = temp;
        }
    }

    /*Make sure the numbers are in order.*/
    for (i = 1; i < size; ++i) {
        assert(numbers[i - 1] <= numbers[i]);
        printf("%i\n", numbers[i]);
    }
    return 0;
}
```

---

### Post by Mathiasdm on 2007-10-27
Do I win? :lolflag:

Note: I didn't try to compile this code, so there might be a silly bug in it ;)

```

int main(void)
{
	int size = 10000;
	int list[size];
	int count, temp,j;
	int sorted = 0;
	int rand_one;
	int rand_two;
	
	srand(time(NULL));

	for (count = 0; count < size; count++) {
		list[count] = rand() % 100;
	}
	
	while(sorted != 1) {
		rand_one = rand()%10001;
		rand_two = rand()%10001;
		temp = list[rand_one];
		list[rand_one]=list[rand_two];
		list[rand_two]=temp;
		sorted = 1;
		for (j = 0; j < (size - 1); j++) {
			if (list[j] > list[j+1]) {
				sorted = 0;
				j = size;
			}
		}
	}

	return 0;
}
```

---

### Post by wolfbone on 2007-10-27
[QUOTE="Mathiasdm]Do I win?[/QUOTE]

Sure - someone'll send you a prize as soon as the program completes ;-)

BTW, I see many of the algorithms in the C code submitted so far swap pairs of integers. Would it be more efficient to do so arithmetically?: 

```
operation            n[j-1], n[j]
---------------------------------
                          x, y 
n[j-1]-=n[j]            x-y, y
n[j]+=n[j-1]            x-y, x
n[j-1]=n[j]-n[j-1]        y, x
```

---

### Post by tenmillionmilesaway on 2007-10-27
Hi,
I expected C to be popular here but here is my Java sorting algorithm.

Its a Quicksort algorithm:

```
public class Quicksort {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		Quicksort sort = new Quicksort();
		final int numItems = 10000;
		final int min = 0;
		final int max = 100;
		
		long time = System.currentTimeMillis();
		
		sort.populate(numItems, min, max);
		sort.quicksort(0, numItems-1);
		
		time = System.currentTimeMillis() - time;
		System.out.println("Time taken (ms) = " + time);
		
		System.out.println("It works: " + sort.test());
	}

	private int[] list;
	
	final private void populate(final int numOfElements, int min, int max)
	{
		max++;
		max -= min;
		list = new int[numOfElements];
		try
		{
			for(int index = 0;;index++)
			{
				list[index] = (int) (Math.random() * max) + min;
			}
		}
		catch(ArrayIndexOutOfBoundsException e)
		{
		}
	}
	
	final private void quicksort(final int left, final int right)
	{
		if (right > left)
		{
	        int pivotNewIndex = partition(left, right);
	        quicksort(left, pivotNewIndex - 1);
	        quicksort(pivotNewIndex+1, right);
		}
	}
	
	final private int partition(final int left, final int right)
	{
		int leftPointer = left + 1;
		int rightPointer = right;
		int pivotValue = list[left];
		while (leftPointer<=rightPointer) 
		{ 
			if (list[leftPointer] <= pivotValue) 
				leftPointer++; 
			else if (list[rightPointer] > pivotValue)
				rightPointer--; 
			else swap(leftPointer,rightPointer); 
		}  
		swap(left,rightPointer);
		return rightPointer;
	}
	
	private int temp = -1;
	final private void swap(final int indexFrom, final int indexTo)
	{
		temp = list[indexTo];
		list[indexTo] = list[indexFrom]; 
		list[indexFrom] = temp;
	}
	
	final private boolean test()
	{
		boolean works = true;
		for(int index = 0; index < list.length -1; index++)
		{
			if(list[index] > list[index+1])
				works = false;
		}
		return works;
	}
}

```

And I fully except that this will use more memory than a C program, but thats the JVMs fault not mine

Richard

---

### Post by tenmillionmilesaway on 2007-10-27
Ive got my threaded version of the quicksort working now.  Its slower than the single threaded version but I only have a single core machine.  You have to specify how many threads you want it to use, so this should be tailored to the number of processing cores you have.  It defaults to 2 but can be set as a command line argument. (eg java QuicksortThreaded 4)

```

public class QuicksortThreaded {

	public static void main(String[] args) {
		QuicksortThreaded sort = new QuicksortThreaded();
		final int numItems = 100000;
		final int min = 0;
		final int max = 100;
		int numThreads = 2;
		if(args.length == 1)
		{
			numThreads = Integer.parseInt(args[0]);
		}
		long time = System.currentTimeMillis();
		sort.populate(numItems, min, max);
		sort.quicksortThread(0, numItems-1, numThreads);
		time = System.currentTimeMillis() - time;
		System.out.println("Time taken (ms) = " + time);
		System.out.println("It works: " + sort.test());
	}

	private int[] list;
	final private void populate(final int numOfElements, int min, int max)
	{
		max++;
		max -= min;
		list = new int[numOfElements];
		try
		{
			for(int index = 0;;index++)
			{
				list[index] = (int) (Math.random() * max) + min;
			}
		}
		catch(ArrayIndexOutOfBoundsException e)
		{
		}
	}
	final private void quicksortThread(final int left, final int right, int numThreads)
	{
		if (right > left)
		{
	        final int pivotNewIndex = partition(left, right);
	        final int newNumThreads = numThreads - 2;
	        if(newNumThreads <= 0)
	        {
	        	Thread lessThanOrEqual = new Thread(new Runnable() {
	 	            public void run()
	 	            {
	 	            	quicksort(left, pivotNewIndex - 1);
	 	            }
	 	        });
	 	        Thread greaterEqual = new Thread(new Runnable() {
	 	            public void run()
	 	            {
	 	            	quicksort(pivotNewIndex+1, right);
	 	            }
	 	        });
	 	        lessThanOrEqual.start();
	 	        greaterEqual.start();
	 	        try {
	 				lessThanOrEqual.join();
	 				greaterEqual.join();
	 			} catch (InterruptedException e) {
	 				e.printStackTrace();
	 			}
	        }
	        else
	        {
	        	 Thread lessThanOrEqual = new Thread(new Runnable() {
	 	            public void run()
	 	            {
	 	            	quicksortThread(left, pivotNewIndex - 1, newNumThreads);
	 	            }
	 	        });
	 	        Thread greaterEqual = new Thread(new Runnable() {
	 	            public void run()
	 	            {
	 	            	quicksortThread(pivotNewIndex+1, right, newNumThreads);
	 	            }
	 	        });
	 	        lessThanOrEqual.start();
	 	        greaterEqual.start();
	 	        try {
	 				lessThanOrEqual.join();
	 				greaterEqual.join();
	 			} catch (InterruptedException e) {
	 				e.printStackTrace();
	 			}
	        }
		}
	}
	final private void quicksort(final int left, final int right)
	{
		if (right > left)
		{
	        int pivotNewIndex = partition(left, right);
	        quicksort(left, pivotNewIndex - 1);
	        quicksort(pivotNewIndex+1, right);
		}
	}
	final private int partition(final int left, final int right)
	{
		int leftPointer = left + 1;
		int rightPointer = right;
		int pivotValue = list[left];
		while (leftPointer<=rightPointer) 
		{ 
			if (list[leftPointer] <= pivotValue) 
				leftPointer++; 
			else if (list[rightPointer] > pivotValue)
				rightPointer--; 
			else swap(leftPointer,rightPointer); 
		}  
		swap(left,rightPointer);
		return rightPointer;
	}
	private int temp = -1;
	final private void swap(int indexFrom, int indexTo)
	{
		temp = list[indexTo];
		list[indexTo] = list[indexFrom]; 
		list[indexFrom] = temp;
	}
	final private boolean test()
	{
		boolean works = true;
		for(int index = 0; index < list.length -1; index++)
		{
			if(list[index] > list[index+1])
			{
				works = false;
					System.out.println(list[index] + " " + list[index+1]);
			}
		}
		return works;
	}
}

```

---

### Post by slavik on 2007-10-27
> **wolfbone said:**
> Sure - someone'll send you a prize as soon as the program completes ;-)

BTW, I see many of the algorithms in the C code submitted so far swap pairs of integers. Would it be more efficient to do so arithmetically?: 

```
operation            n[j-1], n[j]
---------------------------------
                          x, y 
n[j-1]-=n[j]            x-y, y
n[j]+=n[j-1]            x-y, x
n[j-1]=n[j]-n[j-1]        y, x
```
actually, not really, since the swap happens in cache it is very fast.

I remember a friend of mine compared the temp variable swap, with using xor to swap and with using the xchng x86 instruction to swap 2 variables. the temp variable was the fastest.

---

### Post by Wybiral on 2007-10-27
Mine is a modified simple-sort algorithm. Unlike the normal simple-sort, it swaps in place instead of making a buffer. If anyone knows the correct name for this (since it isn't really a simple-sort) let me know.

Essentially it works like this:
```

    for(i = 0; i < len(array) - 1; ++i)
        lowest = array[i]
        for(j = i + 1; j < len(array); ++j)
             if(array[j] < lowest) lowest = array[j]
        swap(lowest, array[i])

```

To make up for its obvious lack of efficiency (and to make it more entertaining), I wrote in in NASM 386 assembly.

```

;; sort.asm

;; void simple_sort(int *array, const int size);

global simple_sort
simple_sort:
    mov eax, [esp+4]
    mov ecx, [esp+8]
    xor edi, edi
    edi_loop_start:
        mov ebx, edi
        sal ebx, 2
        add ebx, eax
        mov esi, edi
        inc esi
        esi_loop_start:
            mov edx, [ebx]
            cmp [eax+esi*4], edx
            jge esi_loop_next
            mov ebx, esi
            sal ebx, 2
            add ebx, eax
        esi_loop_next:
            inc esi
            cmp esi, ecx
            jl esi_loop_start
        esi_loop_end:
        mov edx, [ebx]
        mov esi, [eax+edi*4]
        mov [ebx], esi
        mov [eax+edi*4], edx
    edi_loop_next:
        mov edx, ecx
        dec edx
        inc edi
        cmp edi, edx
        jl edi_loop_start
    edi_loop_end:
ret

```

```

/*
    sort.c

    nasm sort.asm -f elf -o sort.o && gcc sort.c sort.o -std=c99
*/

#include <stdio.h>

void simple_sort(int *array, const int size);

int main(int argc, char *argv[])
{
    int arr[15] = {10, 40, 3, 0, 8, 4, 20, 2, 1, 2, 5, 6, 7, 8, 5};

    simple_sort(arr, 15);

    for(int i = 0; i < 15; ++i)
        printf("%i ", arr[i]);
    putchar('\n');

    return 0;
}

```

It's certainly not the best, but I got a kick out of writing it, so it was fun. At this point I estimate that rplantz is shaking his head in disappointment due to my lack of prologue / epilogue :) but I was aiming for minimal code.

EDIT:

OK, my algorithm seems to be more like selection sort than simple sort.

---

### Post by samjh on 2007-10-28
...

---

### Post by Klipt on 2007-10-28
> **slavik said:**
> interesting (non-scalable) way of doing it :)
Pigeonhole sort is very scalable (linear time) in the length of the sequence, so long as all the numbers in the sequence come from a small set ;)

Mergesort in Haskell:

```
merge x [] = x
merge (x:xs) (y:ys)
	| x < y = x : merge (y:ys) xs
	| otherwise = y : merge (x:xs) ys
mergesort [x] = [x]
mergesort xs = merge (mergesort left) (mergesort right)
	where (left, right) = splitAt (div (length xs) 2) xs

```

I don't want to use random numbers since that would tarnish the pure functional aura, but this works:

```
Main> mergesort [-i | i <- [1..10000]]
[-10000,-9999,-9998,-9997,-9996,...
```

---

### Post by slavik on 2007-10-28
> **Klipt said:**
> Pigeonhole sort is very scalable (linear time) in the length of the sequence, so long as all the numbers in the sequence come from a small set ;)

Mergesort in Haskell:

```
merge x [] = x
merge (x:xs) (y:ys)
	| x < y = x : merge (y:ys) xs
	| otherwise = y : merge (x:xs) ys
mergesort [x] = [x]
mergesort xs = merge (mergesort left) (mergesort right)
	where (left, right) = splitAt (div (length xs) 2) xs

```

I don't want to use random numbers since that would tarnish the pure functional aura, but this works:

```
Main> mergesort [-i | i <- [1..10000]]
[-10000,-9999,-9998,-9997,-9996,...
```
"small set" is why it isn't scalable. scalable means that you can increase the number of items without a major impact.

---

### Post by MadMan2k on 2007-10-28
so far dumbsnakes' bucket-sort variation is the fastest...

---

### Post by geirha on 2007-10-28
This python implementation might sort the array in a finite ammount of time. It has used between 20-120 seconds to sort 10 elements from the tests I have done. It hasn't sorted 10 000 elements for me yet though ... At least it's readable code :)

```
import random

def is_sorted(A):
    prev= 0
    for a in A:
        if a < prev:
            return False
        prev= a
    return True

def sort(A):
    while not is_sorted(A):
        random.shuffle(A)

if __name__ == '__main__':
    A= [random.randint(0,100) for _ in range(10000)]
    sort(A)
    print A

```

---

### Post by aks44 on 2007-10-28
> **geirha said:**
> ```
    while not is_sorted(A):
        random.shuffle(A)
```


LMAO. I guess you deserve the "most original code" award so far... :p

---

### Post by Klipt on 2007-10-28
> **slavik said:**
> "small set" is why it isn't scalable. scalable means that you can increase the number of items without a major impact.
That depends whether by 'items' you mean the items you are sorting, or their possible values...

Radix sort is a bit more scalable - just change 20 to another power of 2.

```
def sortbyradix(n, xs):
	def getradix(x): return (x // 2**n) % 2
	return [i for i in xs if getradix(i) == 0] + [i for i in xs if getradix(i) == 1]

def radixsort(xs):
	for n in range(20+1):
		xs = sortbyradix(n, xs)
	return xs
```

or Haskell:
```
sortbyradix n xs = (filter ((0==).getradix) xs) ++ (filter ((1==).getradix) xs)
	where getradix x = mod (div x (2^n)) 2

radixsort xs = helper 0 xs
	where helper n xs
		| n > 20 = xs
		| otherwise = helper (n+1) (sortbyradix n xs)
```

---

### Post by dumbsnake on 2007-10-28
> **slavik said:**
> "small set" is why it isn't scalable. scalable means that you can increase the number of items without a major impact.


Well,
   to be completely fair... My code scales the best as the number of items increases.  So in that sense it scales wonderfully.  In terms of scaling over a range that is increased (changing 100 to say 10000), it isn't all that bad as long as the range is not much bigger than the size of the list.

---

### Post by CptPicard on 2007-10-28
Read a textbook. Sorting is a fundamental problem that is known inside and out, no need to code anything. :)

---

### Post by slavik on 2007-10-28
> **CptPicard said:**
> Read a textbook. Sorting is a fundamental problem that is known inside and out, no need to code anything. :)
it was still a good motivator to code a sorting routine (which I would have to do anyway).

---

### Post by samjh on 2007-10-28
> **CptPicard said:**
> Read a textbook. Sorting is a fundamental problem that is known inside and out, no need to code anything. :)

Sorting is also something a lot of comp sci students read about in a textbook, copy some code, and not think about why and how it works.

ie. Sorting, like arrays, linked lists, queues, and trees, are too often taken for granted.

---

### Post by CptPicard on 2007-10-28
> **samjh said:**
> Sorting is also something a lot of comp sci students read about in a textbook, copy some code, and not think about why and how it works.

And flunk the exam (at least if it is properly constructed). Sorting algorithms are a really great example of something you learn by understanding, not memorizing the particular implementation of index counting ;)

Yeah, I was an undergrad once, I remember trying to learn quicksort by memorizing code (yes, laugh), but fortunately understood in time the best way to the exam was to code the implementation there ad hoc and just go there equipped with the idea...

EDIT: And you've got a BAD textbook if it approaches those for granted things from a "here's some code, copy it" perspective... ideas are textbook material, implementation is homework assignment!

---

### Post by samjh on 2007-10-28
> **CptPicard said:**
> And flunk the exam (at least if it is properly constructed). Sorting algorithms are a really great example of something you learn by understanding, not memorizing the particular implementation of index counting ;)

...

EDIT: And you've got a BAD textbook if it approaches those for granted things from a "here's some code, copy it" perspective... ideas are textbook material, implementation is homework assignment!

Funny you say that.

I had a fantastic lecturer in my introductory programming class, but we spent maybe 30 minutes in a lab session for sorting.  We had to code a bubblesort implementation from given pseudo-code, and I felt at the end that it was a bit inadequate.

It wasn't until I took an algorithms and data structures course a year later that we went into the actual design and performance analysis of sorting algorithms.  But even then, our text had source codes all on a silver platter (Preiss, *Data Structures and Algorithms*, 2000).

---

### Post by Lux Perpetua on 2007-10-29
Okay, I'll bite. More correctly, I have bitten. Simple driver program: ```
#include <cstdlib>
#include <ctime>

#define N 10000000

extern "C" void bucket_sort(int *p, int n);

using namespace std;

int main(void)
{

    int *a = new int[N];

    srand(time(NULL));

    for (int k = 0; k < N; ++k)
    {
        a[k] = rand()%101;
    }
    
    bucket_sort(a, N);

    return 0;
}

```And some gooey GASsy goodness: ```
        .global bucket_sort
        .data
        .align 4
buckets:
        .skip 404
        
        .text
bucket_sort:
        movl    $100,   %ecx
zero_loop:
        movl    $0,     buckets( , %ecx, 4)
        decl    %ecx
        jge     zero_loop
        
        movl    4(%esp), %edx
        movl    8(%esp), %ecx

count_loop:     
        movl    -4(%edx, %ecx, 4), %eax
        incl    buckets( , %eax, 4)
        decl    %ecx
        jg      count_loop

        pushl   %ebx
        
fix_loop:
        movl    buckets( , %ecx, 4), %eax
        testl   %eax,   %eax
        jz      fix_loop_end
        leal    (%edx, %eax, 4), %ebx
        
repeat_loop:    
        decl    %eax
        movl    %ecx,   (%edx, %eax, 4)
        jnz     repeat_loop

        movl    %ebx,   %edx
        
fix_loop_end:   
        incl    %ecx
        cmpl    $100,   %ecx
        jle     fix_loop

        popl    %ebx
        
        ret

```Some highlights: it's unscalable (in the sense of expanding the range of elements, not of enlarging the array), non-reentrant, and unreadable. It seems to be about neck-in-neck with dumbsnake's code for large array sizes (10,000,000 elements). (We're using the same algorithm.)

---

### Post by dumbsnake on 2007-10-29
> **Lux Perpetua said:**
> 
```

zero_loop:
        movl    $0,     buckets( , %ecx, 4)
        decl    %ecx
        jge     zero_loop
        

```

So, I'll admit my assembly is a bit rusty and I learned intel style not AT&T, but... I'll ask my question anyway.  I would have written that zero loop as:

```

        xor    %eax, %eax

zero_loop:
        movl    %edi,     buckets
        rep stosdw  %eax

```
Is there a reason you wrote it the way you did?  Sorry if my AT&T syntax is wrong.

Also, I would venture to say that my C/C++ code compiles to something faster because there are a few optimizations that I'd guess gcc would use for those loops.  The most obvious one being unrolling them atleast once.

What are your thoughts?

---

### Post by evymetal on 2007-10-29
> **geirha said:**
> 
```

def sort(A):
    while not is_sorted(A):
        random.shuffle(A)

```

Love it, reminds me of an O(n) sorting algorithm a friend told me about for Quantum computers:

```

if is_in_correct_order(A):
    return A
else:
    universe.destroy()

```


But anyway, here's my version (python- can't be bothered to struggle through ASM). Can never remember sorting algorithms so don't know if it's got a name (just wrote it). It cheats slightly by knowing that the values are uniformly distributed.

```
"""Sort a list of 10,000  random ints in the range [0,100]"""
import random
import copy

def mysort(C):
	A = copy.deepcopy(C)
	B = []
	# First part (relies on them being uniformly distributed)
	while len(A) > 0:
		a = A.pop()
		E_posn = int(a/100. * len(B))
		B.insert(E_posn,a)

	# Now Bubblesort
	A,its = bidirectionalsort(B)
	return A,its


def bidirectionalsort(C):
	A = copy.deepcopy(C)
	done = False
	j = 0
	while not done:
		done = True
		j+=1
		for i in xrange(len(C)-1,0,-1):
			if A[i] < A[i-1]:
				done = False
				tmp = A[i]
				A[i] = A[i-1]
				A[i-1] = tmp
		if not done:
			for i in xrange(1,len(C)):
				if A[i] < A[i-1]:
					done = False
					tmp = A[i]
					A[i] = A[i-1]
					A[i-1] = tmp
	return A,j

if __name__ == "__main__":
	A = [random.randint(0,100) for i in xrange(10000)]
	(B,its) = mysort(A)
	print its


```

Clearly the first part is O(n), the second part (bidirectional bubblesort) would be O(n^2) except for the law of large numbers, which reduces the need for sorting as n increases.

Seems to sort 10,000 in approximately 40 itterations of the bubblesort, and 100,000 in approximately 110 (each of which is O(n))

---

### Post by Wybiral on 2007-10-29
> **Wybiral said:**
>  ... 

After a quick refresh on sorting algorithms, I realize mine is a selection sort.

---

### Post by Lux Perpetua on 2007-10-29
> **dumbsnake said:**
> So, I'll admit my assembly is a bit rusty and I learned intel style not AT&T, but... I'll ask my question anyway.  I would have written that zero loop as:

```

        xor    %eax, %eax

zero_loop:
        movl    %edi,     buckets
        rep stosdw  %eax

```
Is there a reason you wrote it the way you did?  Sorry if my AT&T syntax is wrong.

Also, I would venture to say that my C/C++ code compiles to something faster because there are a few optimizations that I'd guess gcc would use for those loops.  The most obvious one being unrolling them atleast once.

What are your thoughts?I wrote it the way I did simply because that's what I thought of at the time. I'm pretty green when it comes to assembly language, and I'm still not very good at optimizing it, so your way may well be faster.

---

### Post by Humph on 2007-10-30
I came across the "Shell Sort" algorithm used below in a book entitled "Pure Visual Basic" by Dan Fox. It is a variation of the "Insertion Sort". As VB don't run on Linux I was forced to read some tutorials so I could rewrite it in C. Sorting 1000000 elements takes around 0.6 seconds.

This is my first ever C[++] program, so I apologise in advance for any gaffes!

```
#include <cstdlib>
#include <ctime>
using namespace std;
int main()
{
    const long size = 999999;
    long x[size];        
    long lb = 0, ub = size;    
    long s, p, i, t;    
    bool d;            

    d = false;
    
    srand(time(0));
    for( i = lb; i <= ub; i++ ) 
    {
        x[i] = rand() % (size + 2);
    }

    s = (ub - 1) * 3;
    do
    {
        s = s / 3;
        for( i = s; i <= ub; i++ ) {
            t = x[i];
            p = i;
            if(s == 0)
            {
                s = 1;
                d = true;
            }
            while ( x[p - s] > t )
            {
                x[p] = x[p - s];
                p = p - s;
                if( p <= s)
                {
                    break;
                }
            } 
            x[p] = t;
        }
    } while ( s != (lb + 1) || d );
}
```

---

### Post by dataw0lf on 2007-10-30
Since quicksort has been covered, I thought I'd offer up something else.  Here's a decorator in Python to time your results (if, obviously, you're using Python):

```

import time
# decorator for timing
def time_it(func):
  def _inner(*arg):
    c1 = time.clock()
    do = func(*arg)
    c2 = time.clock()
    print "Time: %0.3fms" % ((c2-c1) * 1000)
    return do
  return _inner

```

I think the adaptive merge sort built into Python is about as fast as you can go (.sort()), although quicksort might be able to shave off a couple ms for large lists.

---

### Post by Lux Perpetua on 2007-10-31
Very interesting. I hadn't heard of adaptive merge sort before. [Here](http://python.cvs.sourceforge.net/*checkout*/python/python/dist/src/Objects/listsort.txt) is a good explanation.

---

### Post by evymetal on 2007-10-31
> **dataw0lf said:**
> 

```

import time
# decorator for timing
def time_it(func):
  def _inner(*arg):
    c1 = time.clock()
    do = func(*arg)
    c2 = time.clock()
    print "Time: %0.3fms" % ((c2-c1) * 1000)
    return do
  return _inner

```
.

I find that the function lookup time takes too long (and has too much variation if the timing function is in global scope. I'd reference it locally:

```

import time
# decorator for timing
def time_it(func):
  def _inner(*arg):
    clock = time.clock
    c1 = clock()
    do = func(*arg)
    c2 = clock()
    print "Time: %0.3fms" % ((c2-c1) * 1000)
    return do
  return _inner

```

Although I hadn't thought of using decorators for benchmarking, good Idea (Might help me profile some of my threaded code).

---

### Post by NathanB on 2007-10-31
Here is a discussion (with graphs) of the performance of the standard sorting algos:

[http://linux.wku.edu/~lamonml/algor/sort/sort.html](http://linux.wku.edu/~lamonml/algor/sort/sort.html)

For very large amounts of data, I believe that Binary Trees are preferred.  Take a look at **'Red Black Trees'** under *'Tutorials > Data Structures'* here:

[http://www.eternallyconfuzzled.com/jsw_home.aspx](http://www.eternallyconfuzzled.com/jsw_home.aspx)

{also take note of the *'Articles > Using rand()'* and the *'Tutorials > Algorithms > Random Numbers'* discussions}

Nathan.

---

### Post by NathanB on 2007-11-03
Oh heck, let's do the task at "quantum speed" with High Level Assembly:

```

// cross-platform:  Linux & Windows now; others in the works...
// get HLA here:  http://www.artofasm.com

program quantum;
#include( "stdlib.hhf" )

const
    
    ITERATIONS		:uns32	:=	10000;
    MAX_VALUE		:uns32	:=	100;
    
static
    
    items	:uns32[ITERATIONS];
    freq		:uns32[MAX_VALUE+1];
    mixed	:file;
    sorted	:file;
    
begin quantum;
    
    /* initialization
    */
    rand.randomize();
    mixed.create();  // these are file objects
    mixed.openNew( "sfalse.txt" );
    sorted.create();
    sorted.openNew( "strue.txt" );
    
    /* create the unsorted array
    */
    mov( 0, ecx );
    repeat
        
        rand.range( 0, MAX_VALUE );  // returns value in 'eax'
        mov( eax, items[ecx*4] );  // puts value into array
        mixed.put( (type uns32 ecx):5, ": ", (type uns32 eax), nl );
        // mirror to file
        add( 1, ecx );
        
    until ( ecx = ITERATIONS );

    /* record the frequencies of the numbers
    */    
    for( mov( 0, ecx ); ecx < ITERATIONS; inc( ecx ) ) do
        
        mov( items[ecx*4], eax );  // get value from array
        inc( freq[eax*4] );  // increment its frequency count
        
    endfor;

    /* use frequency table to re-order the array
    */
    xor( ecx, ecx );  // could also use 'mov( 0, ecx )'
    xor( ebx, ebx );
    while( ebx < MAX_VALUE+1 ) do
        
        mov( freq[ebx*4], eax );  // get frequency count
        if ( eax != 0 ) then
            
            // keep storing that number until eax = 0
            repeat
            
                mov( ebx, items[ecx*4] );
                sorted.put( (type uns32 ecx):5, ": ", (type uns32 ebx), nl );
                // mirror to file
                inc( ecx );  // could also use 'add( 1, ecx )'
                dec( eax );  // sets Zero Flag if eax = 0
                
            until ( @z );  // check if Zero Flag is set
        
        endif;
        
        add( 1, ebx );
        
    endwhile;
    
    mixed.close();
    sorted.close();
    
end quantum;

```

---

