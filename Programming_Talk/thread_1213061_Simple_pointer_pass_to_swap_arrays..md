---
title: "Simple pointer pass to swap arrays."
date: 2009-07-14
forum: Programming Talk
---

### Post by Timtro on 2009-07-14
Hi All,

Thanks in advance.

I feel slightly silly, but I can't seem to get this working. I'm writing a program in C which handles 3 large N-by-3 arrays (call them **X, **Y and **Z) of type double. There is a main loop, and at the end of each loop, I need to shift them so that B is copied to A and then C is copied to B.

For now, I have a stupid simple little function which simply moves the elements from one to the next:
```

inline void
array_copy(double **A, double **B, int N)
{
   int             i,
                   j;
   for (i = 0; i < N; i++)
      for (j = 0; j < 3; j++) {
         B[i][j] = A[i][j];
      }
}
```
And of course my main loop has the following two lines at the end:
```

array_copy(B, A, N);
array_copy(C, B, N);

```

I'd prefer to be smarter about this and simply swap off the pointers, avoiding all of these memory operations. It would also eliminate the need for the array size to be passed. I just don't know the syntax for such a thing.

I've tried this:
```

      A=B;
      tmp=B;
      B=C;
      C=tmp;

```
where tmp is just a junk pointer to facilitate the swap between B and C. It doesn't seem to work. I don't get compile errors or crashes, but the analysis of the arrays produces nonsense (derivatives are zero, functions of the elements are zero, etc).

Do I need to make a set of pointers which alias the arrays, and swap them that way? What is the best way?

Thanks again.

Best regards,



Tim.

---

### Post by dwhitney67 on 2009-07-14
The usage of pointers in C can be cumbersome; even after many years of experience in developing C and C++ code, it still takes me a while to figure out what you are asking.

Here's what I came up with:
```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

static const unsigned int ROWS = 10;
static const unsigned int COLS = 3;


void displayArray(const double** array, const unsigned int rows);
void copyArray(double** dest, const double** src, const unsigned int rows);


int main()
{
   double** A = malloc(ROWS * sizeof(double*));
   double** B = malloc(ROWS * sizeof(double*));

   for (unsigned int r = 0; r < ROWS; ++r)
   {
      A[r] = malloc(COLS * sizeof(double));
      B[r] = malloc(COLS * sizeof(double));

      // initialize with dummy values
      for (unsigned int c = 0; c < COLS; ++c)
      {
         A[r][c] = 10.0;
         B[r][c] = 20.0;
      }
   }

   printf("Initial Values:\n");
   printf("Array A:\n");
   displayArray((const double**)A, ROWS);
   printf("Array B:\n");
   displayArray((const double**)B, ROWS);

   printf("Copying array A to B...\n\n");
   copyArray((double**)B, (const double**)A, ROWS);

   printf("After copy:\n");
   printf("Array A:\n");
   displayArray((const double**)A, ROWS);
   printf("Array B:\n");
   displayArray((const double**)B, ROWS);

   for (unsigned int r = 0; r < ROWS; ++r)
   {
      free(A[r]);
      free(B[r]);
   }
   free(A);
   free(B);

   return 0;
}

void displayArray(const double** array, const unsigned int rows)
{
   for (unsigned int r = 0; r < rows; ++r)
   {
      for (unsigned int c = 0; c < COLS; ++c)
      {
         printf("%g ", array[r][c]);
      }
      printf("\n");
   }
   printf("\n");
}

void copyArray(double** dest, const double** src, const unsigned int rows)
{
   for (unsigned int r = 0; r < rows; ++r)
   {
      memcpy(dest[r], src[r], sizeof(double) * COLS);
   }
}

```

P.S.  IMO, even though you know the number of columns to be constant (3), I would still recommend that you pass this value as a parameter to the appropriate functions.

---

### Post by croto on 2009-07-14
I definitely agree with your idea of swapping the pointers. How about this?
```

#include<stdio.h>
#include<stdlib.h>

void swaparrays(void** p1, void** p2) {
  void* p3;
  p3 = *p1;
  *p1 = *p2;
  *p2 = p3;
}

int main(){
#define NROWS 2
#define NCOLS 2

  /* Blah blah, init the arrays */
  int i,j;
  float** A = (float**) malloc(NROWS * sizeof(float*));
  for(i=0;i<NROWS;i++) A[i] = (float*) malloc(NCOLS * sizeof(float));
  float** B = (float**) malloc(NROWS * sizeof(float*));
  for(i=0;i<NROWS;i++) B[i] = (float*) malloc(NCOLS * sizeof(float));
 
  A[0][0]=0;A[0][1]=1;A[1][0]=2;A[1][1]=3;
  B[0][0]=4;B[0][1]=5;B[1][0]=6;B[1][1]=7;

  /* Swap the arrays */
  swaparrays((void*)&A, (void*)&B);

  /* Print them out! */
  for(i=0;i<NROWS;i++) {
    for(j=0;j<NCOLS;j++) printf("%f ",A[i][j]);
    printf("\n");
  }
  printf("\n");

  for(i=0;i<NROWS;i++) {
    for(j=0;j<NCOLS;j++) printf("%f ",B[i][j]);
    printf("\n");
  }

  return 0;
}

```

---

