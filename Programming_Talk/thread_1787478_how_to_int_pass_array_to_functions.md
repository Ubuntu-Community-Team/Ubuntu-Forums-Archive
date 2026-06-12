---
title: "how to int pass array to functions"
date: 2011-06-21
forum: Programming Talk
---

### Post by jamesbon on 2011-06-21
Here is my program it is compiling and running without syntax errors.How ever it does not sort the array.The problem lies in where I am passing the array in function
```

    #include<stdio.h>
    #include<string.h>
    int partition (int *,int,int);
    void quicksort (int *,int,int);
    static int call=0;
    int main()
    {
    int i,j,choice;
    int length;
    int a[]={81, 12, 90, 3, 49, 108, 47};
    i=0;

    length=sizeof(a)/sizeof(a[0]);
    quicksort(a,0,length-1);
    printf("the sorted array is\n");
    for(i=0;i<length;i++)
     printf (" %d ",a[i]);
    }
    int partition(int *num,int p,int r)
    {
     int x,j,i,temp,bak;
      x=num[r];
      i=-1;
           for(j=0;j<=r-1;j++)
      { 
             if(num[j]<=x)
         {
          i=i+1;
           temp=num[i];
           num[i]=num[j];
           num[j]=temp;
     
     
          {
           printf(" %d",num[bak]);
            }
      
         }	
      }
      num[i+1]=num[r];
   
     return i+1;
    }
    
    void quicksort (int *num,int p,int r)
    { 
     int q;
     if (p<r)
      {
    	call++;
   
    	q=partition(num,p,r);
            quicksort(num,p,q-1);
            quicksort(num,q+1,r);
      }
    }    

```

The above way of passing array in functions is that right that is what I want to know because that is giving problem in function partition.

Inside the function partition when swapping happens then I tried printing the array there itself (it is not sorted array but just to see upto what point things reached) then I saw that only 2 or 3 elements of array which I had passed are being printed and rest of the array is lost some where.So my doubt is array is not being passed properly.



To be able to see as what is the problem with array passing in a function I wrote a smaller program ka1.c

```

    #include<stdio.h>
    void pass(int *);
    int main ()
    {
    int a[]={3,5,61,32,12};
    pass(a);
    }
    void pass (int *num)
    {
    int i,j;
     j=sizeof(num)/sizeof(num[0]);
     for (i=0;i<j;i++)
     printf(" %d",num[i]);
    }
```

Now when I run the above code I get output just

```
     3 5
```
I was expecting the complete array to be printed in output.
Where as if you notice **rest of the array of second program ka1.c is not getting printed**.Where did that go?
 I have used the same logic in quicksort also hence I feel the error is same in both cases.

I use gcc-4.4.3 on a 64 bit machine.

I also checked the length of array which is being passed in quicksort.c parititon function
```
    int a[]={81, 12, 90, 3, 49, 108, 47};
```
when this array of 7 length is passed into partition function,it receives the array of the length is just 2.
I checked in partition function as
```
length=sizeof(num)/sizeof(num[0]);
```
**the length it returned was just 2 instead of 7.**
The same is case with ka1.c program.Where program was unable to find out the length the of array being passed.
So why is that a problem and what exactly is the fault with such a way of passing array's?

---

### Post by simeon87 on 2011-06-21
You have to pass in the length of the array as well to the function. You can't compute it from the pointer to the first element of the array. The information just isn't there to compute it.

So the value of j in the function pass will be wrong; just pass another int to the function which is the length of the array and it'll be fine.

---

### Post by dwhitney67 on 2011-06-21
An example perhaps would help:
```

#include <stddef.h>
#include <stdio.h>

void function(int* values, const size_t numValues)
{
   for (size_t n = 0; n < numValues; ++n)
   {
      printf("values[%ld] = %d\n", n, values[n]);
   }
}

int main()
{
   int    array[]   = { 10, 20, 30, 40, 50, 60, 70 };
   size_t arraySize = sizeof(array) / sizeof(array[0]);

   printf("arraySize = %ld\n", arraySize);

   function(array, arraySize);

   return 0;
}

```

---

### Post by jamesbon on 2011-06-21
That is a bit surprising because in main() we can  calculate the length like that why not when we pass on same address to a function?

---

### Post by dwhitney67 on 2011-06-21
> **jamesbon said:**
> That is a bit surprising because in main() we can  calculate the length like that why not when we pass on same address to a function?

What's surprising?  When you pass a pointer to a function, it either has a size of 4 bytes (32-bit system) or 8-bytes (64-bit system).

Do the math, where under Linux, an int has a size of 4 bytes...

ptrSize / intSize = 1 or 2, depending on 32- or 64-bit architecture.


