---
title: "how to make this C code optimized...??"
date: 2011-07-09
forum: Programming Talk
---

### Post by Praveen30 on 2011-07-09
hi friends,

i want to know how to make code optimized..what are the different areas on which i have to focus to make my code optimized..like i have this code but it is surely not optimized..

--This code is all about sorting the numbers between 0 to 1000000.
problem- if a user wants to sort only 5 or 10 0r 20 numbers then a lot of space will be wasted.
problem- i have used very normal sorting technique..please suggest me some other which has lower complexity then this....

```


#include<stdio.h>

void main()
{
 int arr[1000000];
int n,i,j,temp=0;
printf("enter the numbers in the number list");
scanf("%d",&n);
printf("enter the numbers");
for(i=0;i<n;i++)
{
   scanf("%d",&arr[i]);
}
for(i=0;i<n;i++)
{
  for(j=0;j<n-1;j++)
  {
     if(arr[j]>arr[j+1])
      {
         temp=arr[j+1];
         arr[j+1]=arr[j];
          arr[j]=temp;
       }
   
   }
}
for(i=0;i<n;i++)
{
printf("%d",arr[i]);
}
}   

```

---

### Post by dwhitney67 on 2011-07-09
Why don't you allocate the array *after* you know how many numbers the user wants to input?

Example:
```

#include <stdlib.h>
...

/* assume n is a positive integer */

...

/* allocate array */
int* arr = malloc(n * sizeof(int));

/* use arr as a regular array */

...

/* clean up */
free(arr);

...

```

---

### Post by TwoEars on 2011-07-09
Well, this is a poor sorting algorithm. Try quicksort or mergesort instead.

---

### Post by Praveen30 on 2011-07-09
> **dwhitney67 said:**
> Why don't you allocate the array *after* you know how many numbers the user wants to input?

Example:
```

#include <stdlib.h>
...

/* assume n is a positive integer */

...

/* allocate array */
int* arr = malloc(n * sizeof(int));

/* use arr as a regular array */

...

/* clean up */
free(arr);

...

```

thanks for your suggestion. once i asked on this forum how to see the execution time of a programme they suggested me this-- [http://ubuntuforums.org/showthread.php?t=1684517](http://ubuntuforums.org/showthread.php?t=1684517)

well, after applying this method, i am getting this in dynamic memory allocation-

real    0m8.912s
user    0m0.000s
sys    0m0.000s

and in the previous( static allocation )--
real    0m6.664s
user    0m0.000s
sys    0m0.000s

does this mean that after dynamic allocation it is taking much more time???

---

### Post by JupiterV2 on 2011-07-09
> **Praveen30 said:**
> thanks for your suggestion. once i asked on this forum how to see the execution time of a programme they suggested me this-- [http://ubuntuforums.org/showthread.php?t=1684517](http://ubuntuforums.org/showthread.php?t=1684517)

well, after applying this method, i am getting this in dynamic memory allocation-

real    0m8.912s
user    0m0.000s
sys    0m0.000s

and in the previous( static allocation )--
real    0m6.664s
user    0m0.000s
sys    0m0.000s

does this mean that after dynamic allocation it is taking much more time???

Yes, it does. However, it's unlikely that dynamic allocation is the problem but how you've used it. dwhitney67's suggestion of allocating a smaller array size through dynamic allocation should have dramatically decreased the time to sort the array, not the opposite.

I would also suggest this: Asking the question, "How can I improve the speed of this code," means you are likely trying to prematurely optimize your code. What you should be doing is using a profiler to see a) where your program is spending the most time; and, b) how much memory its consuming to do it. You may want to look up gprof or valgrind's massif tool to help you. Assuming that a specific piece of code is guilty for taking up too much time is a fools task. Better to know what exactly is taking up too much time.

---

### Post by Praveen30 on 2011-07-09
> **JupiterV2 said:**
> Yes, it does. However, it's unlikely that dynamic allocation is the problem but how you've used it. dwhitney67's suggestion of allocating a smaller array size through dynamic allocation should have dramatically decreased the time to sort the array, not the opposite.

