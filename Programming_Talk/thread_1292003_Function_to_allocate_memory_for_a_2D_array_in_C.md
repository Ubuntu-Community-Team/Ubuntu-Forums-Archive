---
title: "Function to allocate memory for a 2D array in C"
date: 2009-10-15
forum: Programming Talk
---

### Post by geo909 on 2009-10-15
Hi all,

I am trying to make a function that allocates memory for a 2 dimensional integer array. Here is what I have written:

```
int**  allocate_matrix(int cols, int rows)
{
	int i;
	int ** matrix;
	
	matrix = (* int) malloc (rows*sizeof(int *));
	if(matrix == NULL){
		free(matrix); 
		printf("Memory allocation failed while allocating for matrix[].\n"); 
		exit(-1);
	}
	for(i = 0; i < rows; ++i){
		matrix[i] = (int *) malloc(cols * sizeof(int));
		if(matrix[i] == NULL){
			free(matrix[i]); 
			printf("Memory allocation failed while allocating for matrix[x][].\n"); 
			exit(-1);
		}
	}
	
	return matrix;
}


```

Could you please tell me the mistake above?
The message I get when I compile is
```

functions.c: In function &#8216;allocate_matrix&#8217;:
functions.c:24: error: expected expression before &#8216;int&#8217;
functions.c:24: error: expected &#8216;;&#8217; before &#8216;malloc&#8217;
make: *** [functions.o] Error 1

```

The 24th line is 
```
matrix = (* int) malloc (rows*sizeof(int *));
```

Thanks in advance..

---

### Post by Arndt on 2009-10-15
> **geo909 said:**
> Hi all,

I am trying to make a function that allocates memory for a 2 dimensional integer array. Here is what I have written:

```
int**  allocate_matrix(int cols, int rows)
{
	int i;
	int ** matrix;
	
	matrix = (* int) malloc (rows*sizeof(int *));
	if(matrix == NULL){
		free(matrix); 
		printf("Memory allocation failed while allocating for matrix[].\n"); 
		exit(-1);
	}
	for(i = 0; i < rows; ++i){
		matrix[i] = (int *) malloc(cols * sizeof(int));
		if(matrix[i] == NULL){
			free(matrix[i]); 
			printf("Memory allocation failed while allocating for matrix[x][].\n"); 
			exit(-1);
		}
	}
	
	return matrix;
}


```

Could you please tell me the mistake above?
The message I get when I compile is
```

functions.c: In function ‘allocate_matrix’:
functions.c:24: error: expected expression before ‘int’
functions.c:24: error: expected ‘;’ before ‘malloc’
make: *** [functions.o] Error 1

```

The 24th line is 
```
matrix = (* int) malloc (rows*sizeof(int *));
```

Thanks in advance..

You want (int *), not (* int).