Btw, a working quicksort()...
```

#include <stddef.h>
#include <stdio.h>

const int SMALL_ENOUGH = 15;

void selectionSort(int* values, const int left, const int right)
{
   for (int i = left; i < right - 1; ++i)
   {
      int min = i;

      for (int j = i + 1; j < right; ++j)
      {
         if (values[j] < values[min])
            min = j;
      }

      int temp = values[min];
      values[min] = values[i];
      values[i] = temp;
   }
}

int partition(int* values, const int left, const int right)
{
   int val = values[left];
   int lm  = left - 1;
   int rm  = right;

   for (;;)
   {
      do { rm--; } while (values[rm] > val);
      do { lm++; } while (values[lm] < val);

      if (lm < rm)
      {
         int temp = values[rm];
         values[rm] = values[lm];
         values[lm] = temp;
      }
      else
      {
         break;
      }
   }

   return rm;
}


void quicksort(int* values, const int left, const int right)
{
   if (left < (right - SMALL_ENOUGH))
   {
      const int split = partition(values, left, right);
      quicksort(values, left, split);
      quicksort(values, split + 1, right);
   }
   else
   {
      selectionSort(values, left, right);
   }
}

void printArray(int* values, const int numValues)
{
   for (int n = 0; n < numValues; ++n)
   {
      printf("%d ", values[n]);
   }
   printf("\n");
}

int main()
{
   int array[]   = { 40, 10, 50, 30, 70, 60, 20, 90, 80, 140, 110, 5, 130, 120, 170, 150, 160 };
   int arraySize = sizeof(array) / sizeof(array[0]);

   printf("Unsorted: "); printArray(array, arraySize);

   quicksort(array, 0, arraySize);

   printf("Sorted  : "); printArray(array, arraySize);

   return 0;
}

```

---

### Post by Arndt on 2011-06-21
> **jamesbon said:**
> That is a bit surprising because in main() we can  calculate the length like that why not when we pass on same address to a function?

In main, sizeof sees the actual array, and knows its size, but what you send to the function is a pointer to the first element of the array, and it carries no information beyond that.

Besides, mergesort is better than quicksort.

---

### Post by NovaAesa on 2011-06-21
> **Arndt said:**
> Besides, mergesort is better than quicksort.Only in some situations :p

---

### Post by jamesbon on 2011-06-21
Ok I read all the replies including dwhitney67's code.

While trying to debug my program 
I found 2-3 errors which I had in previous program.
After improving them I wrote new program.But while debugging in gdb my problem came the recursive function calls.What is happening is I set break points at 
line no 
17,59,24,60,63,64
now when I am running in gdb when code reaches line 60 a call is again made to line no 56 and execution there on calls line 23 so my break points are not working i.e. I am unable to see the flow of my program once a break point has been crossed and if some function recursively calls the same code which was at a previous break point then this time on execution I directly see the result of function execution.
Is there a way to be out of this recursive function calls in gdb and be able to debug in this situation properly.

This is the new code if some one wants to see.
```


 1 #include<stdio.h>
  2 #include<string.h>
  3 int partition (int *, int, int, int);
  4 void quicksort (int *, int, int, int);
  5 static int call = 0;
  6 int
  7 main ()
  8 {
  9   int i, j, choice;
 10   int length;
 11   int a[] = { 81, 12, 90, 3, 49, 108, 47 };
 12   i = 0;
 13   printf ("the sorted array is\n");
 14   length = sizeof (a) / sizeof (a[0]);
 15   printf ("length of array %d\n", length);
 16   printf ("quick sort called in main\n");
 17   quicksort (a, 0, length - 1, length);
 18   for (i = 0; i < length; i++)
 19     printf (" %d ", a[i]);
 20 }
 21 
 22 int
 23 partition (int *num, int p, int r, int june)
 24 {
 25   int x, j, i, temp, bak, length;
 26   x = num[r];
** 27   i = p - 1;**
 28   bak = 0;
 29   printf ("inside the partition\n");
 30   printf ("length of june recieved =%d \n", june);
 31   for (j = 0; j <= r - 1; j++)
 32     {
 33       if (num[j] <= x)
 34         {
 35           i = i + 1;

 36           temp = num[i];
 37           num[i] = num[j];
 38           num[j] = temp;
 39           printf ("printing array after swap\n");
 40           for (; bak < 7; bak++)
 41             {
 42               printf (" %d ", num[bak]);
 43             }
 44         }
 45     }
[B] 46   temp=num[i+1];
 47   num[i + 1] = num[r];
 48   num[r]=temp;
[/B] 49   return i + 1;
 50 }
 51 
 52 void
 53 quicksort (int *num, int p, int r, int june)
 54 {
 55   int q, bbc, ccd;
 56   if (p < r)
 57     {
 58       call++;
 59       printf ("partition called  %d times p=%d r=%d\n", call, p, r);
 60       printf ("before sending to function length of june=%d \n", june);
 61       q = partition (num, p, r, june);
 62       bbc = q - 1 - p + 1;
 63       quicksort (num, p, q - 1, bbc);
 64       ccd = r - q - 1 + 1;
 65       quicksort (num, q + 1, r, ccd);
 66     }
 67 }

```
Just for information lines in bold are what I had missed in previous attempt.
What I want to understand is in gdb when recursive calls are made by some function then how can I make sure that when execution reaches a previous break point then it does show me all the statements step by step and not jump to next (i.e. by passing to next) this problem is only with recursive function calls.Without recursion gdb works fine.
May be I miss some thing to work with gdb.What can be that?