I would also suggest this: Asking the question, "How can I improve the speed of this code," means you are likely trying to prematurely optimize your code. What you should be doing is using a profiler to see a) where your program is spending the most time; and, b) how much memory its consuming to do it. You may want to look up gprof or valgrind's massif tool to help you. Assuming that a specific piece of code is guilty for taking up too much time is a fools task. Better to know what exactly is taking up too much time.

thanks, i desperately want such type of tools...thanks for your suggestion...

---

### Post by Npl on 2011-07-09
you shouldnt use dynamic allocation when you can use stack variables. However you shouldnt treat stack like a big resource either.
Big or potentially big allocations should be done dynamically, even using a global var would be better than placing 4MB on the stack. Not only because you might overflow the stack, but the system will need to commit memory which takes time aswell.

But neither of this will affect the running time in any measurable manner, the biggest gain would result from using a better sorting algorithm, Quicksort (qsort is in the c library) or Heapsort for example.

---

### Post by lucasart on 2011-07-09
> **Praveen30 said:**
> hi friends,

i want to know how to make code optimized..what are the different areas on which i have to focus to make my code optimized..like i have this code but it is surely not optimized..

--This code is all about sorting the numbers between 0 to 1000000.
problem- if a user wants to sort only 5 or 10 0r 20 numbers then a lot of space will be wasted.
problem- i have used very normal sorting technique..please suggest me some other which has lower complexity then this....

```


#include<stdio.h>

void main()
{
 int arr[1000000];
int n,i,j,temp=0;
printf("enter the numbers in the number list");
scanf("%d",&n);
printf("enter the numbers");
for(i=0;i<n;i++)
{
   scanf("%d",&arr[i]);
}
for(i=0;i<n;i++)
{
  for(j=0;j<n-1;j++)
  {
     if(arr[j]>arr[j+1])
      {
         temp=arr[j+1];
         arr[j+1]=arr[j];
          arr[j]=temp;
       }
   
   }
}
for(i=0;i<n;i++)
{
printf("%d",arr[i]);
}
}   

```

Let's rewrite all this mess!

* First none of this is relevant when n is a small number. ANd if n is a large number, you're not going to ask the user to input n numbers, way too slow. So let's just ask the user for n, and fill the array with random numbers.
* Secondly, your array should be dynamically allocated. Very bad to hardcode the size, because: if n is bigger than your hardcoded number, it crashes, and if not, then you're simply wasting a lot of memory.
* Third, your sorting algorithm is wrong (or inneficient if you prefer): j should start at i+1

```

int rand32()
{
    static int seed = 0;
    return seed = seed * 6364136223846793005ULL + 1442695040888963407ULL;
}

void print_array(const int *array, int n)
{
    for (int i = 0; i < n; i++)
        printf("%d, ", array[i]);
    puts("\n");
}

int main(int argc, char **argv)
{
    int n;
    puts("please enter the value of N:\n");
    scanf("%u", &n);
    int *array = calloc(n, sizeof(int));
    
    for (int i = 0; i < n; array[i++] = rand32());
    print_array(array, n);
    
    for(int i = 0; i < n; i++)
      for(int j = i+1; j < n; j++)
        if(array[j] < array[i]) {
            int dummy = array[j];
            array[j] = array[i];
            array[i] = dummy;
        }
    
    print_array(array, n);
    free(array);
}

```* Fourth, and most important of all! This sorting algorithm is in O(N^2). Whenever N is large, you should use algorithms in O(Nlog(N)). Just google for QuickSort.
* Fifth (and last), here's how to compile your code, if you want it to run fast
```

gcc -o ./test -O3 -std=c99 main.c

```the -O3 is not there by default and makes GCC optimize the executable. in practice you'll see a huge difference (perhaps not on a trivial code like that though).

---

