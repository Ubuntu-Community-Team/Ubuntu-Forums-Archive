---
title: "Help with Quicksort needed"
date: 2010-09-10
forum: Programming Talk
---

### Post by maciejso on 2010-09-10
It's a nasty way to implement quicksort, but why not try it.
I know QS is only two lines of code in Haskell, but this is real life.
have been struggling with it for quite a while now and
got stuck with sorting arrays of size 2.
Can anybody help? 

Here's my partition:```

import java.lang.Math;
import java.util.Random;

public class quicksort{
	/*
	public static int partition2(int A[], int left, int right){
		int pivot = A[right];
		int i = left-1;
		for (int j = left;j<=(right-1);j++){
			System.out.printf("j: %d, i: %d\n", j, i);
			if (A[j] <= pivot){
				i++;
				swap(A,i,j);		
			}
		}
		swap(A,i+1,right);
		return i+1;
	}
       */
	public static int partition(int A[], int left, int right){
		int pivot = A[right];
		System.out.printf("pivot: %d\n", pivot);
		int p = left;
		int q = right-1;

		while (true) {
			System.out.printf("p: %d, q: %d,\n", p, q);
			while (A[p] < pivot)
			p++;
			while (A[q] > pivot) 
			q--;
			///System.out.printf("p: %d, q: %d, A[p]: %d,  A[q]: %d,\n", p, q, A[p], A[q]);

			if (p<q){
				swap(A,p,q);
			}
			else {
				System.out.println("---!---last swap---!---");
				swap(A,right,p);
				System.out.printf("split@ : %d\n", p );	
				printArray(A,0,A.length-1);
				return p;
			}
				
		}
		
	}
	public static void quickSort(int A[], int left, int right) {
		System.out.println("Quicksort called");
		printArray(A,left,right);
		if (left < right){
			int split = partition(A, left, right);
			System.out.printf("subarray 1: ");
			printArray(A,left,split-1);
			quickSort(A, left, split-1);
			System.out.printf("subarray 2: ");
			printArray(A,split+1,right);
			quickSort(A, Math.min(split+1,right), right);
		}
	}

	public static void swap(int[] A, int i, int j){
		if (A[i] != A[j]){
			A[i] ^= A[j];
			A[j] ^= A[i];
			A[i] ^= A[j];
		}
		System.out.printf("swap made: %d <------> %d\n", A[j], A[i]);
		printArray(A,0,A.length-1);
	}
	
	public static void printArray(int[] A,int m,int s){
		String str = "";
		for (int i = m; i<=s; i++){
			str += A[i];
			str += ", ";	
		}	
		System.out.println(str);
	}

	public static void main(String[] args) throws InterruptedException{
		int size = 3;
		int[] A = new int[size];
		int[] B = {10,0,1,9,2,8,3,7,4,6,5};

		Random r = new Random();
		for (int i=0; i<size; i++){
			A[i] = r.nextInt(size);	
		}
		
		printArray(B,0,B.length-1);
		quickSort(B,0,B.length-1);
		System.out.println("sorting done");
		Thread.sleep(1000);
		printArray(B,0,B.length-1);
	}
}



```

---

### Post by dv3500ea on 2010-09-10
> **maciejso said:**
> I know QS is only two lines of code in Haskell, but this is real life.

Why not just use Haskell in real life? Also, for 'real life' you don't need to implement your own quick sort because most languages come with an inbuilt way of sorting that does things more efficiently than you will be able to do.

To sort an array of size 2:
ascending:
```

if arr[0] > arr[1]
    [arr[1], arr[0]]
else
    [arr[0], arr[1]]

```
descending:
```

if arr[0] < arr[1]
    [arr[1], arr[0]]
else
    [arr[0], arr[1]]

```

---