---

### Post by dwhitney67 on 2011-06-21
I have no idea what you are describing.

Set a breakpoint a quicksort, then run your program.

```

gdb your_program

gdb> b quicksort

gdb> run

gdb> next

gdb> <enter>

<repeat...>


```

You may also be better served using 'ddd'; this is a graphical front-end to gdb, thus perhaps giving you a better view of the debugger.

P.S.  Make sure you compile your program with the '-g' compiler option.

---

### Post by jamesbon on 2011-06-21
I want to focus my debugging only in this portion  and in this portion also want to skip call to function partition
```

void
quicksort (int *num, int p, int r, int june)
{
  int q, bbc, ccd;
  if (p < r)
    {
      call++;
**      q = partition (num, p, r, june);** //<-- I want to skip this in gdb session
      bbc = q - 1 - p + 1;
      quicksort (num, p, q - 1, bbc);

     ccd=r-q+1;
      quicksort (num, q + 1, r, ccd);
    }
}} //since it is a recursive function each time quicksort is called partition 
is also executed I want to focus my debugging only to quicksort currently
 setting breakpoint at quicksort does not let me escape from 
seeing steps of partition


```

I did what you said.
```

gdb>myprogram

gdb>break myprog:quicksort

```
Here comes a small problem quicksort calls a function partition.
What I want to debug is I do not want to go through steps of partition
i.e. jump directly to next instruction in quicksort (which had made a call to partition)

```
      bbc = q - 1 - p + 1;
```
So is there a way to skip this call to partition via gdb session from showing me.I tried ddd but felt uncomfortable hence back to gdb.

---

### Post by jamesbon on 2011-06-21
Ok finally I have been able to debug my problem the above comment where I mentioned to skip to the next instruction without seeing all the steps of a function that came in between 
```
gdb)next
``` is for that
and 
```
gdb)step
```
is to go step by step.
What I was looking for is known as step over.
In GDB, it was achieved by issuing the next command. When I was running the ```
q = partition (num, p, r, june);
``` line in gdb, typing ```
next
``` and it  executed the partition function without going into its code in detail.That is what I was looking for.
The corrected code is here and it is completely working.
```

#include<stdio.h>
#include<string.h>
int partition (int *, int, int, int);
void quicksort (int *, int, int, int);
static int call = 0;
int
main ()
{
  int i, j, choice;
  int length;
  int a[] = { 81, 12, 90, 3, 49, 108, 47 };
  i = 0;
  printf ("the sorted array is\n");
  length = sizeof (a) / sizeof (a[0]);
  printf ("length of array %d\n", length);
  printf ("quick sort called in main\n");
  quicksort (a, 0, length - 1, length);
  for (i = 0; i < length; i++)
    printf (" %d ", a[i]);
}

int
partition (int *num, int p, int r, int june)
{
  int x, j, i, temp, bak, length;
  x = num[r];
  i = p - 1;
  bak = 0;
//  printf ("inside the partition\n");
 // printf ("length of june recieved =%d \n", june);
  for (**j = p**; j <= r - 1; j++)
    {
      if (num[j] <= x)
	{
	  i = i + 1;
	  temp = num[i];
	  num[i] = num[j];
	  num[j] = temp;
//	  printf ("printing array after swap\n");
//	  for (; bak < 7; bak++)
//	    {
//	      printf (" %d ", num[bak]);
//	    }
	}
    }
  temp=num[i+1];
  num[i + 1] = num[r];
  num[r]=temp;
  return i + 1;
}

void
quicksort (int *num, int p, int r, int june)
{
  int q, bbc, ccd;
  if (p < r)
    {
      call++;
 //     printf ("partition called  %d times p=%d r=%d\n", call, p, r);
  //    printf ("before sending to function length of june=%d \n", june);
      q = partition (num, p, r, june);
      bbc = q - 1 - p + 1;
      quicksort (num, p, q - 1, bbc);
     // ccd = r - q - 1 + 1;the length here is wrong
     ccd=r-q+1;
      quicksort (num, q + 1, r, ccd);
    }
}
```
The mistake I was doing I have done bold in partition function
```
for(j=p;j<=r-1;r++)
``` was needed and what mistake I had done was
```
for(j=0;j<=r-1;r++)
```

Thanks all finally it is working.
There is a difference in ```
step
``` and ```
next
``` instructions of gdb.
 I learned this also in this program.

---

