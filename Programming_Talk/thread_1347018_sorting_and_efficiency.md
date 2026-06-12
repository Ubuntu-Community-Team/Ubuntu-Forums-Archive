---
title: "sorting and efficiency"
date: 2009-12-05
forum: Programming Talk
---

### Post by swappo1 on 2009-12-05
I have several sorting functions and I am trying to determine which one is more efficient.  I am looking at how many times a comparison and an assignment is made.  What is more labor intensive for the computer, assignment or comparison?  Should I look only at how many times the assignment operator is used?  Here is an example of the bubble sort function I am using.
```
public class bubbleSort
{
	public void bubbleSortArray(int array[])
	{
		int temp;
		int compare = 0;
		int assign = 0;
	
		for(int i = 0; i < array.length - 1; i++)
		{
			compare++;
			for(int j = 1 + i; j < array.length; j++)
			{
				compare++;
				if(array[i] > array[j])
				{
					compare++;
					assign += 3;
					temp = array[i];
					array[i] = array[j];
					array[j] = temp;
				}
			}
		}
		System.out.println("Comparisons = " + compare);
		System.out.println("Assignments = " + assign);
	}
}
```

---

### Post by A_Fiachra on 2009-12-05
Look at the total number of times you loop (at whatever level).

You'll notice that number increases polynomially with the size of the array for bubblesort.

With quicksort, heap sort and radix sorting that number will increase less quickly as the array grows.

Of yourse, you could just look all this up in any CS book.  :-)

---

### Post by MadCow108 on 2009-12-05
regarding sorting the algorithm is far more important than the the low level optimization.

the best possible bubble sort implementation will always be slower than the stupidest possible (but correct) implementation of quicksort on some problem scale.

If you want to optimize your sorts benchmark your input data and choose the appropriate algorithm (quicksort is O(n^2) in certain cases, there are algorithms which have O(nlogn) in all cases) or preprocess your data so the worst case does happen less often.

Quicksort with an insertion sort for small data sizes is usually the best choice for real world data. (this is also the default sort in most languages)

regarding your assignment/comparison question:
I'm no expert on this, but an assignment to an array consists of an arithmetic operation to calculate the memory position (ar[i] = *(ar+i), a memory read and a memory write whereas comparisons just need to read and compare.
So assignment should be slower than comparison by a constant factor. (but this may _very_ dependent on compiler optimizations and architecture)

---

### Post by Can+~ on 2009-12-05
> regarding your assignment/comparison question:
I'm no expert on this, but an assignment to an array consists of an arithmetic operation to calculate the memory position (ar[i] = *(ar+i), a memory read and a memory write whereas comparisons just need to read and compare.
So assignment should be slower than comparison by a constant factor. (but this may _very_ dependent on compiler optimizations and architecture)

This is the only important thing to recognize regarding "what costs more". How many time is the data transversed for a n-size input (m-size, n-size, a-size... if there's multiple inputs).

There's no way to tell if a certain instruction takes longer than other, it supposedly occurs in a certain amount of rising/lowering edge of clock cycles that switch the state of all the cpu components.

In other words, is something so minuscule, and so hardware dependent, there's no surefire way to tell it, and it doesn't matter either.

Optimization should come first from the algorithm, later from the machine. As mentioned above, there's already known algorithms, way better than Bubblesort (in fact, bubblesort is the typical counter-example of efficient algorithms).

Quicksort provides the "quickest" sorting (duh), except when the input is inverted, then it takes $O(n^2)$ (I wish the forum could parse LaTeX).

Heapsort provides a constant $O(nlog_2n)$, but costs more memory. Insertion/Selection Sort, though they usually cost a little more (can get to O(n^2)) is best used when the input is partially sorted.

Oh, and remember:

[CENTER]*"Premature optimization is the root of all evil"*[/CENTER]

---

### Post by Arndt on 2009-12-06
> **Can+~ said:**
> This is the only important thing to recognize regarding "what costs more". How many time is the data transversed for a n-size input (m-size, n-size, a-size... if there's multiple inputs).

There's no way to tell if a certain instruction takes longer than other, it supposedly occurs in a certain amount of rising/lowering edge of clock cycles that switch the state of all the cpu components.

In other words, is something so minuscule, and so hardware dependent, there's no surefire way to tell it, and it doesn't matter either.

Optimization should come first from the algorithm, later from the machine. As mentioned above, there's already known algorithms, way better than Bubblesort (in fact, bubblesort is the typical counter-example of efficient algorithms).

Quicksort provides the "quickest" sorting (duh), except when the input is inverted, then it takes $O(n^2)$ (I wish the forum could parse LaTeX).

Heapsort provides a constant $O(nlog_2n)$, but costs more memory. Insertion/Selection Sort, though they usually cost a little more (can get to O(n^2)) is best used when the input is partially sorted.

Oh, and remember:

[CENTER]*"Premature optimization is the root of all evil"*[/CENTER]

Almost be sure to have a very good reason if you choose to use a non-stable sorting algorithm in favour of a stable one.

---

### Post by CptPicard on 2009-12-06
In formal analyses, what is usually counted is the number of key comparisons, not assignments.

> **Can+~ said:**
> Heapsort provides a constant $O(nlog_2n)$, but costs more memory.

You can do [heapsort in-place]("http://en.wikibooks.org/wiki/Algorithm_Implementation/Sorting/Heapsort#In-place_heapsort").

---

