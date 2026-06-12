---
title: "School assignment, arrays/matrices, help please :("
date: 2010-11-05
forum: Programming Talk
---

### Post by VanillaCone on 2010-11-05
The assignment is to write several functions to do with matrices, The current function im having trouble with is the trace of a matrix, Which Is the sum Of numbers on the main diagonal. 

so far i have 

[PHP]int trace (int **A, int n)

{

    int i;
    int j;
    int sum;

        for (i = 0; i < n; i++)
            {
                sum = 0;

                for (j = 0; j < n; j++)
                   {
                    if (i = j)
                    sum += A[i][j];
                   }

            }

    return sum;

}[/PHP]

for simplicities Sake The matrix is a 4x4 and it is 
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4.

 when i run This program It tells me the trace of my matrix ( 1 + 2 + 3 +4) Is 9, when in reality it is 10, the program does not include the first value of the first row In its calculation and im not sure why, please help =(

---

### Post by worksofcraft on 2010-11-05
> **VanillaCone said:**
> The assignment is to write several functions to do with matrices, The current function im having trouble with is the trace of a matrix, Which Is the sum Of numbers on the main diagonal. 

so far i have 

[PHP]int trace (int **A, int n)

{

    int i;
    int j;
    int sum;

        for (i = 0; i < n; i++)
            {
                sum = 0;

                for (j = 0; j < n; j++)
                   {
                    if (i = j)
                    sum += A[i][j];
                   }

            }

    return sum;

}[/PHP]

for simplicities Sake The matrix is a 4x4 and it is 
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4.

 when i run This program It tells me the trace of my matrix ( 1 + 2 + 3 +4) Is 9, when in reality it is 10, the program does not include the first value of the first row In its calculation and im not sure why, please help =(

I think you want to move the sum = 0 outside BOTH of the loops, but I also think it would be much more efficient to just use one loop:
[php]
   sum = 0;
   for (i = 0; i < n; ++i) sum += A[i][i];
[/php]

;)

p.s. and another thing to watch: the single = is an assignment so if (i = j) is actually setting i to be equal to j and then testing if it is zero. I suspect you wanted == which is the comparison operator

---

### Post by VanillaCone on 2010-11-05
moving sum = 0; outside the loop did not solve the problem =(

---

### Post by worksofcraft on 2010-11-05
> **VanillaCone said:**
> moving sum = 0; outside the loop did not solve the problem =(

No I realized you need to change that = into == and just added a p.s. as you were typing :shock:

---

### Post by VanillaCone on 2010-11-05
no doesnt work =(, It just refuses to Take that 1 Into the calculation


edit - maybe i should mention this is in C.

---

### Post by VanillaCone on 2010-11-05
I fixed it but in a really stupid way

[PHP]int trace (int **A, int n)

{

    int i;
    int j;
    int sum;

        for (i = 0; i < n; i++)
            {
                    sum = 0;
                for (j = 0; j < n; j++)
                   {
                    if (i == 0 && j == 0)
                    sum = sum + A[i][j];
                   else if (i = j)
                        sum += A[i][j];
                   }

            }

    return sum;

}[/PHP]

it now calculates properly But there HAS to be a less ugly solution to this, If anyone has one please let me know

---

### Post by worksofcraft on 2010-11-05
> **VanillaCone said:**
> I fixed it but in a really stupid way

[PHP]int trace (int **A, int n)

{

    int i;
    int j;
    int sum;

        for (i = 0; i < n; i++)
            {
                    sum = 0;
                for (j = 0; j < n; j++)
                   {
                    if (i == 0 && j == 0)
                    sum = sum + A[i][j];
                   else if (i = j)
                        sum += A[i][j];
                   }

            }

    return sum;

}[/PHP]

it now calculates properly But there HAS to be a less ugly solution to this, If anyone has one please let me know

try this one:
[php]
// gcc trace.c
#include <stdio.h>

int trace (int **A, int n) 

{ 

    int i; 
    int j; 
    int sum; 

        sum = 0; 
        for (i = 0; i < n; i++) 
            { 
 
                for (j = 0; j < n; j++) 
                   { 
                    if (i == j) 
                    sum += A[i][j]; 
                   } 

            } 

    return sum; 

} 

int main() {
	int Row[] = { 1, 2, 3, 4 }; // a row of matrix data
	int *A[] = { Row, Row, Row, Row }; // all 4 rows are the same

	return !printf("sum = %d\n", trace(A, 4));
}
[/php]

---

### Post by TiBaal89 on 2010-11-05
Were you specifically instructed to do the loops in that manner?  It's sort of silly.  You're running through all n^2 numbers when you're only interested in the diagonal.  You could do something like (just typing this off the top of my head to give an idea):

```

sum = 0;
for (i=0; i<n; i++) {
  sum += A[i][i];
}
```

---

### Post by VanillaCone on 2010-11-05
i cant make my own Main function, Im forced To work with the one provided by the assignment ^.^

---

### Post by Tony Flury on 2010-11-06
None of the solutions posted require you to re-write the main function.

The main bug in your original code is : 

```

if (i = j)

```

Should be 
```

if (i == j)

```

The fact you are using two loops in your function is a very odd design decision when one loop will work (as demonstrated by TiBaal89), but if you have to use two loops then you need to make sure you use the right comparison operators.

Interestingly in your fix where you added 
```

if (i == 0 && j == 0)
    sum = sum + A[i][j]; 

```
you used the correct operator in your added code.

Note : Confusion over the use and differences between "=" and "==" is very common, and is often the cause of bugs in C code. Many C compilers have options whereby they can warn against the use of "=" in if statements as although it is illegal it is easy to introduce bugs. The difference is : 
```

(i == j) // Comparison operator ==

```
will produce TRUE when variable i is the same value as variable j, but neither i or j are changed.

```

(i = j) // Assignment operator =

```
will cause variable i to be set to the same value as variable j, and that expression takes the value of i - so if j is 0, i becomes 0 and the expression is 0 (which of course is the same as FALSE) - which is why your code did not work initially.

---

### Post by lisati on 2010-11-06
Just a thought: what assumptions can we make about the start index of the array is passed to the function? 

edit: Friendly reminder: the CoC expects that we don't do homework for people, but providing hints when someone is stuck.

---

### Post by Arndt on 2010-11-06
Others have pointed out that you've written = when it should be ==. You can let the compiler help you with this by asking for warnings:

```
gcc -Wall -c code.c
code.c: In function ‘trace’:
code.c:16: warning: suggest parentheses around assignment used as truth value

```

Take the time to look at the manual page for gcc (or whatever compiler you're using); there may be many warnings that are useful for you (now or in the future), beyond the ones enabled by -Wall.

---