### Post by Timtro on 2009-07-16
Thank you so much, both of you.

I will try this out when I get to my desk, and let you both know.

I really appreciate the time you both took to form your replies.

---

### Post by soltanis on 2009-07-16
```

  float** A = (float**) malloc(NROWS * sizeof(float*));
  for(i=0;i<NROWS;i++) A[i] = (float*) malloc(NCOLS * sizeof(float));
  float** B = (float**) malloc(NROWS * sizeof(float*));
  for(i=0;i<NROWS;i++) B[i] = (float*) malloc(NCOLS * sizeof(float));

```

OH GOD IT BURNS

---

### Post by MadCow108 on 2009-07-16
dwhitneys solution will again copy the array instead of just swapping the pointers.

actually your posted code should work (its basicly the same as crotos code which also works). Maybe it you could show us some more code. perhaps the problem is somewhere else.

---

### Post by fr4nko on 2009-07-16
The basic problem is that your implementation of bidimensional array is suboptimal for a C program and the way you swap the pointer is not correct.

In C the best way to implement 2D array is just to implement it as a 1D array and index it as needed to retrieve the elements. This is the way is explained of CS book, the ways is done in BLAS and generally speaking the C and FORTRAN implementation of matrices.

So if you have an array of dimensions rows x cols of double you can do something like that.

```
double *mat = malloc(rows * cols * sizeof(double));

/* set a given term in position (i, j) */
mat[i * cols + j] = some_value;
```Of course you can write any sort of macro to simplify the code or embed the matrix array in a class. With this implementation the swap of the pointers you was doing will work perfectly.

The problem in your implementation is that A, B and C are, each one, array of pointers. So A[i] is a (double *) and if you do A[i][j] you have actually a double. If you reflect this whole implementations wastes a lot of space just to store a pointer for each row. You have also to allocate, probably, each row separately and this is much less efficient than a single call to malloc to allocate the whole matrix.

But if you want to swap the pointer correctly you should do something like that:
```

inline void
array_copy_by_ref(double **A, double **B, int N)
{
   int i;

   for (i = 0; i < N; i++) {
      free(B[i]); /* free the memory associated with the old pointer */

      /* copy just the pointer of each row */
      B[i] = A[i];
   }
}

```but I discourage you to use this kind of approach since the 1D method is simply better. Note also that now if you modify an element of A than you will modify automatically the same element of B because each matrix references the same memory region.

I don't know exactly why the method you was using to swap pointers does not works but it is probably related to the way matrices are used in the rest of the code.

I hope that helps.

Francesco

---

### Post by MadCow108 on 2009-07-16
> **fr4nko said:**
> The basic problem is that your implementation of bidimensional array is suboptimal for a C program and the way you swap the pointer is not correct.


how come it works when I try it?

yo have the pointers A and B pointing to an array of pointers
now you set pointer A to point to the array of B and vice versa
=> A points to the data of B and B points to the data of A
= arrays swapped

where's my error?

(your solution again copies instead of swaps.)

---

### Post by lisati on 2009-07-16
> **Timtro said:**
> 

I've tried this:
```

      A=B;
      tmp=B;
      B=C;
      C=tmp;

```

Is having both A and tmp holding the same thing what you really want? This short piece of code reads to me as if the use of tmp is redundant - B gets copied to A then B gets copied to A. By the time you get to C=tmp, both A and tmp contain the same thing.

---

### Post by fr4nko on 2009-07-16
> **MadCow108 said:**
> 
yo have the pointers A and B pointing to an array of pointers
now you set pointer A to point to the array of B and vice versa
=> A points to the data of B and B points to the data of A
= arrays swapped
this is correct. If you look I'm saying:
> I don't know exactly why the method you was using to swap pointers does not works but it is probably related to the way matrices are used in the rest of the code.because I think that your idea is correct.

My point is that is better and simpler to allocate the matrix as a 1D array. Then you can swap the pointers without having the complicated 'array of pointers' structure that is difficult to maintain.

Francesco

---

### Post by dwhitney67 on 2009-07-16
> **MadCow108 said:**
> dwhitneys solution will again copy the array instead of just swapping the pointers.
...
Did the OP require swapping?  Sorry about that; perhaps the OP should learn to spell correctly.

array_copy(B, A, N).... should be array_swap(B, A, N)

---

### Post by MadCow108 on 2009-07-16
op just wrote his solution which involved copying an asked for replacement of that :)

btw It does seem the tmp pointer is not needed but the posted code still does the same as the old copy code.
```

array_copy(B, A, N);//copied A=B
array_copy(C, B, N);//copied B=C
//----
A=B;//ok
tmp=B;//seemingly useless
B=C;//ok
C=tmp;//seemingly useless

```
so we are going to need more code to see whats wrong.

---

### Post by dwhitney67 on 2009-07-16
> **MadCow108 said:**
> op just wrote his solution which involved copying an asked for replacement of that :)

btw It does seem the tmp pointer is not needed but the posted code still does the same as the old copy code.
so we are going to need more code to see whats wrong.

There are times when I am interested in the solution; other times when I am interested in sharing a solution.  But in this case... yawn.

P.S.  Don't take me seriously.  But it makes me wonder when the OP is MIA, and in the end, we end up make suppositions about what the OP intended or is doing.

---