Besides, you should not be freeing things when in fact nothing was allocated. "if (matrix==NULL) free(matrix)" is at best a no-op, and will probably crash instead (I haven't looked it up). But if you have succeeded in partly allocating the matrix, freeing the already allocated rows is a good idea.

---

### Post by dwhitney67 on 2009-10-15
EDIT:  Looks like Arndt beat me to the answer.

-----------------------------------------------

See snip below for changes:
```

#include <stdlib.h>

...
        matrix = (int **) malloc (rows*sizeof(int *));
...
	if(matrix == NULL){
		/* free(matrix); */   /* Not Needed! */
                ...

```

Note... you do not need to cast the return value of malloc() to suit your object's type.  Second, do you not have to free a NULL pointer when malloc() fails.

---

### Post by geo909 on 2009-10-15
Hello, thanks a lot for the reply.
I replaced (* int) with (int **):

```
int**  allocate_matrix(int cols, int rows)
{
	int i;
	int ** matrix;
	
	matrix = (** int) malloc (rows*sizeof(int *));
	if(matrix == NULL){
		printf("Memory allocation failed while allocating for matrix[].\n"); 
		exit(-1);
	}
	for(i = 0; i < rows; ++i){
		matrix[i] = (int *) malloc(cols * sizeof(int));
		if(matrix[i] == NULL){
			printf("Memory allocation failed while allocating for matrix[i][].\n"); 
			exit(-1);
		}
	}
	
	return matrix;
}
```

Now I get:

```

jorge@flamingo:~/Documents/Academic/Courses/Coding Theory$ make
gcc -c functions.c
functions.c: In function &#8216;allocate_matrix&#8217;:
functions.c:24: error: expected expression before &#8216;int&#8217;
functions.c:24: error: expected &#8216;;&#8217; before &#8216;malloc&#8217;
make: *** [functions.o] Error 1


```

This time line 24 is
```
matrix = (** int) malloc (rows*sizeof(int *));
```

Can you see the mistake here, too?
Oh well, I'm still confused with pointers I guess :(

---

### Post by fct on 2009-10-15
I'd advise this to avoid a cast warning:

matrix = (int **) malloc (rows*sizeof(int *));

Edit: note it's "(int **)" NOT "(** int)"

---

### Post by geo909 on 2009-10-15
Many thanks for the quick responses. I really appreciate it..

> note it's "(int **)" NOT "(** int)" 
Yes, it compiles now! 

Thanks again

---

### Post by Arndt on 2009-10-15
> **geo909 said:**
> Many thanks for the quick responses. I really appreciate it..


Yes, it compiles now! 

Thanks again

Type expressions like these are just like pointer expressions, except that the variable denoting the pointer isn't there. So if you want to be able to say "int x = **p;" you declare p as "int **p;" and then its type is (int **).

Chris Torek once wrote a program which could explain complex type expressions, maybe it still exists somewhere.

---

### Post by geo909 on 2009-10-15
Thanks for the info.. I'll check this out.

---

### Post by Can+~ on 2009-10-15
The simplest way to work with 2D arrays, is with a 1D array and just pretend that it's a 2D array, with macros, function, whatever.

That way you don't need an array filled with pointers.

---

### Post by nvteighen on 2009-10-15
> **Can+~ said:**
> The simplest way to work with 2D arrays, is with a 1D array and just pretend that it's a 2D array, with macros, function, whatever.

That way you don't need an array filled with pointers.

A "flat" array? Why haven't I ever thought about that?? :P With a little of linear algebra that idea seems really easy to implement!

---

### Post by Can+~ on 2009-10-15
[PHP]/*
 * by Can
 * */

//Standard Headers
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define mat(m, col, row) \
		m.data[row*m.cols + col]

#define matp(m, col, row) \
		m->data[row*m->cols + col]

typedef struct
{
	int cols, rows;
	int *data;
}matrix_t;

void matrix_init(matrix_t *matrix, int cols, int rows)
{
	matrix->cols = cols;
	matrix->rows = rows;
	matrix->data = malloc(sizeof(int)*cols*rows);
	
	if (!matrix->data)
	{
		fprintf(stderr, "Insufficient memory for a %dx%d matrix", cols, rows);
		exit(EXIT_FAILURE);
	}
	
	// 0 fill
	memset(matrix->data, 0, cols*rows);
}

void matrix_print(matrix_t *matrix)
{
	int i, n;
	
	n = matrix->cols * matrix->rows;
	
	printf("--M%dx%d--\n", matrix->rows, matrix->cols);
	for (i=0; i<n; i++)
	{
		printf("%d ", matrix->data[i]);
		
		if ((i+1)%matrix->cols == 0) printf("\n");
	}
}


int main(int argc, char **argv)
{
	matrix_t x;
	matrix_init(&x, 5, 4);
	
	// column 0, row 0
	mat(x, 0, 0) = 9;
	
	// column 0, row 1
	mat(x, 0, 1) = 2;
	
	// column 3, row 2
	mat(x, 3, 2) = 5;
	
	matrix_print(&x);
	
	
	
	return 0;
}
[/PHP]

---

